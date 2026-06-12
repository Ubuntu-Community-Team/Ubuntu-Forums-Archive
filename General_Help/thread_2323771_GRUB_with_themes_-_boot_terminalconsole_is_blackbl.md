---
title: "GRUB with themes - boot terminal/console is black/blank before plymouth splash shows"
date: 2016-05-08
forum: General Help
---

### Post by vishalrao on 2016-05-08
Hello,

I'm running various Ubuntu 16.04 "flavours" (KDE Neon, elementaryOS Loki, Kubuntu etc) and if I install a GRUB theme (like KDE Breeze GRUB theme, or few others) then after selecting the OS to boot (I dual boot with Win10) the GRUB graphical console/terminal box pops up but is all-black (blank) with no "Loading linux..." etc output. I have "quiet splash" set in /etc/default/grub FYI and am running a Intel Skylake Core i5-6500 CPU with on-CPU graphics (no discrete GPU card).

My question is, is there a way to prevent the console from showing before the Plymouth splash shows up, or at least, if the console must show, then how to display the echo-ed text output in it?

Cheers!

---

### Post by oldfred on 2016-05-09
Once you select a system in grub, you are past grub and into the normal boot process. And it typically takes a bit before it switches video. But if just Intel you should just have screen until drivers have loaded.

If you want to see boot process remove quiet splash. With SSD it goes by very fast though.

 sudo nano /etc/default/grub
[https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29](https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29)
GRUB_CMD_LINUX


[LIST]
[*]Entries on this  are added to the end of the 'linux' command  (GRUB legacy's "kernel" ) for both normal and recovery modes. It is used to pass options to the kernel.
[/LIST]
 GRUB_CMD_LINUX_DEFAULT="quiet splash"

[LIST]
[*]This  imports any entries to the end of the 'linux'  (GRUB legacy's "kernel" ). The entries are appended to the end of the normal mode only.
[/LIST]
     o To view a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash".

---

