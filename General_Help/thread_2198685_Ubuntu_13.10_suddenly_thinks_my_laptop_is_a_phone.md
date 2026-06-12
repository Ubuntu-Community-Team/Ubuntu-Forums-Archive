---
title: "Ubuntu 13.10 suddenly thinks my laptop is a phone"
date: 2014-01-10
forum: General Help
---

### Post by mcdragon on 2014-01-10
I really don't know what happened but when I tried looking up System Settings yesterday I found it was gone from the dock. When I searched for it I found a generic icon called system settings and this showed up
[http://picpaste.com/Screenshot_from_2014-01-10_07_20_05-3XsErEKf.png](http://picpaste.com/Screenshot_from_2014-01-10_07_20_05-3XsErEKf.png)
Also some other things stopped working like the About this Computer and the System Settings menu in the main wrench system menu on the top right.

I use Ubuntu 13.10 64-bit on a brand new Lenovo Thinkpad T440s

Please help. Otherwise I need to re-install the lot. Again not sure what triggered it but I did some updates 
I couldn't find anything similar problem reported from other users. I think the main issue is Ubuntu now integrating the one interface for all into the Ubuntu installation.

---

### Post by jones quest on 2014-01-10
I don't think this should happen if your running a standard ubuntu installation.
Have you been experimenting with ubuntu touch (for instance by adding ubuntu touch/phone related PPAs or enabling unsupported updates)?

The code base for the phone/tablet version is being merged into main ubuntu archive, which means you can install some of the touch applications on you desktop. The system settings app your picture is showing is called "system-settings" is part of the "ubuntu-system-settings" package meant for ubuntu touch.

The regular desktop system settings app is called "gnome-control-center". Try launching that through the terminal to see if it's still there.

You should be able to install most of these touch apps without removing any of the desktop apps. They should not conflict. The reason you can't find the regular system settings or About this Computer indicates that you may have accidentally enabled some kind of experimental/testing version of ubuntu. Check your repositories in "/etc/apt/sources.list" & "/etc/apt/sources.list.d/" and deselect any non-standard repos. You can also use the "Software & updates" (="software-properties-gtk") application to do this graphically.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by grahammechanical on 2014-01-10
I have a Trusty Tahr install with Unity 8 Shell, Ubuntu Touch core apps and other experimental stuff. That image is indeed the Ubuntu phone system settings. In fact, you should still be able to find the original System Settings where it usually is. We can unlock icons from the dock. Perhaps that has happened. Have you tried?

1) Power/cog>System Settings
2) right click desktop background and select Change Desktop Background.
3) Dash search System Settings
4) Dash>Applications and look for the System Settings icon.

When we install Ubuntu Touch core apps will may also get two Netwrok Manager icons in the top panel, the usual one and one for the phone. As far as I know the only Ubuntu phone app that has been added to 13.10 and Trusty Tahr without the user installing it is Web Browser, the web browser for the Ubuntu phones. Expect more of this kind of phone/desktop convergence when ubuntu 14.10 is released.

Regards.

---

### Post by mcdragon on 2014-01-11
The only thing I have added to the /etc/apt/sources.list was the following two lines: 

```
deb http://download.virtualbox.org/virtualbox/debian saucy contrib
deb http://repository.spotify.com stable non-free
```

In the Ubuntu Software tab I have ticked all: Canonical-supported FOSS, Comunity-maintained, Proprietary... and Software restricted by copyright...

Under Other software I have: Canonical Partners and Canonical Partners (source code), Independent, Independent (source code), A virtualbox repo, a Spotify repo and  a Dropbox repo

Under Updates I have ticked: Important security updates (saucy-security), Recommended updates..., and Unsupported updates (saucy-backports). The Pre-released updates is unticked!
No additional drivers have been installed.

Other points:
[LIST]
[*]the app gnome-control-center is now MISSING
[*]the software updater app is MISSING
[*]right-click on the Desktop is NOT showing the Change bacground option
[*]clicking the power/cog on the system tray and then About this computer does NOTHING
[*]the /etc/apt/sources.list.d/ map only has 2 files: dropbox.list  dropbox.list.save
[/LIST]

I am giving up as cannot understand if and what I did anything wrong. I am re-installing but this time with 12.04.3 and hope this one is more stable

---

### Post by mcdragon on 2014-01-17
Installed the last LTS 12.04.3 but my WLAN card was not recognised so had to go back to 13.10. So far so good as Ubuntu still considers my laptop a Desktop and not a phone. I am being extra vigilant of any updates.

---

