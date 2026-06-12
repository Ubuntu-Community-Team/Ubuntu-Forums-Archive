---
title: "Random crashes on T22"
date: 2008-06-12
forum: General Help
---

### Post by Chonnawonga on 2008-06-12
I've been using Gutsy on an old IBM Thinkpad T22 for the last month or so. Everything starts up nicely, no problems with hardware support, but once in a while (say, every 30 to 60 minutes, on average) it crashes. Hard. I can't figure out a pattern to it at all: it seems to happen even when the computer's doing very little. It happens in Gnome and in XFCE.

I can't get out of the crashes with CTRL+ALT+DEL, or with Alt+SysRq+RSEIUB. The clock stops, the mouse won't move, but the laptop's hard-wired brightness controls still work.

How do I go about tracing these crashes? Is there a log file or something I could check? I'd like to figure out why this is happening so I can fix it.

Thanks!

---

### Post by robaerus on 2008-11-14
Hello,
does this problem happen also when running a LiveCD or any other operative system than Ubuntu? Try to check the logs in /var/log/kern.log and see what it is reported.
Cheers

---

### Post by Chonnawonga on 2008-11-14
Hi robaerus,

Thanks for the offer to help. About a month ago, the T22 went back to the friend I had borrowed it from on a (very) long-term loan. Hopefully your suggestions will be useful to someone else, though!

Cheers!

---

### Post by ECPCLINUX on 2008-11-14
Hi, I would ask if you are running Compiz? If you are go to System/Preferences/Appearance/Visual Effect tab and click on "None". Maybe it will help. I used it once in a smaller system I installed Ubuntu for a friend and it helped. Also, you can try this, I saved it cause I'm a "forever newbie" and I always forget it,lol but here it is:

copy/paste to Terminal >>>

gconftool-2 -t str --set /apps/gnome_settings_daemon/keybindings/power ""
gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"

This should give you that CTRL+ALT+DELETE effect as in windows, so you can terminate, whatever is causing the problem. Of course that's assuming it's not a hardware issue. Please note this does not seem to work in a 64bit System. A T22 should be 32 bit only cause it's an older system hence, it should be perfect for it. Hope this helps, if not maybe someone more knowledgeable will come a long and help. Good luck!

---

