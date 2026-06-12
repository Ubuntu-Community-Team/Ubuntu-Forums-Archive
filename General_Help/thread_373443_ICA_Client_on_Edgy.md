---
title: "ICA Client on Edgy"
date: 2007-03-01
forum: General Help
---

### Post by FluffyLogic on 2007-03-01
Hello All,

I'm on Linux laptop 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Linux. 

I installed the ICAClient according to the directions on the website, but I'm getting the following errors:

The windows scrolls off with Warning: 
    Name: FONTLIST_DEFAULT_TAG_STRING
    Class: XmRendition
    Conversion failed.  Cannot load font.

Warning: 
    Name: FONTLIST_DEFAULT_TAG_STRING
    Class: XmRendition
    Conversion failed.  Cannot load font.

Warning: No font found.
Warning: 
    Name: FONTLIST_DEFAULT_TAG_STRING
    Class: XmRendition
    Conversion failed.  Cannot load font.

Warning: 
    Name: FONTLIST_DEFAULT_TAG_STRING
    Class: XmRendition
    Conversion failed.  Cannot load font.

And then a segmentation fault.

I've done a couple reinstalls, and libmotif3 is set to the newest version.

Can anyone give me a hand with this?

Thanks in advance,

Fluff.

---

### Post by IcemanV9 on 2007-03-01
Someone has a success with it. Here's the [[COLOR="Orange"]solution[/COLOR]]("http://wass.homelinux.net/howtos/Citrix_ICA_How-To.shtml"). Hopes it helps you.

---

### Post by FluffyLogic on 2007-03-01
Same Error, unfortunately.

---

### Post by FluffyLogic on 2007-03-01
Success.

Not sure why, but has to do with the fonts 

xset fp rehash seemed to fix the problem. I think because the client installs fonts, and then the font cache needs to be refreshed.

---

### Post by IcemanV9 on 2007-03-01
Terrific! :)

---

### Post by FluffyLogic on 2007-03-02
Strangely enough, after I restarted ubuntu, I had to run the xset command again. Anyone know why this is?

I get further errors (during actually connecting to a server) also, but only request help for one at a time.

---

### Post by IcemanV9 on 2007-03-06
Sorry. I have no idea, but you might want to read the install.txt for ICA. It tells you how to set the environment variables (for fonts, too?). OR, maybe, you need to add it to the xorg.conf under fonts section?

---

### Post by esacre on 2007-03-06
Take a look at this : [http://support.citrix.com/forums/thread.jspa?forumID=16&threadID=86630&tstart=0](http://support.citrix.com/forums/thread.jspa?forumID=16&threadID=86630&tstart=0)

It seems there is a bug opened for ubuntu 6.10.

The solution has worked for me

---

