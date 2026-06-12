---
title: "Boot XP Partition inside ubuntu ?"
date: 2007-04-06
forum: General Help
---

### Post by lynxus on 2007-04-06
Hi,

Question-
Is it possible to boot the XP install i have on one of my drives in some form of window?
I have almost migrated completely to Ubuntu, but i need to use Dreamweaver & Fireworks and they dont seem to like wine etc.

i know i could gimp etc, But for some reason Dreamweaver does what i want lol 

Sorta like a virtual machine, But rather than actually reinstall windows on a VM to run it can it just boot the exsisting install on my drive?

Cheers
G
Theres a magic :KS in it for the winner :)

---

### Post by mac.ryan on 2007-04-06
> **lynxus said:**
> But rather than actually reinstall windows on a VM to run it can it just boot the exsisting install on my drive?

I am 100% sure it is possible to launch an existing installation of XP within VMware player without having to reinstall it. It is a kind of tricky thing that happened to be discussed in a thread I was participating in it.

Unluckily I couldn't find it anymore now. I can only remember that one of the users (actually running in that configuration) was concerned about the fact that one day the XP installation might cease to work if booted via grub, due to the changes done for booting it within VMware.

Sorry for not being able to be more useful... :(

---

### Post by AusIV4 on 2007-04-06
Some months ago, I decided to try and get my XP partition running in VMWare. I did a Google search, and was able to find instructions on how to map a vmdk to a physical disk, and I was able to boot up the VM to my physical Windows partition. But that's as far as I got - it wanted me to reactivate my copy of Windows for the VM - in which case I no longer would have been able to boot it. Since my intent was to run a few programs on the VM and occasionally reboot to play games that the VM couldn't handle, it wasn't a viable option to reactivate for the VM.

This page [http://netsecurity.about.com/od/windowsxp/qt/aaqtwinxp0829.htm]("http://netsecurity.about.com/od/windowsxp/qt/aaqtwinxp0829.htm") explains the basic principle. You need to keep a copy of the activation files it mentions for each hardware profile, then copy it to the appropriate place before you boot Windows. This will require reactivating windows once for the VM, but if you do it properly, you should be able to switch back and forth without having to call Microsoft. If you decide to take this approach, it's worth noting that if you change the amount of alloted memory in the VM, you'll have to re-activate.

If you're looking to have an identical VM, without ever needing to physically boot back to your Windows partition, I'd reccomend using the VMWare converter (a Google search should find it). This makes a VM copy of a physical machine. You may have to reactivate, but if you're not going to be booting back to windows, this shouldn't matter.

---

