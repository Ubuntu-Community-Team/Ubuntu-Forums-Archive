---
title: "TuxOnIce encrypted (LVM on LUKS)"
date: 2013-11-28
forum: General Help
---

### Post by pok1yoyo on 2013-11-28
Hi!
I am not sure if I hit the right forum, but here is my question:
I use Ubuntu 13.10 64bit (fresh). I installed TuxOnIce using ppa, and it works great, except that I cannot resume from hibernation (because my disk is encrypted using dm-crypt). I have tried making it work using [this]("https://help.ubuntu.com/community/EnableHibernateWithEncryptedSwap") guide, however, it I cannot seem to find TuxOnIce conf file. I would really appreaciate if someone knows how to do this.
What I did so far are the first (including) 9. There is no```
 /etc/acpi/hibernate.sh
``` which I believe is non-existent in Saucy. So I though about puting it in TuxOnIce conf file (since I use TOI for hibernation).
Thanks for any tips.
Regards.

---

### Post by zanfur on 2014-04-20
I just got this working on Saucy.  The guide you linked to is correct for Saucy, except skip steps 9 and 10.  The saucy cryptroot script is smart enough to do the right thing already from the crypttab (see lines 253-257), so don't modify it to add hardcodings -- they would be overridden by updates anyway.  Also, saucy doesn't use the acpi scripts anymore, so you can ignore that bit.  I think TOI doesn't even need the initramfs updates, because it actually sets the resume target itself using a different mechanism, but if you want standard hibernate to ever work you should probably do step 11 anyway.

About the TOI config file, it's not a "file" per-se, but it's all in /sys/power/tuxonice.

---

