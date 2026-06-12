---
title: "Cursed with blinking cursor on black screen after reboot"
date: 2014-02-03
forum: General Help
---

### Post by dannyboy79 on 2014-02-03
I had recently installed Xubuntu 13.10 on a brand new machine i just built. Everything was working great, i was using the built in HD4600 in the i5-4670k haswell chip i have BUT i also have an HD7770 installed in the system which is disabled in the bios (well, bios is set to use igpu instead of pcie). I even played Trine 2 on high settings using the default i915 intel driver earlier in the day AND livestreamed it to hitbox.tv  so i know it's possible to use the igpu AND still leave the hd7770 in the system (there's a reason for this and it involved testing/benchmarking)

Yesterday I installed a bunch of software like kdenlive, steam games, etc etc and realized I wanted to use a separate partition for var, tmp, and opt. So I shutdown my system and booted into a livecd. I edited the fstab to use the new partitions I just created for var, tmp, and opt. I copied over those folders contents from the current systems folders to the new partitions and then I also noticed that fstab was using some uuid for swap which was not the 8.5GB partition I had made for swap so I changed my fstab to use the uuid of the partition for swap. After I felt i was all done doing what I needed to do I shut it down.

removed the livecd and fired her up, only to be presented with a black screen and a blinking cursor in the upper left corner. HUH???????? I don't understand what changed with the X server that it was now doing this. i tried adding nomodeset to my grub boot line which had no effect, i checked dmesg, .xsessions-errors, syslog, and Xorg.0.log and I didnt see anything that stood out as to why this was occuring.

Can anyone please help me trouble shoot this. I have been using Ubuntu since 2005 so I know my way around, I feel i have checked everything but hoping someone can shed some more light. Please do NOT suggest a reinstall because that is not the answer everytime something goes wrong (sometimes it's the answer but i don't feel in this case it is)

Thank you

---

### Post by Bucky Ball on 2014-02-03
A reinstall should always be considered a last resort. ;)

Is your system still looking to the same directories it was looking to previously rather than at the new partitions? The directories are, of course, empty now. Have you tried, as an experiment, booting from the install disk again and moving the info back to see if that is the cause?

Because the partitions are mounted does not mean the system is aware it should be looking to them for vital information. Or does it?

---

### Post by dannyboy79 on 2014-02-03
the system always looks to the same system directories. it's not like i deleted /var, /opt, or /tmp. those directories are still there. its just now a separate partition is mounted to them instead of using the partiiton that / is on. whatever was in those directories was copied into the new partitions so to linux it shoudl look the same. 

this is a graphics issue OR maybe a write permissions issue. maybe /tmp files can't be written to the new /tmp folder by my user so lightdm never appears, instead I get a blinking cursor. I need to do further investigation really. i noticed the problem when i booted up the system pretty much before work so i didn't have too much time to troubleshoot.

After work I can try to remove those extra lines i added from fstab and copy the data back from the partitions into their folders adn see if it boots. ther's a lot of variables i realize so i need to remove some in order to more easily troubleshoot

UPDATE: i know what I did wrong now. When I copied the items that were located within /tmp, /var, and /opt I used a livecd and merely launched thunar with sudo and did a copy paste instead of using rysnc so that it would preserve the owner:group and permissions. So basically my /var directory was all screwed up where all folders/files were owned by root and some directories even lost it's sticky bit etc etc. My HUGE mistake and it was a learning experience. In the end it was faster to perform a fresh installation vs trying to fix each directories owner and groups. Luckily i had /home on it's own partition so all my config and steam games were still there when I did an advanced installation method where i get to pick which partitions get formatted and mounted where. All is well and I am back up and running.

---

### Post by Bucky Ball on 2014-02-03
All good. Please mark thread as solved.

---

