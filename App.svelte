<script>
	import compass from "./assets/compass-3-line.svg"
	import navigation from "./assets/navigation-line.svg"
	import cloud from "./assets/cloud-line.svg"
	import map from "./assets/map.jpeg"
	import cur from "./assets/cur.jpeg"
	import crt from "./assets/crt.jpeg"
	let state = "explore"
	let open_page = false
</script>

<main>
	<header>
		<a href="#">
			<h2 class="logo">tinp</h2>
		</a>
		<nav>
			<button
				class:is-active={state == "explore"}
				on:click={() => (state = "explore")}
			>
				<img src={compass} />
			</button>
			<button class:is-active={state == "nav"} on:click={() => (state = "nav")}>
				<img src={navigation} />
			</button>
			<button
				class:is-active={state == "weather"}
				on:click={() => (state = "weather")}
			>
				<img src={cloud} />
			</button>
		</nav>
	</header>
	{#if state == "explore"}
		<img src={map} class="map" />
		<div class="explore-search">
			<i class="ri-search-line" />
			<input type="search" placeholder="Search..." />
			<button>
				<i class="ri-filter-2-fill" /> Only show selected
			</button>
		</div>
		<div class="explore-trails">
			<div class="explore-trail" on:click={() => (open_page = true)}>
				<h2>River Trail</h2>
				<p>Good beginner trail with a gorgeous view of the river</p>
				<p>
					<span style="color: rgb(113, 163, 40);"
						><i class="ri-dashboard-2-line" /> Easy</span
					>
					<span><i class="ri-walk-line" /> 5km</span>
					<span><i class="ri-time-line" /> 3hrs</span>
				</p>
			</div>
			<div class="explore-trail">
				<h2>Tonto Trail</h2>
			</div>
			<div class="explore-trail">
				<h2>Skeleton Trail</h2>
			</div>
		</div>
		<div class="page" class:show={open_page}>
			<h2>River Trail</h2>
			<button style="float: right">Add to comparison</button>
			<p>
				<span style="color: rgb(113, 163, 40);"
					><i class="ri-dashboard-2-line" /> Easy</span
				>
				<span><i class="ri-walk-line" /> 5km</span>
				<span><i class="ri-time-line" /> 3hrs</span>
				<span><i class="ri-drop-line" /> 500ml</span>
			</p>
			<img src={crt} />
			<p>
				Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod
				tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim
				veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea
				commodo consequat. Duis aute irure dolor in reprehenderit in voluptate
				velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint
				occaecat cupidatat non proident, sunt in culpa qui officia deserunt
				mollit anim id est laborum.
			</p>
			<h3>Features</h3>
			<div class="features">
				<div class="feature" style="background-image: url({crt});">
					<h3 class="feature-text">Silver Bridge</h3>
				</div>
				<div class="feature" style="background-image: url({crt});">
					<h3 class="feature-text">Silver Bridge</h3>
				</div>
			</div>
		</div>
	{:else if state == "nav"}
		<img src={cur} class="map" />
		<div class="filters" />
		<div class="alert">
			<i class="ri-alert-line"></i>
			Landslide warning near Schiit's Creek
		</div>
	{/if}
</main>

<style>
	@import url("https://cdn.jsdelivr.net/npm/remixicon@2.5.0/fonts/remixicon.css");
	@import url("https://fonts.googleapis.com/css2?family=Inter:wght@400;700;900&display=swap");

	:root {
		font-family: Inter, -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto,
			Oxygen, Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
		background-color: grey;
	}

	main {
		position: relative;
		display: flex;
		flex-direction: column;
		margin: auto;
		width: 450px;
		height: 900px;
		background-color: white;
	}

	header {
		position: absolute;
		left: 0;
		right: 0;
		display: flex;
		flex-direction: row;
		align-items: center;
		padding: 1em 1em 0 1em;
	}

	header a {
		color: inherit;
		text-decoration: unset;
	}

	header nav {
		display: flex;
		margin-left: auto;
		border-radius: 5px;
		background-color: white;
		box-shadow: 0px 2px 5px 1px rgba(0, 0, 0, 0.2);
		padding: 0.25em;
	}

	header nav button {
		display: flex;
		padding: 0.25rem;
		border: none;
		flex-direction: row;
		background: none;
		box-sizing: border-box;
		border-radius: 5px;
	}

	header nav button + button {
		margin-left: 0.125em;
	}

	header nav button.is-active {
		box-shadow: inset 0px 0px 3px rgba(0, 0, 0, 0.2);
		background-color: #f3f3f3;
	}

	header nav button:hover {
		box-shadow: inset 0px 0px 3px rgba(0, 0, 0, 0.2);
	}

	header .logo {
		margin: 0;
		font-weight: 900;
	}

	img {
		object-fit: cover;
	}

	.map {
		flex: 1;
	}

	.explore-search {
		position: absolute;
		display: flex;
		left: 2rem;
		bottom: 10.5rem;
		background-color: white;
		padding: 0.25rem;
		align-items: center;
		box-shadow: 0px 2px 5px 1px rgba(0, 0, 0, 0.2);
		border-radius: 5px;
		z-index: 10;
		font-size: 1.125rem;
	}

	.explore-search input {
		font-size: inherit;
		margin: 0;
		margin-left: 0.25rem;
		border: 0;
	}

	.explore-trails {
		position: absolute;
		left: 0;
		right: 0;
		bottom: 0;

		display: flex;
		overflow-x: scroll;
		padding: 2em 1em;
	}

	.explore-trail:hover {
		box-shadow: 0px 3px 6px 2px rgba(0, 0, 0, 0.3);
	}

	.explore-trail {
		flex-shrink: 0;
		background-color: white;
		width: 250px;
		height: 125px;
		border-radius: 5px;
		padding: 0.75em;
		box-sizing: border-box;
		box-shadow: 0px 2px 5px 1px rgba(0, 0, 0, 0.2);
		transition: 0.1s ease box-shadow;
		margin-left: 1em;
	}

	.explore-trail h2 {
		font-weight: 900;
		margin: 0;
	}

	.explore-trail p {
		margin: 0.25em 0;
	}

	span {
		margin-right: 0.3em;
	}

	span i {
		display: inline-block;
		transform: translateY(0.125em);
	}

	.page {
		position: absolute;
		top: 5em;
		left: 0;
		right: 0;
		bottom: 0;
		padding: 1em;
		background-color: white;
		border-radius: 8px 8px 0 0;
		transform: translateY(100%);
		transition: transform ease 0.1s, opacity ease 0.1s;
		box-shadow: 0px 2px 6px 2px rgba(0, 0, 0, 0.3);
		opacity: 0;
		z-index: 100;
	}

	.page h2 {
		margin-top: 0.25em;
		font-weight: 900;
	}

	.page h3 {
		margin-top: 0.25em;
		font-weight: 900;
	}

	.page img {
		width: 100%;
		border-radius: 10px;
	}

	.features {
		display: flex;
		overflow-x: scroll;
	}

	.feature {
		flex-shrink: 0;
		position: relative;
		height: 160px;
		width: 350px;
		border-radius: 10px;
		background-size: cover;
		box-shadow: inset 5px 5px 30px 10px rgba(0, 0, 0, 0.2);
		margin-right: 1em;
	}

	.feature-text {
		color: white;
		position: absolute;
		top: 0.75rem;
		left: 0.75rem;
	}

	.page.show {
		opacity: 1;
		transform: translateY(0);
	}

	.alert {
		position: absolute;
		bottom: 1em;
		right: 1em;
		padding: 1em;
		background: white;
		color: white;
		background: rgba(219, 143, 25, 1);
		border-radius: 5px;
	}
</style>
