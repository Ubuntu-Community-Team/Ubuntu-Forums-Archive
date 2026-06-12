---
title: "keyboard layout screwed up when installing Ubuntu plus partitioned disk wrong way"
date: 2021-06-28
forum: General Help
---

### Post by zeljko-1979 on 2021-06-28
[COLOR=#353C41][FONT=&amp]Ok guys,[/FONT][/COLOR]
[COLOR=#353C41][FONT=&amp]1.I've decided to try Ubuntu but when installing I thought I made 10 GB swap but instead I made 100 GB swap and whol entire disk which is 500 GB in size was used as primary partition and I wanted only 50 GB of a drive.[/FONT][/COLOR]
[COLOR=#353C41][FONT=&amp]So how do I repartition the drive inside Ubuntu,so I can have some free space left 500GB-(10+50) GB.[/FONT][/COLOR]
[COLOR=#353C41][FONT=&amp]Now all the HDD space is populated as 2 partitions which I didn't want.[/FONT][/COLOR]
[COLOR=#353C41][FONT=&amp]2. They keyboard layout on the laptop doesn't match the ones which were installed with Ubuntu,because z=y y=z and all the other characters are ate the wrong places.[/FONT][/COLOR]
[COLOR=#353C41][FONT=&amp]I want to set as default the layout which is like on the laptop but dunno which one to choose from the list in Ubuntu regional settings.[/FONT][/COLOR]
[COLOR=#353C41][FONT=&amp]I'm from Serbia.
[/FONT][/COLOR][IMG][[IMG]https://i.postimg.cc/sMPGnVH1/20210628-150043.jpg[/IMG]]("https://postimg.cc/sMPGnVH1")[/IMG][COLOR=#353C41][FONT=&amp]
[/FONT][/COLOR]&#8203;[COLOR=#353C41][FONT=&amp]
[ATTACH=CONFIG]288741[/ATTACH][ATTACH=CONFIG]288742[/ATTACH][/FONT][/COLOR]

---

### Post by zeljko-1979 on 2021-06-28
So I did manage to figure out keyboard layout ow onto the partioning,when tried got this message,from the pic below,so what now?
Besides I can not repartition swap partition onlz primary system partition.
[ATTACH=CONFIG]288744[/ATTACH]

---

### Post by ajgreeny on 2021-06-28
You will have to boot to a live system and make your chosen changes in that, probably using gparted for ease of use.  Depending on what hardware you currently have and the use you make of your system, you will probably need swap of no more than 2G or 4G; the output of command ```
inxi -Fzx
``` will help with that decision.

When booted to a live system the swap partition will normally be detected and used so you will need to right click on that in gparted and choose Swapoff or unmount it, I can not remember what the option is as I no longer use a separate partition for swap; Ubuntu now uses a swap file instead.

Once swap is off or (or unmounted) you can either extend the main Linux partition into the free space, though this will take a long time as the partition will have to be moved not just extended as the swap is to the left of the main partition, or a new partition could be created for data storage.

---

### Post by GhX6GZMB on 2021-06-28
Best option: redo from start. Honestly. Been there, done that (many times).

---

### Post by ajgreeny on 2021-06-28
Having just seen this post and thought about this a little longer, I think ml9104 may well be right, particularly if this is a newish install with few files so far created which you will need to backup and restore after a second install.

---

### Post by tea for one on 2021-06-28
Yes, reinstall as advised by [COLOR="#0000FF"]ml9104[/COLOR] and [COLOR="#0000FF"]ajgreeny[/COLOR].

If nothing else, a re-installation will give you more confidence and experience with the installation process.
It will allow you to correct and improve on your previous effort.

---

### Post by NM5TF on 2021-06-29
> **tea for one said:**
> Yes, reinstall as advised by [COLOR="#0000FF"]ml9104[/COLOR] and [COLOR="#0000FF"]ajgreeny[/COLOR].

If nothing else, a re-installation will give you more confidence and experience with the installation process.
It will allow you to correct and improve on your previous effort.

+1
.....been there so many times with my Arch Linux installs...like tea for one says, it will give you much more confidence in your
own abilities to learn how Linux works...and will clean up whatever went wrong with the 1st try....:P

tommy

---

