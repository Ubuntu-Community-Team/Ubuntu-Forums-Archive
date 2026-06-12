---
title: "openbox --exit dumps me to a logged in root shell that ignores most keystrokes"
date: 2014-07-11
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2014-07-11
14.04 installed from the mini.iso with xorg, openbox, lightdm and lightdm-gtk-greeter added. So, strictly speaking, this is Ubuntu, but I tagged it Lubuntu because all the relevant parts should be the same as a standard Lubuntu, even though I don't have all of the LXDE & Lubuntu bells and whistles. 

Anyway, everything worked fine until recently but suddennly```
openbox --exit
```shuts down the openbox session as expected but instead of a lightdm/lightdm-gtk-greeter gui login screen as usual, x is shutdown and I get dumped to tty 7, already logged in as root, judging by the prompt. But it is oddly non-responsive, refusing to notice any letter keypresses. It will respond to cntrl-alt-Fn to switch to another tty normally and it will reboot in response to cntrl-alt-del. I can, without rebooting, switch to another tty, login as user, and startx and then I have a normal openbox session. If I use ```
openbox --exit
```again from that session, the same thing happens except I'm dumped to a tty in which user is logged in and that tty accepts input normally. I tried```
openbox --exit > afile
```both from a windowed terminal in the openbox session and from a tty. They make a 0 byte file with no content.

The last thing is tty 7 is:```
Bash: Cannot set terminal process group (1015): Inappropriate ioctl for device
Bash: No job control in this shell
```I don't see anything odd in /var/log/boot.log or dmesg.

Any ideas on how I can figure this out or what might be wrong?

---

