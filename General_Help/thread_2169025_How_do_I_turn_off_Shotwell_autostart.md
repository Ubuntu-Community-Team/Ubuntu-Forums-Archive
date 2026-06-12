---
title: "How do I turn off Shotwell autostart?"
date: 2013-08-20
forum: General Help
---

### Post by Buntu Bunny on 2013-08-20
Shotwell does not play nice with my Kodak Easyshare; or rather my Kodak Easyshare does not play nice with Linux. I finally found some workarounds to get photos transferred to my computer, but not with Shotwell (Shotwell was part of the problem). At one time I thought I found where I could choose to not let Shotwell automatically start when I mounted the camera or SD card reader. I cannot find this any more; it's not under Shotwell preferences, nor Preferred Applications. Does anyone know how I can turn off Shotwell autostart?

---

### Post by d2btoo on 2013-08-20
[http://ubuntuforums.org/showthread.php?t=1979739](http://ubuntuforums.org/showthread.php?t=1979739)
[http://lists.yorba.org/pipermail/shotwell/2010-July/000653.html](http://lists.yorba.org/pipermail/shotwell/2010-July/000653.html)

---

### Post by Buntu Bunny on 2013-08-20
d2btoo, thanks for the response. Both links gave me a start. My menus are slightly different, but I can get to "Removable Drives and Media." However,  nothing addresses Shotwell, nor any photo management tool. Curious, yes?

---

### Post by d2btoo on 2013-08-20
Yeah, that's the trouble... menus are all different across different versions and DE's.
For example, I'm at the moment in my desktop which runs old Lucid, so I can't check for now for the "new menus of current versions". Anyway if it helps, I think you need to make sure to double check the setting which controls what happens when you put removable media -- either make it ask you or completely disable it.

here is a screen shot of it (but this is old Lucid way :p )
[http://i.imm.io/1fAZg.png](http://i.imm.io/1fAZg.png)

---

### Post by Buntu Bunny on 2013-08-20
Lucid was one of my favorites. Now, I don't even have a media tab!

I've unchecked "browse removable media when inserted" under storage in removable drives and media, but that doesn't effect Shotwell's behavior.  Under camera, the only option is "import digital photographs when connected," but that's not even checked. Seems like somebody didn't realize not everyone would want Shotwell!

---

### Post by Buntu Bunny on 2013-08-20
From the Shotwell help files

> Shotwell may also be executed automatically when a camera is plugged in to your computer. To check that your system is set up to run Shotwell when a camera is detected, go to Edit &#9656; Preferences in any Nautilus (file browser) window and choose the Media tab.  You'll see a dropdown box entitled Photos: which lets you choose Shotwell as your photo handling application.

I'm running Xfce on Ubuntu but can still access Nautilus. In Ubuntu 12.04, Nautilus no longer has a media tab. The help file is outdated. 

So where has photo handling preferences been moved to????

---

### Post by Azdour on 2013-08-20
Does this thread help:

[http://ubuntuforums.org/showthread.php?t=1976683](http://ubuntuforums.org/showthread.php?t=1976683)

In xfce you find this also under Settings | Settings Manager | Removable Drives and Media

---

### Post by d2btoo on 2013-08-20
[S]Please see here [http://askubuntu.com/questions/22313/what-is-dconf-what-is-its-function-and-how-do-i-use-it](http://askubuntu.com/questions/22313/what-is-dconf-what-is-its-function-and-how-do-i-use-it) and here [http://askubuntu.com/questions/69606/how-do-i-disable-usb-auto-play](http://askubuntu.com/questions/69606/how-do-i-disable-usb-auto-play) (not the chosen answer but the answer below it)  

So basically check out if you find any interesting property regarding shotwell with the dconf and gsettings, if not then try to disable autorun altogether![/S]

oops! didn't see Azdour's post! Please disregard this post.

---

### Post by Buntu Bunny on 2013-08-20
@ Azdour, thanks. I've found Removable Drives and Media, but there are no options to address this. I've unchecked everything except to mount removable media when inserted. Everything else is disabled. 

@ d2btoo, I will check those out! I never think to look at Ask Ubuntu, unless it comes up in a search. However, this may put me on the right track.

---

### Post by Azdour on 2013-08-20
@d2btoo - you didn't need to edit out your post :)  my solution did not work so maybe yours will.  that's why sometimes posting various solutions helps the OP

---

### Post by Buntu Bunny on 2013-08-20
> **Azdour said:**
> ... that's why sometimes posting various solutions helps the OP

Agreed! And although I don't have this figured out yet, the links being provided have given me a basis to explore information that hopefully <i>will</i> lead to an answer. 

I have other things to do, but I will continue working on this and report back what I find, hopefully with the solution.

---

### Post by Buntu Bunny on 2013-08-20
> **d2btoo said:**
> Please see here [http://askubuntu.com/questions/22313/what-is-dconf-what-is-its-function-and-how-do-i-use-it](http://askubuntu.com/questions/22313/what-is-dconf-what-is-its-function-and-how-do-i-use-it) and here [http://askubuntu.com/questions/69606/how-do-i-disable-usb-auto-play](http://askubuntu.com/questions/69606/how-do-i-disable-usb-auto-play) (not the chosen answer but the answer below it)  

So basically check out if you find any interesting property regarding shotwell with the dconf and gsettings, if not then try to disable autorun altogether!

These links have been the most helpful so far. The only problem is that I can find nothing even remotely close to autorun.

```
BuntuBunny@BuntyBunny-CM1740:~$ gsettings list-schemas | grep -i shotwell
org.yorba.shotwell.preferences.window
org.yorba.shotwell.plugins.enable-state
org.yorba.shotwell.sharing.org-yorba-shotwell-publishing-piwigo
org.yorba.shotwell.video
org.yorba.shotwell.preferences.ui
org.yorba.shotwell.sharing.flickr
org.yorba.shotwell.sharing
org.yorba.shotwell.sharing.picasa
org.yorba.shotwell.preferences.editing
org.yorba.shotwell.preferences.slideshow
org.yorba.shotwell.printing
org.yorba.shotwell.crop-settings
org.yorba.shotwell.preferences
org.yorba.shotwell.plugins
org.yorba.shotwell.sharing.facebook
org.yorba.shotwell.preferences.files
org.yorba.shotwell.sharing.org-yorba-shotwell-publishing-yandex-fotki
org.yorba.shotwell.dataimports
org.yorba.shotwell
org.yorba.shotwell.sharing.youtube

```

There's an auto-import under preferences > files, but that's not the problem.
Dataimports refers to imports from fspot. 

So, I'm learning a lot, just not how to solve my problem yet. :P

---

### Post by Buntu Bunny on 2013-08-24
Still no progress on this, so I reported it as a bug at yorba.org

---

### Post by Buntu Bunny on 2013-08-27
I heard back about the bug report I filed at redmine.yorba.org. The response was that this was not a bug with Shotwell, but with Ubuntu. I was given [this link]("http://ubuntuguide.net/ubuntu-12-04-actions-cd-dvd-blu-ray") to refer to. 

The gist of it is that I could disable Shotwell auto-start only in Ubuntu (Unity). This I did, and it resolved the issue on my Xfce DE. 

This is the second program that I've had dealt with that was configured only for Unity, not the other flavors of Ubuntu. I should add that Shotwell is not on the [list of recommended apps for Xfce]("https://wiki.xfce.org/recommendedapps"). I started with Ubuntu and installed the Xfce desktop when I didn't care for Unity, and hence inherited Shotwell, so to speak.

So there you have it. At least the issue is resolved and I learned something.

---

### Post by mjc24 on 2013-10-21
Superkey (Windows Key) | System Settings | Details | Removable Media

worked for me.

---

### Post by Buntu Bunny on 2013-10-21
> **mjc24 said:**
> Superkey (Windows Key) | System Settings | Details | Removable Media

worked for me.

Mjc24, welcome to the forums. 

Yes, that would work for Ubuntu, not Xubuntu. :(

---

