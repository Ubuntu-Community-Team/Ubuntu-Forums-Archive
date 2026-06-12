---
title: "Epiphany and &quot;Open with other application&quot;"
date: 2005-04-06
forum: General Help
---

### Post by Funkpreacher on 2005-04-06
Hello,

I really like to use Epiphany for web browsing, and I more or less have only one problem with it, which seems trivial, but I could not find an answer to it anywhere.
The version I am using is 1.6.1 within Gnome 2.10.

I cannot find where to tell Epiphany which external application to use for opening files. The most frequent example for that is when trying to open Real Media files, I would like to use the Real Player for it, but Epiphany picks Totem.

In Firefox the open file dialog offers you the possiblity to open file with a different application, Epiphany does not have this. According to the Epiphany webpage I can set it in "Advanced Desktop Preferences" which also does not exist, at least not in Gnome 2.10.

I would be thankful for any input. It must be an easy thing to solve, I am sure.

---

### Post by jobezone on 2005-04-08
yeah, I'm also using epiphany and have that problem. I think it uses what Nautilus does by default, when opening applications. Probably there is some way to configure this, but where?....

---

### Post by mirwin77 on 2007-11-11
I'm trying to figure this out as well, using Epiphany 2.20.1.  Anyone know how to set helper applications for the Epiphany web browser?

---

### Post by jslmg on 2008-01-07
> **mirwin77 said:**
> I'm trying to figure this out as well, using Epiphany 2.20.1.  Anyone know how to set helper applications for the Epiphany web browser?

mirwin, did you figure this out? Here's how to do it, if you haven't. It's quite easy once you know, and it's all in the gnome interface:

In the main menu, go to Applications-->System Tools-->Configuration Editor. (If you don't see System Tools, you'll need to add it using System-->Preferences--> "Main Menu" editor). 

In Configuration Editor, go to Desktop/Gnome/URL-Handlers. There you will see a list of most net protocols. Down the list, you'll see "rtp" and "rtsp". These are the RealPlayer 'cols. Select them.


Where it says "totem," change it to "realplay". Leave the "%s" as is. You can change other handlers in the same way.

If the changes don't seem to take immediately, restart the computer.

---

### Post by linuxisfree on 2008-05-26
Hi, i actually have a slightly different problem... i'm using epiphany browser and i'm downloading torrents... how do i make it so that whenever i click the link, it automatically uses deluge to access the torrent file?

Thanks very much!

EDIT: Nevermind... i can just open it manually (without downloading the torrent). Thanks, though!:D

---

