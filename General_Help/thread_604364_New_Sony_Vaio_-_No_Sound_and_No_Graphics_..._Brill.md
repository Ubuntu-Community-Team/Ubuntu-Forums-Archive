---
title: "New Sony Vaio - No Sound and No Graphics ... Brilliant!"
date: 2007-11-06
forum: General Help
---

### Post by daz4126 on 2007-11-06
I've just bought a new sony vaio vgn-cr22g, the specs can be seen here:

[http://www.sonystyle.com.hk/ss/product/vaio/vgn_cr22g_w_e.jsp]("http://www.sonystyle.com.hk/ss/product/vaio/vgn_cr22g_w_e.jsp")

I have no sound working and although I can get graphics, I cannot enable any desktop effects, which should be possible since it is a new graphics card.

I think that the drivers are not available because this model of laptop is only two weeks old, so the drivers are not in gutsy. They are intel chips which I believe (mistakingly?) usually have open source drivers.

Does anybody know if there is a place where I can get more up to date drivers or if there is another solution to get sound and desktop effects working?

Thanks,

DAZ

---

### Post by dwasifar on 2007-11-06
This sounds similar to a widespread problem with Intel sound chips when Feisty first came out, mostly but not always affecting Toshiba laptops.  

You may find some help here:

[http://ubuntuforums.org/showthread.php?t=416207]("http://ubuntuforums.org/showthread.php?t=416207")

Or do a search on "snd-hda-intel" or "toshiba sound."

For the graphics, try installing xserver-xgl and then restart X.  Also check /etc/X11/xorg.conf to make sure you're using the best video driver for your hardware and not defaulting to vesa.  Run this:

```
sudo dpkg-reconfigure xserver-xorg
```

if you want to walk through the process of changing the xorg.conf.

---

### Post by daz4126 on 2007-11-06
WOW!

That worked! I now have sound! Thanks dwasifar!

Anybody got any ideas about getting the desktop effects to work?

I also have two other minor issues. If I set my bottom panel to not expand (so it is only as big as the things in it) it resets its position to the top every time I log on. And when I log on, I don´t get that ubuntu picture that shows nautilus and other things loading in.

cheers,

DAZ

---

### Post by dwasifar on 2007-11-06
> **daz4126 said:**
> 
That worked! I now have sound! Thanks dwasifar!

Anybody got any ideas about getting the desktop effects to work?

I also have two other minor issues. If I set my bottom panel to not expand (so it is only as big as the things in it) it resets its position to the top every time I log on. And when I log on, I don´t get that ubuntu picture that shows nautilus and other things loading in.


You're quite welcome.  :)  Glad to help.

I don't know what to tell you about the desktop effects - you got the sum of my knowledge about those problems with the advice about xserver-xgl and dpkg-reconfigure.  :)  But there are a lot of people with various compiz problems with Gutsy, so the best I can recommend is to crawl the forums for a while and try the various solutions, hoping one of them works.  I also don't know about the panel problem - that's just bizarre.  But I do know about the Gnome splash screen; that is just gone in Gutsy.  I don't have it on any Gutsy machine.  As far as I can tell, it's not a bug, it's a feature.

---

### Post by daz4126 on 2007-11-06
Sorry, I didn't see your reply about the video card - will give that a go.

---

### Post by daz4126 on 2007-11-06
Okay, it seems that installing xserver-xgl has done the trick. How come I had to do that?

Wobbly windows I now have, but the redrawing of them could be better - the graphics card shouldn´t be that bad.... any way of tweaking this. And what other effects are included.

Thanks for two fixes dwasifar! 

You´ve also helped me with the splash screen, which I miss....
...the wierd panel, I will have to have a play with.

thanks again!

DAZ

---

### Post by dwasifar on 2007-11-06
> **daz4126 said:**
> Okay, it seems that installing xserver-xgl has done the trick. How come I had to do that?

Wobbly windows I now have, but the redrawing of them could be better - the graphics card shouldn´t be that bad.... any way of tweaking this. And what other effects are included.

Thanks for two fixes dwasifar! 

You´ve also helped me with the splash screen, which I miss....
...the wierd panel, I will have to have a play with.

thanks again!

DAZ

I don't know why you had to install xserver-xgl, because I don't know why I had to do it either.  :)   I figured it out when none of the other compiz fixes worked for me, so I thought perhaps it would work for you too.

If you want more control over the effects, install compizconfig-settings-manager, which will show up in your menu as Advanced Desktop Effects Settings (and also add a "Custom" radio button to your Appearance choices).  The settings are numerous and not always self-evident, so for an excellent summary of what you can do, go to Forlong's blog at [http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion")

---

### Post by Ice_cone on 2007-11-28
How's compiz running, is it smooth without artifacts?
are other hardware like webcam supported?
I'm quite interested in that notebook as well
thanks

---

### Post by daz4126 on 2007-11-28
compiz is running fine - very smooth (I'm not sure what an artifact is...!)
I'm not sure how I could test the webcam - do I need software for it. It's not something I'd normally use. Does ubuntu have any inbuilt web-cam software - I'm happy to test this for you.

compiz can be seen on the screenshot attached.

I'm going to write a post tonight about seting up this laptop with Gutsy.

DAZ

---

### Post by Ice_cone on 2007-11-28
> **daz4126 said:**
> compiz is running fine - very smooth (I'm not sure what an artifact is...!)
I'm not sure how I could test the webcam - do I need software for it. It's not something I'd normally use. Does ubuntu have any inbuilt web-cam software - I'm happy to test this for you.

compiz can be seen on the screenshot attached.

I'm going to write a post tonight about seting up this laptop with Gutsy.

DAZ

Ekiga can be used to test your webcam.  Or maybe you can install skype 2.0 beta (if you skype).
Thanks you very much.
The pictures are really nice.  What software do you use for the desktop widgets?

---

### Post by daz4126 on 2007-11-28
screenlets for the widgets - some really nice ones available. It's not in the repos, but there is a deb on the screenlets site. Cairo dock is the dock - again, it's not in the repos, but there is a deb at:
[http://developer.berlios.de/projects/cairo-dock/](http://developer.berlios.de/projects/cairo-dock/)

I will try out ekiga to see if there is any web cam action!

DAZ

---

### Post by daz4126 on 2007-11-28
Judy installed a package called cheese - it looks nice and allows you to take pictures with a webcam, but it doesn't pick up the webcam. I will post about this and try to fix it as it's not something I've bothered with before.

DAZ

---

### Post by daz4126 on 2007-11-28
Looks like the motioneye webcam is a bit of a pain - see this thread here:
[http://ubuntuforums.org/showthread.php?t=289836](http://ubuntuforums.org/showthread.php?t=289836)

I've tried some of the fixes, but had no luck so far, so posted to that thread.

DAZ

---

### Post by Ice_cone on 2007-11-28
> **daz4126 said:**
> Looks like the motioneye webcam is a bit of a pain - see this thread here:
[http://ubuntuforums.org/showthread.php?t=289836](http://ubuntuforums.org/showthread.php?t=289836)

I've tried some of the fixes, but had no luck so far, so posted to that thread.

DAZ

Thanks you very much

---

