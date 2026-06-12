---
title: "any way to get half my HDD back? :P"
date: 2006-11-05
forum: General Help
---

### Post by Ludwig7666 on 2006-11-05
hey all.. I'm somewhat new to linux still. I don't get into it much . but here's my qustion..

I have a 120GB HDD. I also installed Ubuntu and Windows XP Home on it. All was working well till I had to format my windows. So I managed to format just my windows partition just fin.. Then as I started up my computer I noticed somethign odd happening. No option to click on Ubuntu at all........ Then I thought for the day that I must of formatted the whole thing.. Then I went and looked at my HDD size... "55.8GB"?!?!?! I'm losing some HDD space big time here.  I understand that microsoft is fusy and can't read linux format but is there a way to get my other half or get the option to use ubuntu again? I only resently thought of something in the bios, but can't see it being in there to fix this problem.. Anything else??

Not sure if this is a common thing and I have no clue how to google this one. :D

---

### Post by po0f on 2006-11-05
Ludwig7666,

You'll have to boot with a live CD and reinstall GRUB into the MBR.

---

### Post by David Corrales on 2006-11-05
Thing is, your partitions are not "merged" after you formatted. Why don't you download the GParted livecd and fix it up. It's an awesome tool.

---

