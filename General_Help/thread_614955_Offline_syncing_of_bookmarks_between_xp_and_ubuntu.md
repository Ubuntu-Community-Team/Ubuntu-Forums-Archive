---
title: "Offline syncing of bookmarks between xp and ubuntu"
date: 2007-11-16
forum: General Help
---

### Post by Schecters on 2007-11-16
Hello all, this is my first post on the ubuntu forums.  I am very pleased with Ubuntu, and love using it.  

I dual boot (well honestly I triple boot but for this post's sake I dual) xp and gusty.  As of now, I am sharing a firefox profile between the two, which is a neat idea.  But I don't like going that route because  1)certain addons have become corrupt 2)I would prefer to keep the settings and what not separate.

I honestly just want to share bookmarks.  History and password saves would be nice too, but really all I need is bookmarks.  I have seen foxmarks, which sounds great.  But, to be honest, I don't like the idea of all the daily sites I visit to which  I provide my personal info to being online.  Is there anyway to **not** share a profile between xp and gusty, but share bookmarks, without the online-sync route?

Thanks in advance for any replies!

---

### Post by briwood on 2007-11-16
Hey Scheters,

I wrestled with the same problem.  What I ended up with was [http://www.google.com/tools/firefox/browsersync/](http://www.google.com/tools/firefox/browsersync/)  I use that to keep my bookmarks sync'd between xp/ubuntu (dual booting at home) and my workstation at work.

Keep in mind that Google, for all of their great apps and convenience is spying on you. 

I tried foxmarks and a bunch of other services.  Google browser sync was far and away the best.

---

### Post by Schecters on 2007-11-16
> Keep in mind that Google, for all of their great apps and convenience is spying on youThat is exactly why I just want to do it myself.  I'm not wanting to share bookmarks with other computers, just my one.  Is there anyway to maybe make a custom profile for each os and then somehow have just the bookmark location shared or something?

---

### Post by Irihapeti on 2007-11-16
I shared bookmarks between Vista and Ubuntu for a couple of months. I did it like this.

I had the bookmarks file on a shared partition which both OSs could write to.

I created a user.js file for each installation, which gave the path to the bookmarks file. It goes in the Firefox profile folder.

There are more details here:

[http://kb.mozillazine.org/User.js_file](http://kb.mozillazine.org/User.js_file)

Another way is to set up some sort of script, so that when you open/close Firefox it syncs the file between systems. Rsync can be used for this.

BTW, it pays to do a backup of your bookmarks file while you are experimenting with this sort of thing - I was glad I did on more than one occasion.

HTH
Irihapeti

---

### Post by Schecters on 2007-11-18
Thanks Irihapeti, I created a user.js.  It does exactly what I wanted, thanks!

---

### Post by Irihapeti on 2007-11-18
Glad to be able to help.

---

