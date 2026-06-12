---
title: "Wow! Did I have a crazy problem! Luckily it's solved now..."
date: 2007-06-13
forum: General Help
---

### Post by michaelzap on 2007-06-13
All of a sudden my Feisty Ubuntu started crashing on me this afternoon in the weirdest way. First I was told that my hard drive was nearly full, although there should've been some 70 GB free. And then I would see different total sizes for my drive in gparted, Nautilus, and the Device Manager, but all of them were telling me that my drive was nearly full. Then I would suddenly lose access to network shares, programs would start to crash in waves, and when I would try to reboot the restart and shutdown options weren't even on the shutdown dialog. So I would log off and then be greeted with a totally odd logon screen (a theme I've never selected) that failed to respond. Basically things went totally insane and my installation became completely unusable, and this seemed to happen all of a sudden and without me having done anything in particular.

It turns out that Ubuntu was actually using a different partition for saving files than it was for the system! This happened because a few days ago I decided that I was definitely going to keep Ubuntu as my main OS and so I wanted to move my existing 50GB partition on a drive that also has XP to its own 120 GB drive. I used gparted to copy that partition to the new drive and then resized it to the full 120 GB (minus 3 GB swap), but I didn't delete the old partition because I thought who knows maybe I'll need something from it. That was a mistake!

So anyway long story short I decided that maybe this had something to do with my current weirdness and I booted off the live CD and used gparted to delete the old partition. Now my Ubuntu boots up just fine and everything registers the drive as its correct size (and far from full). Which is great. The only negative to this wacky story is that I lost all files and changes that I had made since moving to this drive (email, installed programs, etc.), but luckily I can recover most of that without too much trouble.

Just thought I'd share my story in case some other dolt does what I did and is wondering what's going on...

On a hardware/system level, I'm really not sure how this could happen, but those of you who work on those things might want to see if there's a way to prevent this in the future.

---

