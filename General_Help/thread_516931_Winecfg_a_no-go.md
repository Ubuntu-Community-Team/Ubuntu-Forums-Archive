---
title: "Winecfg a no-go"
date: 2007-08-03
forum: General Help
---

### Post by RotoGrip on 2007-08-03
Hi all,

 Winecfg and my computer are not playing nice. I have tried using both Ubuntu, Mint, and Kubuntu. But  i get the same effect when i run Winecfg my computer locks up. I was able to get it working with Sabayon no problem. But come trying it with a buntu distro and it's not happy. I don't even know where to start looking as i don't use Wine much. Any help would be appreciated.

Thanks

---

### Post by splintercellguy on 2007-08-03
Strange indeed. Can you try doing:

rm -rf ~/.wine

and then firing up winecfg? And what version of Wine are you running?

---

### Post by buzzmandt on 2007-08-03
or can you do in terminal:
wine cmd

---

### Post by RotoGrip on 2007-08-03
Both suggestions result in locking up

---

### Post by buzzmandt on 2007-08-03
did you install follwing the directions on this page?
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by RotoGrip on 2007-08-03
> **buzzmandt said:**
> did you install follwing the directions on this page?
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)


Im sorry, I forgot to say that im running Kubuntu as of now.

---

### Post by splintercellguy on 2007-08-03
Ubuntu is Kubuntu, except different window manager :). The instructions apply to you too.

---

### Post by RotoGrip on 2007-08-03
Ok,

 Uninstalled Wine, Followed the link above and it still locks up.

---

### Post by splintercellguy on 2007-08-03
Hmmmm, Bugzilla check suggests drivers. What's the output of lspci?

---

### Post by RotoGrip on 2007-08-03
> **splintercellguy said:**
> Hmmmm, Bugzilla check suggests drivers. What's the output of lspci?


00:00.0 Host bridge: ATI Technologies Inc Radeon 9100 IGP Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP PCI/AGP Bridge
00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
00:13.2 USB Controller: ATI Technologies Inc EHCI USB Controller (rev 01)
00:14.0 SMBus: ATI Technologies Inc ATI SMBus (rev 18)
00:14.1 IDE interface: ATI Technologies Inc ATI Dual Channel Bus Master PCI IDE     Controller
00:14.3 ISA bridge: ATI Technologies Inc Unknown device 434c
00:14.4 PCI bridge: ATI Technologies Inc Unknown device 4342
01:05.0 VGA compatible controller: nVidia Corporation NV36 [GeForce FX 5700LE] (    rev a1)
02:06.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/H    T] PCI Multi-Channel Audio Controller (rev 01)
02:09.0 Ethernet controller: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit     Ethernet Adapter (rev 11

EDIT: I dont know why the smiley is in there it should say (rev eighteen)

---

### Post by splintercellguy on 2007-08-03
I'm probably going off on an irrelevant tangent, but have you tried installing restricted drivers for the video card? Anyone with more knowledge help me here :).

---

### Post by buzzmandt on 2007-08-03
worth a shot, wine does some 3d stuff so it might be locking up trying to access 3d thats not there....

good question though, did you activate the restricted video driver?

---

### Post by RotoGrip on 2007-08-03
I used envy to install the driver. But i did not get the icon to activate it like i do when using Ubuntu

---

