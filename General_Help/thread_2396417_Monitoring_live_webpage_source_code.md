---
title: "Monitoring live webpage source code"
date: 2018-07-15
forum: General Help
---

### Post by Ynothna on 2018-07-15
Hey!

I trying to figure out if it's possible to monitor a page for changes in its source code from an open page and have that exported to a file.

The specifics of what I'm trying to do, and what I've tried, is that I run a twitch stream that has a large focus on audience interaction. Part of that interaction is that they can redeem rewards that will affect the game we're playing, so I want to know as quickly as possible when these have been redeemed.

The software I'm using is StreamLabs and they have an overlay tool that lets viewers manage their rewards from an interface rather than with chat commands, but it's limited in the data I'm able to access for automated scripting. Ideally I want to be able to monitor when a reward is claimed and have a script save the info to a database so my system can handle the rest instead of me doing it manually while running the game.

So far I've found that using their alert box url, when a reward is claimed, JavaScript modifies the source code to display the info I need. Because it's JavaScript I can't just load the page and grab the code at that time, since it would only get the base HTML, I need something that has the site open already, then at an interval checks for changes and exports it.

Does anyone have any ideas on something that might be able to do this? I found urlwatcher and it supports pages using JavaScript but from what I can tell it doesn't leave the page open between checks, only works for pages that use JavaScript to build the page.

Thanks so much!

---

