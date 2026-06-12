---
title: "Messed up graphical login window"
date: 2007-07-01
forum: General Help
---

### Post by ceil420 on 2007-07-01
Wow I hate lynx... *ahem*

I've recently done a few things to my computer, and now my graphical login doesn't work. I'll list the things I've done in the order of importance on this particular issue.
1) Designed and installed a new theme. I doubt this is it, but I'm including it anyway, because it was designed from scratch (I didn't just edit a default theme), and I don't know what all a theme is capable of messing up.
2) Updated Xubuntu Feisty. Note that this is updated Feisty, not TO Feisty; I've had the OS itself for a while. A new kernel version (2.6.20-16-generic) was included in the updates. I don't think this is really the culprit, but it's more likely to be this than the theme.
3) Changed Login Window settings. Specifically, I added sounds (system sounds, nothing custom), and I may have changed the window's appearence itself, but I'm pretty sure I decided against that. I think this is most likely what's causing my little "issue".

I've already updated nvidia-glx-new and it's kernel-source whatever. I've also tried **dpkg-reconfigure xserver-xorg**, but to no avail. The most drastic thing I've tried is re-naming /etc/gdm/gdm.conf-custom, and backing up gdm.conf and putting factory-gdm.conf in it's place. Restarted X, and still no graphical login screen. It does the same thing it did when my problems started: shows the nvidia splash screen, blanks for a second or three, shows the nvidia splash screen again, then blanks again and shows a "waiting" cursor (rotating hourglass). Forever.
I can use startx from tty to get my GUI back, but gdm uses 94-96% of my CPU when I do so (according to Conky desktop sysinfo thing). When I kill gdm, it does the nvidia>blank screen with cursor bit and hangs there. I have to go back to tty and ctrl+c for X to actually "close", though, because I could still see my xchat self until I did so.
Any ideas? I'm not hardcore enough to actually be enjoying this text-only stuff :( And while I can use startx, I don't like gdm using all my CPU power like that :x

---

### Post by ceil420 on 2007-07-02
Update: A friend kindly informed me that i can **/etc/init.d/gdm stop** and then startx without having gdm eat up my CPU. This is a satisfactory temporary solution (it's certainly making posting on this forum easier; and navigating my dozens of channels in IRC), but I'd like something a little more long term.

Oh, and some details: I'm running Xubuntu Feisty on kernel version 2.6.20-16-generic (upgraded from -15- yesterday, and no, booting with the old kernel doesn't fix it). My graphics card is an nVidia GeForce FX 5200, but I don't think that matters. I don't know what version of Xfce I have, or how to find out.

If you've read it this far, thanks for your time; if you try to think of a solution, thanks for your effort; if you fix my issue, thanks for everything :)

---

### Post by ceil420 on 2007-07-02
Nobody knows? :( I know linux boxes are known for their uptime, but I can't keep my computer on forever, and I'd like to get this resolved before next shutdown (and before I forget how to **sudo /etc/init.d/gdm stop || startx** :x)

---

### Post by ceil420 on 2007-07-03
My haunted computer (sorry, inside joke) strikes again :o Storm knocked out the power, and when I re-booted my computer, I got the X login window just fine. Wish I could post a solution for future victims of this issue, but I don't really know what happened.

---

