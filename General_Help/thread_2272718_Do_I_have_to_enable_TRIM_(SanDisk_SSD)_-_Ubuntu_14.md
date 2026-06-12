---
title: "Do I have to enable TRIM? (SanDisk SSD) - Ubuntu 14.04"
date: 2015-04-08
forum: General Help
---

### Post by user1397 on 2015-04-08
Just replaced my internal laptop hard drive with a SanDisk SSD.  Reinstalled ubuntu 14.04.2 and everything works.  Was reading up on TRIM and ubuntu, seems like the only brands of SSDs that enable TRIM by default are Samsung and Intel.

Should I set it up as a cron job?  And if so what's the best way to do that?

Thanks.

---

### Post by oldfred on 2015-04-08
Make sure BIOS is in AHCI mode for trim to work.


 Trim as cron job, also must be ext4
[http://www.howtogeek.com/176978/](http://www.howtogeek.com/176978/)
Disable 14.04 auto trim, if you add your own

I preferred this as then I also have a log file (but then have to houseclean log)

 Shows both discard & fstrim methods for trim
[http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html](http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html)
gksu gedit /etc/cron.daily/trimSSD
sudo chmod +x /etc/cron.daily/trimSSD

  ```
#!/bin/sh
# trimSSD

LOG=/var/log/trimSSD.log
echo "* $(date -R) *" >> $LOG
fstrim -v / >> $LOG
# fstrim -v /home >> $LOG

```


I do not have separate /home so I have line  but commented it out with #.

---

### Post by user1397 on 2015-04-08
Thanks oldfred, I'm gonna go with the fstrim method from the webupd8 link.  I verified my BIOS is in AHCI mode, and I don't have a separate /home partition so I don't need to add that extra line.

How do I disable the default autotrim though? I don't think that's covered by the article.

---

### Post by efflandt on 2015-04-08
This link will give you some suggestions. I used that when setting up 14.04.1 (with grub) on 512 GB Crucial mSATA SSD card in my laptop (sdb). Although, for #5 I forget how much I left unallocated, because I figured a larger drive did not need as much %. My laptop has 8 GB RAM and I do not hibernate, so I currently have no swap. But I had 13.10 on sda4 of my hard drive, so I may use some of that for swap.
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

---

### Post by kerry_s on 2015-04-08
if you look in /etc/cron*  fstrim is set to run weekly on all drives that support it.
so you really don't need to do nothing.

did you leave some free space, 7% of the drive, it's suppose to increase performance ?

---

### Post by sammiev on 2015-04-08
> **kerry_s said:**
> if you look in /etc/cron*  fstrim is set to run weekly on all drives that support it.
so you really don't need to do nothing.

did you leave some free space, 7% of the drive, it's suppose to increase performance ?

Hi kerry, can you recommend the format that should be used for the free space?

Thanks

---

### Post by kerry_s on 2015-04-08
> **sammiev said:**
> Hi kerry, can you recommend the format that should be used for the free space?

Thanks

none, it's suppose to be unallocated/deleted

---

### Post by sammiev on 2015-04-08
> **kerry_s said:**
> none, it's suppose to be unallocated/deleted

+1 I was looking at the attachment you posted and mine does say unallocated, but I see yours say free space.

Thanks

I see the difference now, I'm using gparted. :)

---

### Post by kerry_s on 2015-04-08
yeah, it should be unallocted in gparted

---

### Post by user1397 on 2015-04-09
So I created the cron.daily file.  Should I delete the default weekly cron file?  Or will it not interfere with the daily one? I'm talking about the file: /etc/cron.weekly/fstrim (as opposed to /etc/cron.daily/trim)

Also, I did not allocate any free space on my SSD at the end of the last partition, I did not know that was needed.  Will it really make a huge difference?  I'm dual-booting with windows 8 so I had to install windows first and then install ubuntu, and windows formats the hard drive in a specific way and uses all of the space (the last 16GB or so is a recovery partition.) so I wouldn't even know how this is possible without getting rid of windows (which I'd rather keep for now).

---

### Post by oldfred on 2015-04-09
Always best to have a full backup of Windows.
And the recovery partition should have a way to create a set of recovery DVD or a flash drive. Once you create that, you can delete the recovery partition.

If you have a good backup of Windows, the only reason for the recovery is to restore to as purchased. Which you may need if you later sell system or if your backup does not work. But then you have to reinstall all updates since you bought system.

---

### Post by user1397 on 2015-04-10
> **oldfred said:**
> Always best to have a full backup of Windows.
And the recovery partition should have a way to create a set of recovery DVD or a flash drive. Once you create that, you can delete the recovery partition.

If you have a good backup of Windows, the only reason for the recovery is to restore to as purchased. Which you may need if you later sell system or if your backup does not work. But then you have to reinstall all updates since you bought system.
Gotcha.  I actually do have a good backup of windows on one of my flash drives so I guess I don't need the recovery partition, but what I want to know is if leaving unallocated space is still that important (now in 2015) and how much exactly should I leave?  I have a 128GB SSD

Also, like I mentioned before, since I have the trim command set to daily, should I remove the weekly cron job file?  Or does it not matter?

---

### Post by Bucky Ball on 2015-04-10
I've heard everything from leaving 5% free to leaving 20% free. Who knows with newer drives? Supposed to extend the functional life of the device from what I've read. I have a fifth unallocated on my 128Gb SSD, but thinking of getting rid of that, so curious to know the 'real' story myself. :-k

---

### Post by user1397 on 2015-04-10
> **Bucky Ball said:**
> I've heard everything from leaving 5% free to leaving 20% free. Who knows with newer drives? Supposed to extend the functional life of the device from what I've read. I have a fifth unallocated on my 128Gb SSD, but thinking of getting rid of that, so curious to know the 'real' story myself. :-k
A fifth? Seems like a lot of valuable space unused for a 128GB ssd!!! :(  I hope I don't need to allocate that much...

On [this]("https://sites.google.com/site/easylinuxtipsproject/ssd") website it says this: "I only mention it as option and not as advice, because it's unclear whether this is still useful nowadays" about allocating free space. Hmm..

---

### Post by QIII on 2015-04-10
I have read a number of articles of late indicating that over-provisioning is no longer an issue with current SSD technology and wear-leveling algorithms.   Much like the "swap = 2x RAM" rule, it seems no longer to apply but the notion persists.

Unfortunately, I don't have any ready citations at hand.

---

