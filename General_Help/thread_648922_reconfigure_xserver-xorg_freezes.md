---
title: "reconfigure xserver-xorg freezes"
date: 2007-12-24
forum: General Help
---

### Post by njparton on 2007-12-24
I've just run into the well documented 8800 reboot xserver fails to load bug after my first reboot.

I can get to the command line by doing ctrl-alt-F1 but when I run the following command the wizard that pops up is frozen so I can't select yes or no.

```

sudo dpkg-reconfigure xserver-xorg

```

is this because Xserver is actually running and gdm failed to launch?  I've made sure gdm isn't running, how do I stop xserver?

Or am I wrong? What can I do to get this wizard to run?

---

### Post by njparton on 2007-12-24
I think it's because the file system is being mounted as read-only (ro in menu.list)?

However, when I remove that during boot after pressing e to edit, it still gets mounted read-only grrr.

Re-install coming up, must remember to edit menu.lst and fstab to avoid this before first reboot!

Anyone got any other ideas please?

---

### Post by tgilber1 on 2007-12-24
> **njparton said:**
> I've just run into the well documented 8800 reboot xserver fails to load bug after my first reboot.

I can get to the command line by doing ctrl-alt-F1 but when I run the following command the wizard that pops up is frozen so I can't select yes or no.

```

sudo dpkg-reconfigure xserver-xorg

```

is this because Xserver is actually running and gdm failed to launch?  I've made sure gdm isn't running, how do I stop xserver?

Or am I wrong? What can I do to get this wizard to run?

When booting, select recovery mode, which will boot the computer directly into root without starting gdm. At this point, you do not have to use sudo.  

dpkg-reconfigure -phigh xserver-xorg 

# just in case the xorg is hosed - it will give you a generic xorg.conf using the vesa driver

Then, try the following

dpkg-reconfigure xserver-xorg


After completing these command, type "exit" to boot into gdm

---

### Post by njparton on 2007-12-24
Thanks for your reply.

I ended up re-installing and making sure that the filesystem wasn't being mounted as read only and I also installed envy and got it to update my nvidia drivers before I dare reboot.

I'll keep your reply in case I get into more difficulty.

---

### Post by SOULRiDER on 2007-12-24
Make sure to keep a backup of aworking xorg.conf that way if something goes bad you have a backup. Keep both actually, one with nvidia drivers and one with the stock ones.

---

