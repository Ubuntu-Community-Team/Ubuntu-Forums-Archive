---
title: "Strange Page Rendering In Firefox 2.0.0.3"
date: 2007-05-18
forum: General Help
---

### Post by davidbdr on 2007-05-18
I've had this problem with any version of Firefox I've run. Running in safe mode makes no difference. I only use the default theme. This doesn't occur on my Win XP hard drive but I've been using Ubuntu more and more and only resort to the evil empire when I have to. Flock also displays the same weirdness. Opera runs great but there are a couple of extensions I rely on heavily in Firefox. 

These [strange blocks of what appears to be icons]("http://www.dbaldinger.com/firefox-mess.html") show up when a page first loads. If I scroll the page up so that the strangeness moves up beneath the toolbar, when I scroll back down, the blocks usually disappear. It's only a minor annoyance but still a pain in the butt! :confused:

I am running Ubuntu Feisty Fawn but this same thing happened in every other version so it is nothing new. I've searched many time but have come up with no explanation. I have also posted this question in the Mozilla forums. I have done totally fresh installs and re-installs. Nothing changes.

---

### Post by mjitkop on 2007-05-18
What extensions do you have in Firefox? Try disabling all your extensions and try again just to rule out any extensions causing the problem.

Can you give a link to one specific page so I can check right now with my config?

---

### Post by davidbdr on 2007-05-22
Been there--done that! I've run in safe mode, I've run with all extensions disabled. It makes no difference. This happens on just about any page. It seems particularly bad on my Gmail or MyYahoo page. I have also been noticing lately that cached images start overlaping each other. Say I have an image in a blog post. An image from farther down the page will seem to lay on top of it. Very weird. Clearing the cache doesn't help. I have to shut down FF completely and restart. It has been crashing more and more also. ](*,)

---

### Post by tregeagle on 2007-07-31
Interesting, I am just  setting up an older machine for a friend and it has the same problem.

Firefox 2.0.0.5 on Feisty. When I view web pages they are normally fine but every so often a picture will load and render oddly. Blocks overlaid with sections of other pictures below it. Only seems to affect Firefox as Epiphany does not have any problems. Clearing the cache in Firefox seems to fix it temporarily.

---

### Post by tregeagle on 2007-07-31
okay, looks like in my case it was related to my Savage Video driver. 
As the machine will only be used for email + web I've changed my xorg file to use the vesa driver which has sorted it out. Although this is not really a fix, more of a workaround.

---

