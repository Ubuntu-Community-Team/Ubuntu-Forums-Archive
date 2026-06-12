---
title: "Add 2nd drive (MEPIS) to GRUB"
date: 2007-05-02
forum: General Help
---

### Post by fishmorg909 on 2007-05-02
I've tried out Mepis, and it's so good I want to set up dual boot - Ubuntu on HDD1, and Mepis on HDD2.  What's the best way to do this? I've looked and looked on the forums, but I can't find what I want.

(I installed Mepis on the second drive seperately, then installed it as a second drive. Could I just edit GRUB? How?)

(Edit) I am already running Ubuntu Dapper right now... but if I change boot sequence in BIOS, the Mepis HD won't boot.

---

### Post by Eddie Wilson on 2007-05-02
I have MEPIS 6.5 installed on my system and also I have Ubuntu 7.04 and Windows Xp. I'm not really sure how you have your system set up or what your drives are called but the way I did it was I already had windows installed then I installed Ubuntu 5.10. After that everytime I upgraded I would always have to edit the grub menu list to get Mepis back on the boot menu. It was fairly easy because I have everything on one drive.(except for a drive I use for music and data sharing between systems). The last linux system you install will usually be the menu in charge. In my case Ubuntu is on hda2 and Mepis is on hda3. I logged in as root and had to edit the grub menu list. What I really did was to go to partition that Mepis was on and copied the section of the menu.lst that loaded Mepis and then went to the partition that Ubuntu was on and pasted that part in the menu.lst that was booting the system. It works like a charm and should give you no problems at all. You can also edit the titles to suit what you want it to say. I hope this helps.
Eddie

---

### Post by Eddie Wilson on 2007-05-02
I forgot to mention that your drives will more than likely be called hda1, and hdb1 or something like that.
Eddie

---

### Post by confused57 on 2007-05-02
> **fishmorg909 said:**
> I've tried out Mepis, and it's so good I want to set up dual boot - Ubuntu on HDD1, and Mepis on HDD2.  What's the best way to do this? I've looked and looked on the forums, but I can't find what I want.

(I installed Mepis on the second drive seperately, then installed it as a second drive. Could I just edit GRUB? How?)
Can you boot your Mepis drive by selecting it to boot first in bios?  Since you had Ubuntu installed, grub recognizes this drive as (hd0) and your Mepis drive would be (hd1)...but installing Mepis separately on a separate hard drive without the Ubuntu drive connected, the Mepis grub thinks it (hd0).  You might need to boot into Mepis and post your /boot/grub/menu.lst:
```
kwrite /boot/grub/menu.lst
```
at least by posting it you'll have a copy you can refer to, if needed.

You might need to change your Mepis grub entry to root (hd1,0), before you can boot Mepis, using Ubuntu's grub...which you can do by configfile:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

Here's an idea, which probably won't work, but you might try booting Mepis with this added to your Ubuntu /boot/grub/menu.lst:
```
title   Mepis
root (hd1)
chainloader +1
```
I've never tried this & as I mentioned it probably won't work, but it would be an attempt to boot to the Mepis drive mbr?

---

### Post by confused57 on 2007-05-02
If you haven't customized Mepis to the point that you don't mind reinstalling it, that would probably be the easiest solution.  What I'd suggest is to have both drives connected, install Mepis to your 2nd hard drive, but select to install grub to the Mepis root partition...then all you'd need to do to boot Mepis is to add an entry to your Dapper menu.lst:

```
title   Mepis
rootnoverify (hd1,0)
chainloader +1
```

This is the method that I use to boot multiple Linux distros, using 2 hard drives.

Added:  If you want to try to get your current setup working, you could try mounting your Mepis root partition and editing your menu.lst:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

you would probably need to change the line with root to (hd1,0) and the kernel line may need to be changed to something like root=/dev/hdb1...then add a Mepis entry to your Ubuntu menu.lst, using configfile method.
Also, you might want to make sure the hard drive jumper settings are correct if you switched it from master to slave...if you're using cable select, this shouldn't be a problem.

---

### Post by fishmorg909 on 2007-05-02
> **confused57 said:**
> If you haven't customized Mepis to the point that you don't mind reinstalling it, that would probably be the easiest solution.  What I'd suggest is to have both drives connected, install Mepis to your 2nd hard drive, but select to install grub to the Mepis root partition...then all you'd need to do to boot Mepis is to add an entry to your Dapper menu.lst:

```
title   Mepis
rootnoverify (hd1,0)
chainloader +1
```

This is the method that I use to boot multiple Linux distros, using 2 hard drives.

Thanks, confused57 -- this advice worked perfectly! :)

---

