---
title: "ISO CD Download"
date: 2013-05-19
forum: General Help
---

### Post by philpense on 2013-05-19
[COLOR=#000000][FONT=Calibri][LEFT][COLOR=windowtext][FONT=Calibri][COLOR=windowtext][FONT=Calibri]Visited the Lubuntu site [/FONT][/COLOR][[FONT=Calibri]http://lubuntu.net/[/FONT]]("http://lubuntu.net/")[COLOR=windowtext][FONT=Calibri] for the x86 CD ISO download and would want the download to go straight to my notebook  CD/DVD drive.  Presently using a USB Lubuntu install and need a disc for a legacy machine.[/FONT][/COLOR][/FONT][/COLOR][/LEFT]
[/FONT][/COLOR]

[COLOR=#000000][FONT=Calibri][LEFT][COLOR=windowtext][FONT=Calibri][COLOR=windowtext][FONT=Calibri]Clicking the link starts a download where I do not see a way to direct the file placement to the [COLOR=windowtext]CD/DVD drive[/COLOR] and seeking specific guidance.[/FONT][/COLOR]
[/FONT][/COLOR][/LEFT]
[/FONT][/COLOR]

---

### Post by Mark Phelps on 2013-05-19
You can't download directly to a CD/DVD drive because it is not really a filesystem; instead, you have to download to a mass storage device and then "burn" the ISO to the CD/DVD.

---

### Post by philpense on 2013-05-19
Much thanks for your timely reply.  I would then ask if there is a way to direct the download to a USB drive other than the Lubuntu install USB drive.  Have made a few attempts without success

---

### Post by Nr90 on 2013-05-19
Yes, you can either do this through your browser and select the USB drive as the download directory.

Another option is to open a terminal and cd to your USB drive and run:
wget [http://cdimage.ubuntu.com/lubuntu/releases/13.04/release/lubuntu-13.04-desktop-i386.iso](http://cdimage.ubuntu.com/lubuntu/releases/13.04/release/lubuntu-13.04-desktop-i386.iso)

---

