---
title: "Couldn't open dvd device /dev/dvd (no such file or directory)"
date: 2013-12-29
forum: General Help
---

### Post by boeingx37 on 2013-12-29
Hello. I installed lubuntu 13.10 and I have Gnome Mplayer.
When I open folder with DVD files or put a disk into my laptop I see this message
"Couldn't open dvd device /dev/dvd (no such file or directory)"
I don't have this folder in the system.
Haw can I create this folder with necessary files?

Also, I tried VLC Media player. In a word, it can play some DVD disks but some not.
For example, an English video course which has complex structure, it can't end a part up and move on to a next one.
So many parts of the video are missed partly.
I checked this disk on Windows in order to be sure that it was not the fault of DVD files(folder on USB stick). It perfectly works on windows.
So I wanna check it out with Gnome Mplayer but I have this unpleasant error.
Please, help me to solve this problem:)

Regards,

---

### Post by damage3025 on 2013-12-29
Chances are the device file for your DVD driver is /dev/sr0

You may try the following steps to let [COLOR=#000000][FONT=arial]GNOME MPlayer use [/FONT][/COLOR]/dev/sr0
Edit => Preferences => MPlayer => MPlayer Default Optical Device => (Select the black entry) => (Input /dev/sr0) => Close

---

### Post by boeingx37 on 2013-12-30
Unfortunately, I have no both /dev/dvd and /dev/sr0. Can I do something else?[HR][/HR]

---

### Post by damage3025 on 2013-12-31
From your screenshot, I do see /dev/cdrom as a symbolic link.

You can use /dev/cdrom, the name doesn't matter (Unless you have multiple optical drivers on your computer)

If you want to use the real device, you use ls -l /dev/cdrom to find out which file it links to.
( You GUI file manager should have the ability also, just that I'm cannot be 100% sure. You are running LXDE/Lubuntu? )

---

