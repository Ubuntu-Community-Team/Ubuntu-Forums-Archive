---
title: "Ubuntu Gnome 17.04 graphics issues"
date: 2017-07-10
forum: General Help
---

### Post by richie60 on 2017-07-10
I'm having an issue with the latest os when booting up.  This happens quite frequently, not all of the time but enough to be a problem.  

I have recently built a new htpc based upon an Intel core i3, Asus H110 plus mitx board, 8gb ram and it's connected to my tv via HDMI.

When booting up, I only get a blank grey screen and nothing else.  I can fix  this sometimes by turning the tv off and back on again if I'm lucky, but normally I have to reboot the pc.

I've tested the live Kubuntu 7.04 and Mint 18.2 KDE and it seems to be ok with this which leads me to think it's a problem with Gnome.  I heard it's using Wayland and that could be the issue I'm having.

Has anyone else had problems?

[IMG]http://i1083.photobucket.com/albums/j387/hifiman60/Forum%20pics/20170710_175956_zpse0nqkxsv.jpg[/IMG][/URL]

---

### Post by dragonfly41 on 2017-07-10
I had some issues installing a simple VGA monitor when my laptop display failed.

It may be that same principle applies to HDMI monitor - I don't know.

But try installing arandr

[COLOR=#111111][FONT=Ubuntu]sudo apt-get install arandr

[/FONT][/COLOR]and run from terminal .. Ctrl + Alt + F1

Another process I had to use to switch to external monitor is hitting Windows icon button + P (cycle through three modes).

---

