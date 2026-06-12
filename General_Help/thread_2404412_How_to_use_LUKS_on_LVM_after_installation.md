---
title: "How to use LUKS on LVM after installation?"
date: 2018-10-23
forum: General Help
---

### Post by thatrandomguy+ on 2018-10-23
Hello,

After a day's worth of reading and scrambling my head, I finally figured out how to install Lubuntu 18.10 with LVM. :-k

The issue now is that the only reason I opted for that setup was to encrypt the entire LVM partition.

The installer doesn't allow for on-demand creation of LVs unless a VG has already been provisioned&#8212;so I was forced to simply create the LVM partition and VG.

AFAIK, I'm not understanding how this is supposed to map out.

Is it possible to encrypt anything at this point or do I have to figure out a way to get that going during install?

TIA

---

### Post by TheFu on 2018-10-24
If you are struggling with LVM, then manually setting up LUKS with LVM will be very difficult. It can be done, but it is non-trivial. I've failed with multiple attempts on 16.04.  There are how-to guides in these forums. When you find the latest, you'll see what I mean by non-trivial.

Generally, it is 1000x easier to choose full encryption + LVM during installation.  This will create a few partitions, then encrypt one, and create the PVs, VGs, and LVs inside it.  It is fairly painless.

BTW, I have no idea what you mean by "LMs".

Might I suggest that you learn LVM using a virtual machine first?  This way, you risk nothing except time.  There are how-to guides for LVM on the internet with step-by-step instructions.  HowToForge and IBM sites have some that I've used.  Because LVM is meant to be used by Linux admins, there isn't any GUI and help is provided in the manpages.  LVM works the same as the commercial LV tools like Veritas and HP provides.  Same architecture, same names, same ideas about laying out how things fit together.  If you've been trained in HP-UX, Solaris, AIX, or any other system that supports volume management, Linux LVM is the same.

---

### Post by thatrandomguy+ on 2018-10-24
@TheFu

I want to do during install but Calamares won't let me create an LVM partition on the fly. It assumed I already have a volume group setup. The LV (logical volumes) are the only other things I can create during the install (with calamares).

I've tried using KVPM, GParted, and Gnome DISKS together to get what I'm asking for and it ain't working.

Whenever I create an encrypted LVM2 PV via the installer, the outcome results to me not being able to create any LV. It wants them already created (I assume). My issue with that is that I don't know how to provide for LUKS in that fashion.

I just ran up a VM and attempted to create the encrypted LVM PV using Gnome disks before running the installer. Now I can't get to the volume because it can't open it. I'm stuck. :?

---

### Post by TheFu on 2018-10-24
If you use the default Ubuntu installer, then you have either automatic or 100% manual storage setup.  The 100% automatic "Encrypt + LVM" will use the entire disk and setup encryption + LVM.  2 LVs will be created, but post install, you can resize those and create new LVs as desired.

Going with the manual storage setup, means you have to do everything in the proper order. All my attempts doing this for 16.04 failed to result in a correctly setup boot system.

I don't know anything at all about Calamares or KVPM or Gnome disks.  I've never used them.  Gparted doesn't do LVM.  Most partitioning tools don't, IME.

Paddy put a guide in these forums that you might find helpful.  This isn't my "itch."  Good luck.

---

