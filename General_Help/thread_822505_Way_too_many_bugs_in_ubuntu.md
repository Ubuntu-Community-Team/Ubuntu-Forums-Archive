---
title: "Way too many bugs in ubuntu"
date: 2008-06-08
forum: General Help
---

### Post by Stoodle on 2008-06-08
I recently reinstalled Ubuntu. However, I'm having a lot of problems. When I first installed it, it didn't let me manually partition. I did the guided partitioning. Well, when I had it installed, I began running into many problems. Too many for me to use it. First, the resolution is stuck 1600 x 1200. When I try to change it in system>preferences, I can choose 1024x768 like I want to but it doesn't change when I choose apply.

Next, Firefox 3 is buggy as we all know. I decided to go back to Firefox 2 but it told me there wasn't enough room in tmp for it. I was thinking "I gave Ubuntu a lot of room when I installed it." In fact, I gave it too much room. it asked me how much free space I wanted to give it (first option of partitioning). It came out to around 68 GB I think. well, Windows was taking about 23 GB with a NTFS partition of around 30~ GB. I don't think it should have had that much room because of NFTS partition being so big.

Now, I can't boot up into windows. I don't think that it was erased, but I can't access that partition from Ubuntu (it asks for a password but does the shaking thing like I entered it wrong) and when I choose it in GRUB it says "starting up..." forever.

Help me out guys! I didn't have these problems when I had Ubuntu before!

Edit:

I'm also having a problem with Evolution not getting my mail from AOL. I had this working before and I followed some guides but I don't know what to do.

---

### Post by Barriehie on 2008-06-08
> ...First, the resolution is stuck 1600 x 1200. When I try to change it in system>preferences, I can choose 1024x768 like I want to but it doesn't change when I choose apply.

I had to restart for my changes to work with my resolution.  Also, I believe you can set that in /etc/X11/xorg.conf. Be VERY careful...  Other forumers may have a better/safer solution.

Barrie

---

### Post by Stoodle on 2008-06-08
I've restarted multiple times. I guess I will just have to try the X configuration file.

---

### Post by Barriehie on 2008-06-08
> **Stoodle said:**
> I've restarted multiple times. I guess I will just have to try the X configuration file.

Here is my original section from xorg.conf
```

[COLOR=SeaGreen] Section "Screen"
    Identifier    "Default Screen"
    Device        "Failsafe Device"
    Monitor        "Failsafe Monitor"
    Defaultdepth    24
    SubSection "Display"
        Depth    24
        Virtual    1400    1050
        Modes        "800x600@85"    "800x600@60"    "800x600@75"    "832x624@75"    "800x600@72"    "1024x768@85"    "800x600@56"    "1024x768@75"    "640x480@85"    "1024x768@70"    "640x480@75"    "1024x768@60"    "640x480@72"    "1024x768@43"    "640x480@60"    "1152x864@75"    "1280x960@60"    "1280x1024@60"    "1400x1050@60"
    EndSubSection
EndSection[/COLOR]

```I changed it to this:
```

[COLOR=Red] Section "Screen"
    Identifier    "Default Screen"
    Device        "Failsafe Device"
    Monitor        "Failsafe Monitor"
    Defaultdepth    24
    SubSection "Display"
        Depth    24
        Virtual    1400    1050
#[/COLOR][COLOR=SeaGreen] Modes        "800x600@85"    "800x600@60"    "800x600@75"    "832x624@75"    "800x600@72"    "1024x768@85"    "800x600@56"    "1024x768@75"    "640x480@85"    "1024x768@70"    "640x480@75"    "1024x768@60"    "640x480@72"    "1024x768@43"    "640x480@60"    "1152x864@75"    "1280x960@60"    "1280x1024@60"    "1400x1050@60"[/COLOR]
[COLOR=Red]        Modes        "1024x768@85"
    EndSubSection[/COLOR]
EndSection

```

---

### Post by Stoodle on 2008-06-08
Mine wasn't as big. I'd copy mine but Ubuntu's giving me such a hard time on everything that I don't know what to do and don't want to bother with it. Do you guys know what's wrong with the fact that I couldn't partition it and I can't access windows?

---

### Post by wolfen69 on 2008-06-08
with that many problems, i would do a re-install. a re-install only takes an hour. your problems could take days. better yet, why not go back to gutsy until 8.04.1 comes out?

---

### Post by Stoodle on 2008-06-09
I feel the same way. However, I still need to solve the problem of not being able to boot into windows.

---

### Post by Quantumstate on 2008-06-09
I have had very few problems with Kubongo HH.

---

### Post by ugm6hr on 2008-06-09
Assuming you are using Hardy...

> When I first installed it, it didn't let me manually partition.
Sounds like a problem with the install CD.  Did you check md5 & for errors?

> When I try to change it in system>preferences, I can choose 1024x768 like I want to but it doesn't change when I choose apply.
Try this:
```
sudo xrandr -s 1024x768
```

> However, I still need to solve the problem of not being able to boot into windows. 
Sounds like GRUB loads the Windows bootloader, but that doesn't launch Windows.  Something might have gotten corrupted during the partitioning stage.

---

### Post by Stoodle on 2008-06-09
What's Kubongo HH?

I think I'm going to reinstall, because I didn't have too many problems before when I was in Gutsy. However, my big problem is what do I do when I reinstall? Do I get rid of my Windows partition? Maybe it still works and Ubuntu's just giving me hard time. I'll be upset if that's not the case. If so, then I want to partition my computer myself. However, during the install it cries that it has an incompatible feature on any ext2 or ext3 partition I make. I want to partition in GParted and not partition in the install!

---

### Post by Stoodle on 2008-06-09
> 
Sounds like GRUB loads the Windows bootloader, but that doesn't launch Windows. Something might have gotten corrupted during the partitioning stage.


So you think windows is still there? Maybe I should look it up.

> 
Sounds like a problem with the install CD.  Did you check md5 & for errors?

That's when you check the CD for defects right? I did check the CD and it said it was fine. Like I said before, It's not that it won't let me partition manually, it's that it told me there were incompatible features.

---

### Post by ugm6hr on 2008-06-09
> **Stoodle said:**
> However, during the install it cries that it has an incompatible feature on any ext2 or ext3 partition I make. I want to partition in GParted and not partition in the install!

I have never encountered this.

Things I think that might be a problem:
1. HD failure
2. Corrupted HD partition table

What version of Windows did you have?  If Vista - GParted can cause issues (at least it did with older versions).

---

### Post by Stoodle on 2008-06-09
Got XP Home.

---

### Post by Stoodle on 2008-06-10
What do you think guys? Anyway I can at least salvage what's on my Windows partition? I'd like to copy it to my ext HD and completely wipe my hard drive. However, I'd also like to manually partition my computer and it won't let me. Installing Edgy was nicer.

---

