---
title: "Help! 19G hard-drive is full with only 4.5 Gb of files: disk error or rootkit?"
date: 2007-04-04
forum: General Help
---

### Post by andy gee on 2007-04-04
:frown: 

I went to log onto to my Edgy desktop tonight. I had been using it today and had left it running. As soon as I attempted to run something - can't remember what - the system refused to run, indicating that I had no spare room on the drive.

This was confusing since I have /home on a separate 200G hard drive. I rebooted, but I couldn't log into the system - again, the error given indicated that the disk was full. I then booted into Zenwalk (on yet another hard drive) mounted up the Ubuntu disk, and had a look. When I used Thunar to check the size of the listed files, it gave me a total size of 4.5 Gb for all folders listed (apart from /home).  When I use ```
df
```, the result is: > Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdc3              8728544   2358696   5926456  29% /
/dev/sdc1            166603736 106509548  58401580  65% /home
/dev/sda1             19542568  11208288   8334280  58% /mnt/windows
/dev/sdd1            438419764 327811524  88337736  79% /mnt/usb
/dev/sdd2             42952880  13855776  29097104  33% /mnt/usb1
/dev/sdb1             18793496  18783520         0 100% /mnt/ubuntu

where sdb1 is my Edgy installation, sdc1 is my group /home (used for Edgy, Feisty and Zenwalk). So this is showing 18 Gb used! :confused: 

I then thought I might have a rootkit, so I installed the wonderful 'chkrootkit' which found no infections on that hard drive or any other. ](*,) 

Do I have a crashed hard drive? If so, why can I still access it? It seems to work ok, only it doesn't have any room. Any suggestions on how to go from here? I know we'll have full Feisty soon, but I'd rather upgrade than get a new hard disc, reinstall and then get everything just the way I like it all over again.

I would really appreciate some help at this point. I like Zenwalk, it's quick but sometimes it's hard work using slackware, and for a n00b like me, I miss Ubuntu!:cry:

---

### Post by silverglade00 on 2007-04-04
Just a quick thought, you might want to check your Ubuntu root's trash. Make sure it isn't full of stuff. I'm not sure if it counts stuff in there or not.

---

### Post by andy gee on 2007-04-04
Thanks for the idea silverglade00. I looked around in Ubuntu's /root, but strangely enough there was no /.Trash folder there at all! I thought this was odd, so I used Thunar as root this time and checked 'properties' . Result: > Size: 711 items, totaling 14.5 GB. Huh!
Anyway, turns out that /root's  /.Trash is in (keep for future reference): /root/.local/share/.Trash/files

Thanks heaps for your feedback - would never have thought to use Thunar as root without your suggestion, and of course if you don't use it as root, it wont give you the file size of any file you don't have permissions to check. Owe you big favour.

And now, off to bed (at last). Work starts in a few hours.....

---

### Post by silverglade00 on 2007-04-04
Awesome! I'm glad it helped. Would you believe I've only been running Ubuntu for about a week? I've been using PCLinuxOS for about a year, though, and a lot of the stuff I learned with that transfers to Ubuntu.

As for the big favor, how about you just share your install CD with someone who could use it and we call it even? :)

---

### Post by bashologist on 2007-04-04
Using the "-h" option makes df more readable:
[QUOTE=man df]       -h, --human-readable
              print sizes in human readable format (e.g., 1K 234M 2G)[/QUOTE]
Using du is a good way to see where your hdd space is:
```
sudo du -ch --max-depth=0 /*
```
To see the disk usage of your home folder:
```
sudo du -ch --max-depth=0 ~
```

---

### Post by andy gee on 2007-04-06
Nice work bashologist - the 'du -ch' command is nice and useful, and now resides in my "nice and useful commands" file. Seems slow though.

silverglade00 - isn't Ubuntu wonderful like that? I've gone from Windows in November 06 to Ubuntu in December 06, and generally if I break something I can fix it. I even changed my /home folder to a separate hard drive - if you haven't tried it, it's a very good thing to do if you use multiple distros.

As for sharing the install cds around - I tried that for a while, but I don't have enough charisma to be a guru, and everyone stays with windows. So, instead I've started a charity called "LibrePC". I get donated computers, install Xubuntu, add some ahndy software, make sure there are nice shortcuts and beginner information and give them away to people who can't afford new pcs - senior citizens, economically disadvantaged families etc.

These computers won't run Windows XP - they're too old, and Windows 2000 sucks compared to Xubuntu, so I'm hoping these folk will stay with Linux, and in some cases grow up with it.

If you know anyone in Sydney (Australia) who can help, point them my way! Thanks for sitting through my shameless and off-topic plug (*heh heh*). Enjoy Ubuntu!

---

