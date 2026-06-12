---
title: "HELP PLEASE - Cannot get 'startx' to work on ubuntu on UserLAnd app for android"
date: 2019-09-27
forum: General Help
---

### Post by vexyzio on 2019-09-27
Hi guys, new to linux. I'm trying to get Diablo 3 working on a Samsung Galaxy Note 10+ but I can't get the startx command to work. Here is what I get in the command prompt when I attempt startx:

"[Config] failed to pre-init udev"

"Fatal server error
(EE)parse_vt_settings: Cannot open /dev/tty0(no such file or directory)"

"Xinit: giving up
Xinit: Unable to connect to x server: Connection refused
Xinit: server error"

Note: there was a log created at /var/log/xorg.0.log. If you need to see this I would need to be told how to find it as typing that in didn't do anything and I couldn't find the file on my device.

I'm hoping and assuming that this is an easy fix because once I can get the GUI to work I should be able to figure it out.

Thanks for your help anyone I appreciate it!

---

### Post by Skaperen on 2019-09-27
how did you know a log was created at /var/log/xorg.0.log?  was there output that said that?

try this command:  ls -l|fgrep -i xorg  and see if the file exists in some other form, such as compresses.

if the name if the file ends (after a dot) with some character that include a "z" then it is probably compressed.  do not try to output it, if so.

the file may no longer be there.

---

### Post by vexyzio on 2019-09-27
Okay so I ran the startx command again to see if I needed to create the file again. I then tried your command and nothing happened at all.

Yes there was output that said that.

Edit: There was no "z" in the file's name.

---

### Post by Skaperen on 2019-09-27
if nothing happened and you just get the next command prompt, that means the file is not there.  maybe it really is somewhere else.  or maybe something deleted it (because it was empty).  or maybe it never really existed.

---

### Post by vexyzio on 2019-09-27
Can you help me without it?

---

### Post by HermanAB on 2019-09-28
Are you sure your version of Ubuntu has Xorg installed?  Older versions used Wayland.

---

### Post by Holger_Gehrke on 2019-09-28
Did you read the documentation linked in the playstore description of the UserLAnd app ? It's at [https://github.com/CypherpunkArmory/UserLAnd/wiki/Getting-Started-in-UserLAnd](https://github.com/CypherpunkArmory/UserLAnd/wiki/Getting-Started-in-UserLAnd) and plainly says that you need to install an X-Server on Android and even gives a link to an X-Server on the playstore ([https://play.google.com/store/apps/details?id=x.org.server&hl=en](https://play.google.com/store/apps/details?id=x.org.server&hl=en)). I think this might be problematic, though. The description of that server says it only works on Android up to Version 5.

As far as your final goal of playing Diablo 3 on your phone is concerned: even if you do manage to get Linux working you probably won't be able to do that. Diablo 3 is written for Computers with X86 processor running windows (it works on computers with X86 processors running Linux with the windows compatibility layer wine), your phone has an ARM-processor. So you'd need not only Wine, you'd also need an X86-emulator. You'd probably get frame rates on the order of one frame every other second ...

Holger

---

### Post by vexyzio on 2019-09-28
At least I'll have a desktop on my phone, if anything.

As far as getting lxde to work Holger I have installed lxde and upon starting it I get this:

"(lxsession:6403): Gtk-WARNING **: 16:24:22.796: cannot open display: :0"

---

### Post by TheFu on 2019-09-28
Did you install an X/Server or not?  If not, you can't run programs that depend on having an X/Server.

---

### Post by Holger_Gehrke on 2019-09-28
Did you install and run the X-Server on Android before running 'startlxde' ? I've got it working on my Tablet, but it's slow since the X-server does not offer any of the extensions normally used to speed things up and controlling a mouse pointer through a touchscreen is not really fun ...

Holger

Edit: What do you get if you start to write an answer, install an X-Server and a (chrooted, I guess) Linux System to check that it works as it should, and post afterwards ? Ninja'd ...

---

### Post by TheFu on 2019-09-29
The only way I've gotten a Linux desktop on a tablet (a phone seems foolish), is to run VNC server on a chroot linux install and use a VNC viewer on android to connect to it.  It was big, slow, terrible keyboard mappings. It was bad enough that I stopped attempting to travel only with a tablet and switched to a small, light, Linux laptop.

I did travel with a Nokia N800 tablet ( 4in ) for a year. It natively ran Debian and a GUI called Maemo. At the time, it was amazing. I used it to ssh and rsync travel stuff back home. Poor battery was the biggest issue.

---

### Post by vexyzio on 2019-10-06
Yes, I've installed xorg. I redid the whole thing and now the command startlxde isn't found and using the command xinit /usr/bin/start ldxe give the error parse_vt_settings cannot open /dev/tty0 (no such file or directory) with no log file to look at as it closes the log. Someone help...

---

