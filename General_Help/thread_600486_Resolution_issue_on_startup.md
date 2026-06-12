---
title: "Resolution issue on startup"
date: 2007-11-02
forum: General Help
---

### Post by Fireblend on 2007-11-02
Hey; I installed Gutsy since the official release and there's only one thing that's been bothering since I started using it. Everytime I log in (the login window is fine, btw), during the startup sequence my resolution is reset to 640 x 480 and then I have to set it manually to 1024x768 with the configuration tool. This happens everytime I logout/restart my computer.

Anyone know what might be causing this issue or how to solve it? It's really starting to annoy me...

Thanks in advance!

---

### Post by sammydee on 2007-11-02
I have the same problem and it's driving me mad.

Every time i start up it boots into 1024x768 and I want 1280x800.

Sam

---

### Post by Pumalite on 2007-11-02
Here is a collection of links and tips that might be of help:

[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)
[http://www.linuxforums.org/forum/ubuntu-help/105368-newb-help-everything-too-big.html](http://www.linuxforums.org/forum/ubuntu-help/105368-newb-help-everything-too-big.html)

[http://ubuntuforums.org/showpost.php?p=3484653&postcount=15](http://ubuntuforums.org/showpost.php?p=3484653&postcount=15)

 Re: Changing screen resolution?
Hi. The solution is in that page; I would just add that since you're using the i810 driver, you probably need to install the 915resolution package. Here's what Synaptic says about it:
Quote:
resolution modification tool for Intel graphic chipset

915resolution is a tool to modify the video BIOS of the 800
and 900 series Intel graphics chipsets. This includes the 845G,
855G, and 865G chipsets, as well as 915G, 915GM, and 945G chipsets.
This modification is necessary to allow the display of certain
graphics resolutions for an Xorg or XFree86 graphics server.

915resolution's modifications of the BIOS are transient.
There is no risk of permanent modification of the BIOS.
This also means that 915resolution must be run every time the
computer boots in order for its changes to take effect.
If you want to automatically set the resolution on each boot
and before X is launched, see /usr/share/doc/915resolution/README.Debian
for information about configuring the provided initscript.

The 915resolution package becomes obsolete with the newer xorg,
especially if you have the xserver-xorg-video-intel package installed.
Newer xorg brings modesetting support by default.

Homepage: [http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/)
Or, you could use the intel driver instead of the i810.

---

### Post by sammydee on 2007-11-02
YES! Found the solution!

For all of those people who have the issue of GDM being the perfect resolution and some stupid resolution being used on actual GNOME startup, here's the way to fix it:

Run from terminal:

```
gconf-editor
```

Browse the editor to /desktop/gnome/screen/default/%d where %d will probably be 0. Select this node and change the resolution to your resolution of choice, and make sure rate is something functional for your display device as well.

Exit the editor, and try logging in through GDM again.

Bingo! Lovely beautiful full resolution again. Aaaaaaaaah...

Sam

---

