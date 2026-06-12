---
title: "GRUB Problems after uninstalling"
date: 2007-02-01
forum: General Help
---

### Post by SHodges on 2007-02-01
Alright, I decided to use just Ubuntu on my laptop, and just XP on my PC.  Originally, I had two HDDs, one with XP, one with Ubuntu.  Using a "Western Digital Data Lifeguard Tools" disc that came with my newer 2nd HDD, I cleared the 2nd drive and formatted it for XP and everything, and everything was working fine.  *Then*, I had to reboot, and it didn't load Windows, it just gave me the follow error message.

"GRUB Loading Stage 1.5.

GRUB loading, please wait...
Error 17"

I'm not really sure what that means or what I did here (I'm guessing there was something on that 2nd HDD that I shouldn't have gotten rid of), but I have stuff on this PC that I really need to get.  All the Windows Data is there and working just fine, like I said the machine was working perfectly for a few days after I did the format, I just can't get to it, so I'm using an Ubuntu LiveCD right now.  My question is, how do I fix this so that I can get my computer to boot into Windows again?

---

### Post by Hatrist on 2007-02-01
Try this:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

If it doesn't help, post back.

---

### Post by SHodges on 2007-02-01
That doesn't help me, I need to recover Windows, not Ubuntu.  The troubleshooting section of that doesn't apply either, as I don't meet the prerequisite of "Your Ubuntu partitions are all still intact".  

When I first installed Ubuntu, it was onto the 2nd HDD, and it would come up with a boot list that had a bunch of ubuntu's, and XP.  I later decided to just keep Ubuntu on my laptop, and keep XP on my desktop, so I used that Data Lifeguard disc to format the 2nd harddrive (the one with Ubuntu) for use with XP.  The computer worked just fine, until I rebooted, and now it won't boot.  I just need to get it to boot into Windows.  All of the necessary data is there, it must be possible to get to it.

---

### Post by rsambuca on 2007-02-01
In formatting your second HD, you deleted the grub instructions.  You need to use your original XP installation disk and run "fixmbr"

---

### Post by SHodges on 2007-02-01
I'll try that, thanks.


EDIT: That worked.

---

