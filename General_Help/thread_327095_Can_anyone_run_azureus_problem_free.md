---
title: "Can anyone run azureus problem free?"
date: 2006-12-28
forum: General Help
---

### Post by TomalakBORG on 2006-12-28
Hey guys, here;s my story. 

I was running a headless (vnc) gentoo server, when I found azureus was killing my system. It would hard-lock the machine after an hour or so of downloading. I'd tried many things, until I finally gave up the ghost and took it as a sign to try me some kubuntu. 

I like kubuntu pretty well, even though I miss portage - I'll live; adept is a fine package manager and apt-get is solid once the repositories are set. Not having to compile every last thing is nice too. 

Azureus worked when I installed it after first setting up the system with the default packages. I did not test to see if it would give up after an hour of downloading, but it ran and I changed some of my settings to my liking before closing it. Then I installed limewire, and it threw a fit about java being 1.4 and I needed 1.5. Fine. I used automatix2 to install sun-jdk-1.5-ubuntu3 - now azureus refuses to run because the "hotspot vm encounters a problematic frame" 

So I used adept to purge my java environments, and reinstall all the 1.5's it listed. No dice. Then I decided "it ran before, let's try the old 1.4s" - this time it loads, but as soon as the window comes up, it dies with "java hotspot vm encountered an "internal error (and a bunch of numbers)"

Great. Really great - I switch distros, take my server down for a week to screw around with getting it back to *where it was before for many many months*

Are any of you able to run azureus nicely, and if so, what packages/configs did the trick?
Thanks in advance - I'm pulling my hair out over here!
Bill

---

