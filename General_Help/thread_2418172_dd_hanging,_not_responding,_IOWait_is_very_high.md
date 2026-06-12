---
title: "dd hanging, not responding, IOWait is very high"
date: 2019-05-02
forum: General Help
---

### Post by timothylegg on 2019-05-02
Ubuntu 16.04, Lenovo T440p, 2x Seagate BUP Slim RD USB Hard disks

Hello,

I'm duplicating a 2TB USB hard disk as a backup ahead of a two month travel.  I've used this technique for years:

#  pv /dev/sdb | dd of=/dev/sdc

Once complete, I take an MD5SUM to assure myself the volumes are correct.

Yesterday, I woke up to find it was hung at 520GB, with a transfer rate of 19KiB/s and the ETA timer frozen.  CTRL-C, couldn't kill it.  It didn't occur to me that kill -9 might kill it as I wasn't coffee'd up yet.  I instead told the laptop to shutdown.  It didn't.  I had to force shutdown the laptop.

Today, I tried again and this time it's at 1.17TiB and hung frozen at 19KiB/s with exactly 4:49:50 remaining.  Kill -USR1 doesn't wake it up.  Other terminal windows work fine and I ran top.  No processes out of control, but the Wait parameter is steady between 70-90%.  Forgot using a web browser.  I was going to cut-paste some info, but typing lags by approximately 80-90 seconds before appearing on the screen.  However, the Terminal works just fine.  Nothing is logged in dmesg.

I have not tampered with anything and I have an operable term window.  I want to understand where the problem is.  These tools are as old as I am and cannot accept that there is a bug in them.  Where do I look to find out where the issue is?  This is not a code red emergency, but I'd rather not leave these disks powered for days at a time.

Thanks!

Tim

---

### Post by TheFu on 2019-05-02
When dd has issues, it doesn't fail gracefully.  Use **ddrescue** instead.  There might be a single, bad, sector, preventing dd from continuing. It might be unused.

For making an image backup, using something like fsarchiver might be a better choice since it compresses stuff and if it understands the file system, only the actually used parts are included.  Also, it can be restored to a smaller disk/partition unlike most other image-based tools.

OTOH, if you have great backups already, using real backup tools, then those should be preferred over any image-based solution.  This is the method I use. Backups take 2-5 minutes daily and restores to a working system take just 30-45min including a base install of the OS from the current ISO file. Anyways, that is probably an option for when you return. Getting everything into this backup method, but nothing extra, takes a few attempts. Took me about 5 failures before I got it correct on the first system. That was about 10 yrs ago.  Used it last week to move a system to new hardware. Used it 3 months ago to move to a new laptop. About once a year, I do something really stupid and need to restore the entire system during an approved maintenance period.

There is something about images which make people sleep better. The trade-off is backup downtime and huge storage requirements when compared to the alternatives. Once you master grub-install and update-grub with having the files in the correct places, all the boot "magic" doesn't matter anymore. It is very easy to get a system restored to working from efficient non-image backups.

---

