---
title: "firefox flash player -installed but not working"
date: 2007-12-04
forum: General Help
---

### Post by jdbausch on 2007-12-04
Here is my situation:

I backed up my home folder (including the .mozilla) folder

I wiped and reinstalled gutsy.

I replaced the .mozilla folder on my new install with my backup.

all is good in the world.  all bookmarks, settings, etc came forward.

however.  I am unable to get the flash plugin non-free to work.

i've installed via synaptic.  Firefox goes to a site with flash and gives the notification that I need to download the software.  I removed via synaptic, go to the site again (youtube) and get the same notification.  this time it installs, but does the same thing - about:plugins does not show it being installed either.

any help on how to get this rectified would be appreciated.

---

### Post by formol on 2007-12-24
the solution is here:

[https://answers.launchpad.net/ubuntu/+question/19584](https://answers.launchpad.net/ubuntu/+question/19584)

Cyrus Jones  said on 2007-12-08:

I don't believe Ralph Janke's answer is correct. This is about Adobe Flash Player, not Adobe (Acrobat) Reader.

This is not your fault. This is a very recent bug, caused by Adobe's update of Flash 9.0 update 3 (9.0.115.0) codename "Moviestar" on December 4th.

[http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html](http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html)

This caused Ubuntu to not install the flash plugin, detecting a change in the flash plugin installer file (via MD5 checksums). See bug 173890. This bug has been fixed in the next release of Ubuntu (Hardy 8.04) and it should soon come as an update to Ubuntu 7.10.

If you want an immediate fix, do the following.

Using Synaptic Package Manager, remove the package flashplugin-nonfree. For more information on how to do this, see the Ubuntu documentation here: [https://help.ubuntu.com/7.10/add-applications/C/advanced.html#synaptic](https://help.ubuntu.com/7.10/add-applications/C/advanced.html#synaptic)

Alternatively, you can run this command in the Terminal (Applications -> Accessories -> Terminal): sudo apt-get remove flashplugin-nonfree

Then just download this package (32-bit only) and install it (it is identical to the current package in the next release of Ubuntu, Hardy 8.04): [http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)

If you have 64-bit Ubuntu (not likely or recommended for a person new to Ubuntu), you currently need to build a binary package from this source package: [http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2](http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2)

---

### Post by jdbausch on 2007-12-24
thank you for the reply - I hope it will help someone.

I ended up figuring this out and fixing it myself, but for the life of me I can't recall how.

(I was really busy at the time, and should have posted my own solution, but again the busy thing...)


thank you though

---

### Post by aonegodman on 2007-12-27
Tried this once before and it worked the first time. Then seemed to just stop working in Firefox and I'm not sure if it was before or after I installed Opera 9.5.

Anyway, I uninstalled the flashplayer-nonfree and re-installed the d/l from above link.

All went well. Checked both Browsers and they list the plugin as installed. Neither work.

Now Firefox has the MediaPlayerConectivity Tool plugin and when I click on a YouTube video I get the black box with > arrow to click on. I do. Nothing happens.  ](*,)

---

### Post by aonegodman on 2007-12-28
Hope this helps somebody else.

After doing the uninstall/ reinstall thing on the flashplayer-nonfree I still was unable to get it to work in Firefox.

All I was getting was the "black box" image in video window and flash player wouldn't run.

I kept checking the MediaPlayerConnectivity Tool Plugin that I had installed and tried different options but no luck. Finally I decided to remove the useless plugin from Firefox.

Guess what?  Reloaded Firefox > YouTube > It Works!!!  \\:D/

Now I had originally installed that plugin in order to choose the media players for streaming media online and that solved that issue for me. I may not be able to view other media online now without it.  Let ya know later.

---

### Post by andykimbrey on 2007-12-29
Worked great for me, Many thanks!

---

### Post by akimatsu123 on 2007-12-29
i tried this and NOTHING would work from synaptic or the terminal. 

i ended up going to the adobe site and downloading the file, compiling, and manually installing a .deb file. that did the trick.

---

### Post by pushin50 on 2008-02-23
I tried the "official" bug fix from the first link below. That didn't work but loading the newer version, per Cyrus' suggestion. "if you want an immediate fix" below, worked like a charm.

Thanks folks!

> **formol said:**
> the solution is here:

[https://answers.launchpad.net/ubuntu/+question/19584](https://answers.launchpad.net/ubuntu/+question/19584)

Cyrus Jones  said on 2007-12-08:

I don't believe Ralph Janke's answer is correct. This is about Adobe Flash Player, not Adobe (Acrobat) Reader.


If you want an immediate fix, do the following.

Using Synaptic Package Manager, remove the package flashplugin-nonfree. For more information on how to do this, see the Ubuntu documentation here: [https://help.ubuntu.com/7.10/add-applications/C/advanced.html#synaptic](https://help.ubuntu.com/7.10/add-applications/C/advanced.html#synaptic)

Alternatively, you can run this command in the Terminal (Applications -> Accessories -> Terminal): sudo apt-get remove flashplugin-nonfree

Then just download this package (32-bit only) and install it (it is identical to the current package in the next release of Ubuntu, Hardy 8.04): [http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)

If you have 64-bit Ubuntu (not likely or recommended for a person new to Ubuntu), you currently need to build a binary package from this source package: [http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2](http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2)

---

