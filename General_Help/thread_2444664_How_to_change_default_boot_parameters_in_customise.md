---
title: "How to change default boot parameters in customised LiveCD?"
date: 2020-06-02
forum: General Help
---

### Post by &amp;KyT$0P# on 2020-06-02
Trying to customise live CD of Xubuntu 20.04 using a script I wrote based mostly on [this guide]("https://help.ubuntu.com/community/LiveCDCustomization").  One customisation I'd like is to make [FONT=Courier New]nopersistent[/FONT] boot parameter default, in light of [this]("https://ubuntuforums.org/showthread.php?t=2431843").

I tried manually editing [FONT=Courier New]boot/grub/grub.cfg[/FONT] .  But when I tested my custom Live CD in VirtualBox, it was as if I didn't make any edits to boot parameters.  And grep'ing for [FONT=Courier New]quiet splash[/FONT] found several files which seem to have boot parameters, including some binary files :-k

In a running Ubuntu system, this would be the wrong approach to editing boot parameters - there I would edit [FONT=Courier New]/etc/default/grub[/FONT] then run [FONT=Courier New]sudo update-grub[/FONT] .  So I wonder if I just did it wrong?

How to edit the default boot parameters of the live CD?

---

### Post by &amp;KyT$0P# on 2020-06-03
bump

---

### Post by dragonfly41 on 2020-06-04
As a first thought would CUBIC help you (keyword: customise).

---

### Post by &amp;KyT$0P# on 2020-06-04
It did, thanks for the tip!  I looked through its code.  Looks like I was on the right track, but also needed to also edit [FONT=Courier New]boot/grub/loopback.cfg[/FONT] and [FONT=Courier New]isolinux/txt.cfg[/FONT] .  Quick testing that now in VirtualBox it seems to have worked :KS

I'll mark this thread SOLVED if it still looks good when I've had the chance to do more testing.

---

