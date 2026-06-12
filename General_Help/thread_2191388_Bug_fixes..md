---
title: "Bug fixes."
date: 2013-12-02
forum: General Help
---

### Post by Andrew_Lucas on 2013-12-02
Hi all,

There are a couple of issues I've got, and have yet to find a conclusive 'fix' that consistently works. My install is 12.04.

**_NEW THREAD STARTED, SEE [HERE]("http://ubuntuforums.org/showthread.php?t=2193936")_** [s]Bug #1: [https://bugs.launchpad.net/ubuntu/+source/accountsservice/+bug/996791](https://bugs.launchpad.net/ubuntu/+source/accountsservice/+bug/996791) . As detailed here, very slow loading of the desktop. Someone on that thread mentioned removed i386 libs, but I definitely need *some* 32 bit libraries (despite having an x64 machine), for e.g. Skype. This bug is particularly annoying, and affecting both my personal machine, and installs I've done for family.[/s]

**_SOLVED_****_ - SEE POST #5_** [s]Bug #2: Thunar slow to open. Having no tabs in Thunar was driving me mad, so I added the xubuntu-dev/xfce-4.10 ppa (as detailed [here]("http://www.webupd8.org/2012/11/install-thunar-with-tabs-support-in.html")). Touch wood, Thunar has been behaving thus far, but if someone could guide me through a check I could do to confirm it won't reappear in the future, I'd appreciate it.[/s]

_**SOLVED**_**_ - SEE POST #2_** [s]Bug #3: My panel has been destroyed (by the update perhaps?) :(. Screenshot attached. Things e.g. like the terminal shortcut from the dock also had to be reset to point at the Xfce terminal emulator.[/s]

Thanks for any help!

AA.

---

### Post by Dennis N on 2013-12-02
On the panel, you need to add a separator between the window list and the notification area. The separator must be set to expanded (check box): select the separator in the panel preferences dialog > items tab, then click on the edit button on the right. 

Setting the terminal application need only be done once.

---

### Post by vasa1 on 2013-12-02
Re. #3,
>  NOTE: If you have upgraded to Xfce 4.10 and all your panel plugins have shifted to the left (or top) of the panel, please use an expandable separator as described above. In Xfce 4.8 the window buttons plugin was expandable as well, but it is no longer the case in Xfce 4.10.
From [http://docs.xfce.org/xfce/xfce4-panel/preferences](http://docs.xfce.org/xfce/xfce4-panel/preferences)

---

### Post by Andrew_Lucas on 2013-12-02
Thanks! I knew it was something to do with seperators but just couldn't find the right setting.

1 down, 2 to go. Unfortunately these two are much more important.

---

### Post by ajgreeny on 2013-12-02
For your thunar slow opening try this:-
Edit /usr/share/gvfs/mounts/network.mount and change it from:
```
[Mount]
Type=network
Exec=/usr/lib/gvfs/gvfsd-network
AutoMount=true
```
to
```

[Mount]
Type=network
Exec=/usr/lib/gvfs/gvfsd-network
AutoMount=false
```

it will make opening up thunar very quick again even for the first time.  If you want the smb browsing you just click on the network:/// link in thunar and it will then do the browsing search which takes a bit of time.

This worked in a previous version of thunar but I'm not sure if it's needed any more.

---

### Post by Andrew_Lucas on 2013-12-06
> **ajgreeny said:**
> For your thunar slow opening try this:- Edit /usr/share/gvfs/mounts/network.mount and change it from: ```
[Mount] Type=network Exec=/usr/lib/gvfs/gvfsd-network AutoMount=true
``` to ```
 [Mount] Type=network Exec=/usr/lib/gvfs/gvfsd-network AutoMount=false
```  it will make opening up thunar very quick again even for the first time.  If you want the smb browsing you just click on the network:/// link in thunar and it will then do the browsing search which takes a bit of time.  This worked in a previous version of thunar but I'm not sure if it's needed any more.  Going to reboot, and give this a shot. At the moment, the slow opening bug only tends to affect the first time you launch Thunar, after that, it works like a treat!

---

### Post by Andrew_Lucas on 2013-12-06
Just to confirm - Thunar fix seems to be working!

If someone could recommend a fix for the desktop, or at least something pointing me in the right direction, that'd be great...

---

### Post by Andrew_Lucas on 2013-12-09
Bump.

---

### Post by Andrew_Lucas on 2013-12-15
BUMPing.

---

### Post by vasa1 on 2013-12-15
I suggest you stop bumping this one. Make a new thread with an informative title.

---

### Post by Andrew_Lucas on 2013-12-15
Sure, will do.

---

