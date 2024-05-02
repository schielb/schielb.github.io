# schielb.github.io
## Bryson Schiel

A personal website that allows me to post on various things in my research and personal experience.

Developed using the [Stack](https://themes.gohugo.io/themes/hugo-theme-stack/) theme from Hugo.

## Site Development Pattern

I create new branches for each new post so as to explore different ideas/drafts for my work. It also helps me see what articles I haven't worked on in a hot minute and if I need to come back to any of them.

This extra step, of creating a whole new branch, comes with plenty of risks if you don't do it right, and so today I am documenting my workflow so that I can remember what steps I need to take to avoid issues I've had in the past.

### Branch Basics for the Repo

The default branch is the `main` branch. This is where all things get published and are viewable for the public. It has the follwoing processes run whenever it gets updated:
- Build site
- Deploy site

There are two ways that I can edit this branch, both involving a pull request:
- New posts through the `posts` branch
- Site-wide development through the `dev` branch

At any given time, these three branches will ideally be all in sync. Both of these branches are also used to run the "build site" step up above. Only if the build process succeeds would I then merge the branch into `main`.

### New Posts

When I write new posts, I start by branching off of the `posts` branch and create a new `posts_<article_label>` branch. On this branch, I go through the process of writing new content and making sure that it will function just right through Hugo's command line interface.

When I commit content in these branches, **I ONLY COMMIT FILES IN THE `content/post` FOLDER**. Any time that I run `hugo server` in the command line, other files in the `public/` folder will also be changed, but I do not need to save these within the branch; they are automatically generated, and when the content reaches the `main` branch, the correct files will be built by the system. If I am using an IDE like VSCode, I can just revert all the changes for the files in the `public/` folder, since these changes don't need to be tracked through the `posts` and `main` branches.

### Site-wide Development

Any time that I want to add a new feature, like comments or links, this goes through the `dev` branch. Again, it builds any changes upon push to make sure that they won't break, checking to see if something went wrong. If all the changes look right when I `hugo server` this branch and it builds on GitHub, then I can merge these changes into `main`, being sure to then pass them into the `posts` branch for later posts to follow through as well.
