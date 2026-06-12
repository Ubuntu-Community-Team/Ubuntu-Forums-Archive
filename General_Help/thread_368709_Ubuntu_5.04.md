---
title: "Ubuntu 5.04"
date: 2007-02-23
forum: General Help
---

### Post by Monolithic on 2007-02-23
I've been wanting to try out Linux for a while and my CD Burner been dead for the past 6 years so I couldn't download it. I was talking to a friend of mine today and he said he had a copy of Linux. So I have it in front of me now and I see that the newest version of Ubuntu is 6.1 and his version is 5.04. Having never used Linux before is there that big of a difference between 5.04 and 6.1? He also told me that I don't have to install it. I just pop it in the CD Drive and set the BIOS to boot from the CD and it will boot right up.

Thanks, and if I posted this question in the wrong forum, my bad. I just registered quickly and am in a hurry as I'm on my way to hockey.

---

### Post by taurus on 2007-02-23
Ask your friend if he can burn you something newer like Dapper or Edgy.  Otherwise, you can order a free copy of Dapper from ShipIt.

[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

---

### Post by SyvanX on 2007-02-23
It's a pretty big difference.  I have a laptop that won't boot from / read burned CDs anymore, so I did a floppy install of ubuntu 5.10, then I upgraded from there.

There are instructions for upgrading in the community help
[Upgrade Notes]("https://help.ubuntu.com/community/UpgradeNotes")

You can get an older version of ubuntu you can upgrade to the newest that way.  I think the installation is easier in the newer versions though, since they've moved to a live cd.

---

### Post by Monolithic on 2007-02-24
Upgrading is out of the question because the computer I'm installing it on is an old junker that was only set up for dial-up. So no ethernet card. Anyway, I just installed and everything went smooth and now I'm getting a GRUB Error 18 when I boot up. I reinstalled it again and I'm getting the same error. Gonna check it out on Google now.

---

### Post by nickoli_02 on 2007-02-24
I don't think it makes a huge difference if it's a slightly older version. 5.04 is still officially supported (though not for long, support cycle is 2 years so it expires on 7.04). 

Not so sure about te grub error... do a search in google for the error message

---

### Post by Monolithic on 2007-02-24
Ok, I Googled it and didn't understand what it meant. A guy in [this]("http://www.pbnation.com/showthread.php?t=1994243&page=16") thread on PBNation said I didn't partition it correctly or something. I'm the process of reinstalling now.

---

### Post by Monolithic on 2007-02-24
Ok, since my last post I've reinstalled 3 more times. :frown: I tried fiddling with all the partition options and I still get that GRUB Error 18.

My specs are

256MB RAM
20GB HD
Pentium 3 500MHz
MS 6163 Pro Motherboard

Does anyone have any idea what is going wrong? I'm dying to try Linux and my patience is running out.

---

### Post by SyvanX on 2007-02-24
It sounds like your kernel is on a partition that your BIOS won't boot from, because it is too large.  Try partitioning your HD to keep your /boot directory on a partition less than 8 GB, if you still get the error, drop to 512 MB.  

[http://wiki.linuxquestions.org/wiki/GRUB#Error_18](http://wiki.linuxquestions.org/wiki/GRUB#Error_18)

---

