---
title: "grub rescue while booting my old computer"
date: 2016-11-25
forum: General Help
---

### Post by karasuman on 2016-11-25
It's been well over a year since I turned this computer on. It has Windows 7 and a borked Ubuntu partition (I upgraded without doing a clean install).

When I turn on the computer, I get "error: unknown filesystem" and a grub rescue prompt.  I recall that there was something I typed in order to boot into Windows, but I have no idea what it was.  Can someone help me with that?

Once I finally DO get into Windows, I'm going to want to fix that broken OS by reinstalling Ubuntu. It's just been so long since I used a dual boot machine that I don't remember how to do any of this.  I'd really appreciate any help you can give me.  For all that I've been using linux since 2007 or so, I don't remember any of this stuff and I feel like a newborn.

---

### Post by oldfred on 2016-11-25
Easiest to use Windows repair disk to fix Windows.

If just a boot issue Boot-Repair can reinstall a Windows type boot loader, but cannot do most Windows fixes.

You may just need fsck to repair file system or reinstall of grub. But only worthwhile if a current version.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by karasuman on 2016-11-25
Unfortunately, this being an old computer, I don't have a repair disk.  Also, the CD drive on this computer is screwed up, so I can't use a disk, anyway.  I can't boot into a live cd, or I would have done that already.

But... I figured it out!  Here's what I did:

ls
(this gave me a list of partitions--I tried them all until I found the one that worked)
set prefix=(hd0)/boot/grub
insmod normal
normal

And then I get a list where I can choose the OS I want to boot.

---

### Post by Cavsfan on 2016-11-25
> **karasuman said:**
> Unfortunately, this being an old computer, I don't have a repair disk.  Also, the CD drive on this computer is screwed up, so I can't use a disk, anyway.  I can't boot into a live cd, or I would have done that already.

But... I figured it out!  Here's what I did:

ls
(this gave me a list of partitions--I tried them all until I found the one that worked)
set prefix=(hd0)/boot/grub
insmod normal
normal

And then I get a list where I can choose the OS I want to boot.

Great! Nice work! Now you can probably just re-install grub and you should be good to go.

If you don't already know how, instructions [here]("https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2_from_a_Working_System").

---

### Post by karasuman on 2016-11-25
Thanks!  Even better!

---

