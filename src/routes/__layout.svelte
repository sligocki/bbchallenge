<script lang="ts">
	import '../styles/tailwind.css';
	import { page } from '$app/stores';

	let currentRoute = fCurrentRoute();
	function fCurrentRoute() {
		if ($page.url.toString().includes('team')) {
			return 'team';
		}
		if ($page.url.toString().includes('method')) {
			return 'method';
		}
		if ($page.url.toString().includes('story')) {
			return 'story';
		}
		if ($page.url.toString().includes('zoology')) {
			return 'zoology';
		}
		if ($page.url.toString().includes('contribute')) {
			return 'contribute';
		}
		return 'root';
	}
</script>

<div class="p-3">
	<nav
		class="lg:px-2 px-0 pb-2 flex justify-between lg:h-9 border-b-2 flex-col lg:flex-row h-14 mt-1"
	>
		<!-- top bar left -->
		<ul class="flex items-end">
			<!-- add button -->
			<h1 class="text-base lg:text-xl">
				<a href="/" rel="external">The Busy Beaver Challenge</a>
			</h1>
		</ul>

		<ul class="flex items-end space-x-2 lg:space-x-4 text-sm lg:text-base  main-menu ">
			<!-- <li>
				<a
					href="/"
					class="active"
					class:active={currentRoute == 'root'}
					on:click={() => {
						currentRoute = 'root';
					}}
					>Machines
				</a>
			</li> -->
			<li>
				<a
					href="/story"
					class:active={currentRoute == 'story'}
					on:click={() => {
						currentRoute = 'story';
					}}>Story</a
				>
			</li>
			<li>
				<a
					href="/method"
					class:active={currentRoute == 'method'}
					on:click={() => {
						currentRoute = 'method';
					}}>Method</a
				>
			</li>
			<!-- <li>
				<a href="/zoology" class="disabled" class:active={currentRoute() == 'zoology'}>Zoology</a>
			</li> -->
			<li>
				<a
					href="/contribute"
					class:active={currentRoute == 'contribute'}
					on:click={() => {
						currentRoute = 'contribute';
					}}
					>Contribute
				</a>
			</li>
			<li>
				<a
					href="/team"
					class:active={currentRoute == 'team'}
					on:click={() => {
						currentRoute = 'team';
					}}
					>Team
				</a>
			</li>
			<li><a href="https://discuss.bbchallenge.org">Forum</a></li>
			<li>
				<a href="https://github.com/bbchallenge" class="cursor-pointer "
					><img
						class="w-[23px] lg:w-[26px]"
						src="/GitHub-Mark-Light-32px.png"
						alt="Github logo"
					/></a
				>
			</li>
		</ul>
	</nav>

	<slot />
</div>

<style>
	:global(body) {
		@apply bg-gray-900 text-white font-mono;
	}

	.main-menu a {
		@apply cursor-pointer;
		color: rgba(190, 199, 238);
	}

	.main-menu a.active {
		color: rgba(250, 251, 252);
	}

	.main-menu a.disabled {
		@apply cursor-default opacity-50;
	}

	.main-menu a:hover:not(.disabled) {
		@apply text-[#dee2f7];
	}

	:global(input) {
		@apply text-black px-1 py-0.5;
	}

	:global(pre[class*='language-'] > *) {
		font-size: 1.1rem;
	}

	:global(.prose h2:first-child) {
		margin-top: 2.4rem;
		margin-bottom: 0;
	}
	:global(.prose h2:nth-child(3)) {
		margin-top: 3rem;
	}
</style>
