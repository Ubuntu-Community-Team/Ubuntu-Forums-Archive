---
title: "Ubuntu and solid state drives (SSD)"
date: 2014-03-14
forum: General Help
---

### Post by Twilk73 on 2014-03-14
I just purchased a thinkpad laptop and I plan to replace the HDD with a SSD. Is there anything I should know upfront about how linux plays with SSD's? Are there any negative side effects? Are there any recommended install methods or settings for SSD setups? The computer comes with 4gigs of RAM but I might end up upgrading that to 16gigs. I would like to be able to use sleep or hibernate so I does that mean swapa will be necessary?

As always thanks for the wonderful help this forum always gives. Iv loaded ubuntu before however my linux skills are limited so its probably best to treat me like an ignorant linux user.

---

### Post by HermanAB on 2014-03-14
Howdy,

Don't worry about it.  SSDs have little control processors and manage themselves.  It will last for many years, but nothing lasts forever, so do make backups as usual.

---

### Post by ajgreeny on 2014-03-14
Hibernate will need at least as much swap as you have ram; sleep or suspend does not work in the same way so does not really need that, though a small amount of swap, 2 - 4 GB, is nearly always recommended.

With an SSD for the OS itself you may find that there is little point in hibernating, as boot speed is likely to be very fast.

---

### Post by oldfred on 2014-03-14
Some are now saying that the new SSD have similar life to hard drives.

The new 14.04 will have trim script automatically.

With my older SSD a couple of years ago I did this:
 With SSD or Flash (trim does not work on flash) drives, Use ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sdb1
sudo tune2fs -o discard /dev/sdb1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
Make sure BIOS is in AHCI mode for trim to work.


 You normally want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.

I changed my trim from discard to a daily cron task.

 Trim in 14.04
[https://launchpad.net/ubuntu/+source/util-linux/2.20.1-5.1ubuntu11](https://launchpad.net/ubuntu/+source/util-linux/2.20.1-5.1ubuntu11)
HOWTO: Check If TRIM On Ext4 Is Enabled And Working On Ubuntu And Other Distributions
[http://sites.google.com/site/lightrush/random-1/checkiftrimonext4isenabledandworking](http://sites.google.com/site/lightrush/random-1/checkiftrimonext4isenabledandworking)
Ubuntu Aims To TRIM SSDs By Default
[http://www.phoronix.com/scan.php?page=news_item&px=MTUxOTY](http://www.phoronix.com/scan.php?page=news_item&px=MTUxOTY)
Trim as cron job, also must be ext4
[http://www.howtogeek.com/176978/](http://www.howtogeek.com/176978/)


 Shows both discard & fstrim methods for trim
[http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html](http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html)
gksu gedit /etc/cron.daily/trim
sudo chmod +x /etc/cron.daily/trim

---

### Post by Twilk73 on 2014-03-14
One last question. My plan of attack for installing ubuntu on the new SSD is simple but is it flawed? I was going to simply just swap the HDD with the SSD and use a USB stick to install the latest ubuntu OS. Is that going to work?

Thanks guys all usefull information. I wasnt aware of "trim" but thanks for the heads up. I didnt buy a SSD yet but it will be an option I am looking for now when making the purchase. I am not a total newb at linux but I am probably pretty close lol. Anyway the goal is to take full advantage of the SSD and lots of RAM. Its really only going to be a work computer. I am an auto mechanic with a need to tinker with everthing lol. So most of what I will be doing will involve web surfing but start up time will be very important because It will probably be turned off more than turned on threw out the

---

