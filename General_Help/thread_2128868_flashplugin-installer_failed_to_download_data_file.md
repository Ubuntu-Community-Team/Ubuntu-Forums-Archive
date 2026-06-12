---
title: "flashplugin-installer failed to download data files"
date: 2013-03-24
forum: General Help
---

### Post by coljohnhannibalsmith on 2013-03-24
Hello,

[COLOR=#ff0000]*flashplugin-installer failed to download data files.*[/COLOR]

This message keeps popping up on my screen and I've already removed and reinstalled it as the message suggests.

It also took forever to reinstall with a good internet connection.

Please see the attachment for a screenshot.

Thanks, Hannibal

---

### Post by Impavidus on 2013-03-24
The flashplugin-installer doesn't contain the flash plugin. Instead, during installation it downloads the flash plugin from a different server than where you got the installer package. Maybe that server had a problem.

Although in the past I have had the problem that the flashplugin-installer pointed to the wrong URL, so I couldn't update flash for a few weeks. I had to install flash manually or disable it. I didn't want to go on the internet with an outdated flash plugin.

---

### Post by faust99 on 2013-04-22
> **coljohnhannibalsmith said:**
> Hello,

[COLOR=#ff0000]*flashplugin-installer failed to download data files.*[/COLOR]

This message keeps popping up on my screen and I've already removed and reinstalled it as the message suggests.

It also took forever to reinstall with a good internet connection.

Please see the attachment for a screenshot.

Thanks, Hannibal

I kept having this issue too and just installed flash manually. It's easy. 
1. Download tar.gz from here: [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
2. Unpack it anywhere. Two files are there: (a) /usr and (b) libflashplayer.so
3. Open nautilus as root (gksudo nautilus) and use it to:
4. Move libflashplayer.so to /usr/lib/mozilla/plugins
5. Move the downloaded flash directory (/usr) to /usr.

---

### Post by coljohnhannibalsmith on 2013-04-22
Thank you,

I installed the Flash-Plugin manually and it's working fine.

BTW, how do I mark this thread as solved?  I can't find the control for this.

Hannibal

---

### Post by BlinkinCat on 2013-04-22
Hi,

Here is the present method of marking threads as solved -

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Cheers - :)

---

