---
title: "Mix SATA and IDE drives?"
date: 2012-11-08
forum: General Help
---

### Post by poliltimmy on 2012-11-08
I have Windows Vista on a 180G IDE HD. I have Ubuntu 12.04 on a 320G SATA HD. I want to put them in the same box and dual boot. How can I do this without goofing up?

---

### Post by oldfred on 2012-11-08
Is it a newer system? But not so new as to still have IDE connector?

Windows is licensed for one computer, so it may not work at all.

Just replacing motherboard on my XP computer, I had to personally call BillG and beg to renew license. :) Actual renew windows window was hidden under the this system cannot be booted without license window and it took me a while & several reboots to realize I had a way to connect to Microsoft to update license.

Depends a lot on BIOS.
Some older systems have issues with mixed IDE & SATA. Most work, but PATA drive is often promoted to sda and then the SATA drives become sdb, sdc etc.

---

### Post by poliltimmy on 2012-11-08
The motherboard  Acer M1100 has one IDE and the rest SATA. It has a legal install. That is the motherboard I want to use.

---

### Post by Mark Phelps on 2012-11-08
I have much the same situation -- mix of IDE and SATA drives.

What works for me is the following:
1) Keep each OS on a physically separate drive and have only the boot loader for that OS on the drive.
2) Boot from the Ubuntu drive by default
3) Use GRUB on the Ubuntu drive to put up a menu to choose the OS to use.

This way, each drive remains independently bootable, and upgraded to either OS don't affect the other in any way.

---

### Post by nwalkey on 2012-11-08
Another option would be to have two partitions on your 320gb drive and your other drive set up as a storage drive that you can access from both operating systems. This is how I set my computer up and I find it very effective. Then again, if you want to be able to swap hard drives out while keeping the operating systems separate then you're best bet is to stick with two separate drives with two separate oses on them. Depending on the drives and such you might find that both oses run slightly better being installed on the sata drive. Both ways work, just a matter of what is better for you :)

---

