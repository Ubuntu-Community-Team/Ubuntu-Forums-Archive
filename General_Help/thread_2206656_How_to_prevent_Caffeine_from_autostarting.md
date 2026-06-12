---
title: "How to prevent Caffeine from autostarting?"
date: 2014-02-20
forum: General Help
---

### Post by The Trickster on 2014-02-20
Hi everyone! I've recently installed Caffeine via adding a repository, and now Caffeine is autostarting with every reboot. I have no option in Caffeine to prevent this. There is no Caffeine app in .kde/autostart nor in .config/autostart. How to solve this? I'm using Kubuntu 13.10. Thanks.

---

### Post by Dennis N on 2014-02-20
The places you are looking are in your home folder, and these autostart after you login. 
There should be a Startup Applications dialog somewhere (I don't use Kubuntu, but it's in Ubuntu) where you can disable applications from starting at boot up. (On Ubuntu, that dialog also includes the local ones.)

---

### Post by QDR06VV9 on 2014-02-20
Or you could just uninstall it, and use your power options to adjust screen blanking.
I think I set mine @ 315 minutes.
Regards
More Info [HERE]("http://forums.opensuse.org/showthread.php/478475-How-to-stop-screen-off-standby-in-KDE-desktop-even-though-all-settings-are-seemingly-correct") Post #4

---

### Post by The Trickster on 2014-02-21
I use it mostly to prevent screen saver when watching Youtube videos in fullscreen... but that's not often, so I don't need it at every startup.

> **Dennis N said:**
> There should be a Startup Applications dialog somewhere (I don't use Kubuntu, but it's in Ubuntu) where you can disable applications from starting at boot up. (On Ubuntu, that dialog also includes the local ones.)

Yes, there is a program named "Autostart" in Kubuntu, which does this, but there is no Caffeine application there at all in the list.

---

### Post by The Trickster on 2014-02-24
bump

---

### Post by Daxxi on 2015-02-18
This thread came top when I was searching for the same answer.

Here's how I solved it:
_Move_  **/etc/xdg/autostart/caffeine.desktop** to  ~/.config/autostart
(You'll need to be root for it to be deleted from /etc/__)
Change ownership of the moved "caffeine.desktop" to yourself, if necessary (it should be writable).

Now caffeine should appear in:
   System Settings -> Startup and Shutdown -> Autostart (panel) -> Desktop File
where you can disable/enable it using the Status checkbox.
( KDE disables by inserting **Hidden=true** into the desktop file )

I leave caffeine enabled because the Kubuntu 14.04 version seems to know when I'm in YouTube fullscreen.
(However, I did this anyway because, if I need to, I can easily prevent autostarting.)

---

