---
title: "Deleting the Microsoft partition? What 'bout GRUB"
date: 2013-01-07
forum: General Help
---

### Post by Mark_in_Hollywood on 2013-01-07
I want to delete the Microsoft partiton (about 70 gigs) and enlarge the /home to use it for my Ubuntu box.

What will GRUB do when that partition is gone? How can I make sure the MBR and GRUB will boot into Ubuntu (Precise Pangolin 12.04LTS)?

What I'm trying to understand is whether removing the MS partition will confuse my current GRUB config and what about that 100 meg that MS uses for it's 'hidden' or whatever they call that?

I will do a /home backup before I do the deletion, but I sure would like to know if I'm making a mess of the Linux OS, MBR, GRUB before hand and try to avoid as much headache/heartache as possible.

This is MicroSoft Win 7-64 "ultimate".

---

### Post by cottfcfan on 2013-01-08
It all depends whether or not Ubuntu or Windows controls Grub/boot.
If you installed Ubuntu last & that is controlling Grub,then all you need to do is delete your Windows partition from inside Ubuntu, expand your home partition into the empty space & then run ```
sudo update-grub
```
If Windows controls boot then from inside your Ubuntu partition, run, ```
sudo dpkg-reconfigure grub-pc
```
This should give Ubuntu control (reboot to check), then do the above.

---

### Post by sgage on 2013-01-08
> **cottfcfan said:**
> It all depends whether or not Ubuntu or Windows controls Grub/boot.
If you installed Ubuntu last & that is controlling Grub,then all you need to do is delete your Windows partition from inside Ubuntu, expand your home partition into the empty space & then run ```
sudo update-grub
```
If Windows controls boot then from inside your Ubuntu partition, run, ```
sudo dpkg-reconfigure grub-pc
```
This should give Ubuntu control (reboot to check), then do the above.

Or just run 'sudo grub-install /dev/sda', followed by 'sudo update-grub'.

---

### Post by Mark_in_Hollywood on 2013-01-08
I had installed Windows first. Thank you. I'm closing this thread.

---

