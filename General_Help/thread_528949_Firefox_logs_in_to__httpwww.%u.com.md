---
title: "Firefox logs in to:  http://www.%u.com/"
date: 2007-08-18
forum: General Help
---

### Post by myke on 2007-08-18
I've recently begun using the Gnome desktop whereas I had been primarily using KDE but was having some odd problems with it like it not ejecting my audio cds.   Now after doing a clean install of Feisty with Gnome I have two new weird problems.

First no matter if I set Firefox to open to a blank page or my personal start page (which I'd prefer), it trys to open this url:  [http://www.%u.com/](http://www.%u.com/)     which it can't of course because it doesn't exist.  I have my home page set properly in preferences and have tried changing it to other simple urls such as google.com but upon initial launching, that's the only thing that it will come up with.   Is there perhaps a corrupted file some where that I can go in and edit so that it will launch to the page I set it too?  I can untar a direct download of Firefox from Mozilla.com and it works fine but then I have the problem of not getting the odd plugins I need thru the mplayer plugins for Firefox to work.

Also, my audio cds will now eject upon command but the cd player nor Audacious which I like to use for general media use will recognize any audio cd as one.  Funny thing, though, Amarok, my trusty old KDE program will recognize any audio cd and play it just fine.  

I know how to normally set file associations thru the properties tabs but I can't get an audio cd to launch on clicking the icon with anything.   The only way I can even get one to play is by opening it with Amarok.  Any suggestions on how to fix this?

---

### Post by aidanr on 2007-08-18
check the shortcut you use to launch firefox, it'll be firefox %u, so just remove the %u

---

### Post by myke on 2007-08-18
why thank you!  That worked just fine.  I was using a launcher from a gdesklet launcher bar but even the launcher from the main ubuntu menu had the same problem.   Using your simple solution worked fine.  Thanks again.

Now ... if I can just get my audio cds to launch when clicking the desktop icon to a program of my choice or even to be recognized by a program of my choice ... I'll have no problems at all.  I had no trouble getting read/write capability with my NTFS winxp partition and Gnome recognizes my portable hard drive and external dvd writer just fine.  

The only unrecognizable media I still have problems with is plain old audio cds.   New ones, old ones ... doesn't matter.   Only Amarok will recognize and open them at all.  Nothing else will open them.  Oh .. K3B ... another KDE app oddly .. will recognize them for ripping so I guess that's something.

I was just hoping to use  a small simple media player like audacious to pop open an audio cd but not such luck.  At least they eject now!

Thanks again for your help with the firefox problem!

---

### Post by euler_fan on 2007-08-18
I know it's overkill, but VLC is a great player for anything you might want. Their website has install instructions.

---

