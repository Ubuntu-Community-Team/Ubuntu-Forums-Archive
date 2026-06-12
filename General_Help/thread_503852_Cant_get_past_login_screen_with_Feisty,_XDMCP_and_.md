---
title: "Cant get past login screen with Feisty, XDMCP and Xming or CygwinX"
date: 2007-07-18
forum: General Help
---

### Post by madanasta on 2007-07-18
Hello all

I am not exactly a Linux expert, although I do have some experience with it. I know this subject has been discussed a lot, but my problem is slightly different and besides I haven't yet been able to locate any conclusive solution.

I've recently installed Feisty on a machine destined to be totally headless, so I used VNC to control it remotely. However, I'd rather use XDMCP for that. So, I enabled remote logins and installed CygwinX on a WinXP Pro machine. The Feisty machine's set with gdm and Gnome btw. By running "Xwin -query xx.xx.xx.xx" on Cygwin, I've been able to get to a gdm login screen but no further. When I enter a correct username/password, the screen instantly returns to username entry with a system beep and no other feedback whatsoever. In contrast, a wrong username/password results in an appropriate error message, so authentication seems to work fine. I haven't been able to locate anything in syslog and other logs, but that might just be me :). Exactly the same behaviour with Xming. There is no firewall on the XP machine. I am not enabling clipboard integration to avoid (apparently well-known) problems when creating remote Gnome sessions. I also tried to install xfs and make CygwinX and Xming use a remote font server just in case, but that resulted in problems connecting to xfs and that's another story :).

I'd really appreciate any ideas, especially as to settings that *must* be made in order for xdmcp to allow remote logins with gdm and Gnome, experiences from working similar setups and related problems, or at least where I should look to get feedback on what happens when gdm tries to create a Gnome session and fails (because that's what I suspect happens here).

Thank you all in advance

---

### Post by madanasta on 2007-07-20
Nailed it down. It was the "Disable multiple logins for a single user" setting on the "General" tab of the "Login Window Preferences" dialog (System | Administration | Login Window)... the one whose tooltip says "This only works for session's running on Virtual Terminals started with gdmflexiserver, **and not with XDMCP**". I was already logged-in with vnc, so gdm wouldn't start another session due to that setting, no matter that I was trying to start it with XDMCP.

And now, I am on to solving the gray rectangle problem :lolflag:.

---

