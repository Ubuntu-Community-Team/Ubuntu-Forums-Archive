---
title: "Do I have to enable trim in Xubuntu 15.04?"
date: 2015-05-24
forum: General Help
---

### Post by lendoz27 on 2015-05-24
I see there are files in /etc for daily, hourly, weekly, monthly, etc.
So how do I make sure that trim is enabled for my ssd?

Do I have to modify one of the files?
Are they all set to "off" by default?

I have everything on one partition, except swap.

What's the best way to approach this?

Thanks!
Len

---

### Post by v3.xx on 2015-05-24
One day I will get a ssd and find out about these things :) Till then, I can just point in the direction.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=trim+ssd&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=trim+ssd&sa=Search&cof=FORID:9)

---

### Post by oldfred on 2015-05-24
I had an older small SSD and enabled my own script with logging, so I knew it worked.

The new automatic script does not have logs and only runs weekly. It also does some checks on brands and does not run on all brands. Not sure how to check if it ran, but you can just run the trim from a command line soon after it runs and see it only a few updates are needed.

I turned off the Ubuntu version and put back the version I added with old SSD on my new SSD.
You do have to have BIOS set to AHCI mode for trim to work. Most new systems have drives set for that.

       Shows both discard & fstrim methods for trim
[http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html](http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html)

This is what I did and I turned off the Ubuntu one in cron weekly:
gksu gedit /etc/cron.daily/trimSSD
sudo chmod +x /etc/cron.daily/trimSSD

   #!/bin/sh
# trimSSD
LOG=/var/log/trim.log
echo "*** $(date -R) ***" >> $LOG
fstrim -v / >> $LOG
# fstrim -v /home >> $LOG

   
Manuallly run command
fred@fred-Precise:~$ sudo fstrim -v /
/: 23267893248 bytes were trimmed

---

