---
title: "Ubuntu fails to boot"
date: 2007-02-23
forum: General Help
---

### Post by Mozork on 2007-02-23
I am using the newest Ubuntu Edgy Distribution (or so I guess).
What happened:
I manually installed glib-2.0 and after that atk (my internet connection is a bit unstable at the moment;) ) and while running configure it told me, that I had two installations of glib, so the installation would not work, and it suggested to remove the lower version, which I did manually (again) by searching for all filenames containing glib-2.0, recognized, that all of them existed twice, one time with a older date and one time with the date of today (now actually yesterday), so I deleted all the old ones, ran the configure of atk again, and almost the same error occured, although it now didn't know the version of eighter installed glib-2.0 package anymore. I then also experienced some anomalies with my desktop, such as, I wasn' able to untar a tarball through nautilus, or nautilus would not open through my deskbar, nor did the terminal. So I decided to reboot in recovery mode, what went fine, and I rebooted again and the reboot stopped about half the way. So I ran recovery mode again, and rebooted again, and it almost booted (about 95%) and then stopped. So I figured it had something to do with my glib installation. I reinstalled it (in recovery mode) and tried to get atk to compile, which it eventually did (I had to set some LD_* variable - i dont quite remember which one) and i thought that maybe the problem now would be solved. I guessed wrong. ;) Same error, every time I tried...

I would of course be happy to get my ubuntu to work again (I need vour help for that) but if not possible it would actually be enough if i could somehow save my emails, addressbook (thunderbird) and my feeds (blogbridge) the rest is eighter not important, or I know how to recover it...

---

### Post by cronholio on 2007-02-23
In case you cannot recover it, boot from an Edgy or Knoppix Live CD and mount your Ubuntu partition, so you can copy your home folder to an USB drive. You can restore your home folder after a reinstall.

---

### Post by Mozork on 2007-02-23
Thanks a lot for answering. :D
Is that a installing option? Or do I have to do something 'special' to have my homefolder back and kicking? And more importantly does that save my mails?

---

### Post by cronholio on 2007-02-23
If you use Evolution, it will save your mails. To mount the partition, boot from a Live CD, open a terminal and type:
```
sudo mkdir /mnt/hd
mount /dev/hda1 /mnt/hd
```
Replace hda1 with whatever your Ubuntu partition is. Now use Nautilus to navigate to /mnt/hd/home and copy your home folder (copy the whole thing, don't enter it and mark all files, or hidden folders won't be copied). Your emails should be in /mnt/hd/home/yourusername/.evolution/mail but copy everything to a USB drive to be sure. After reinstallation you can just copy your home folder back to its original position and everything will be there.

---

