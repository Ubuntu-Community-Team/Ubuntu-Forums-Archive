---
title: "can't boot"
date: 2006-07-19
forum: General Help
---

### Post by metricben on 2006-07-19
i tried to install windoze onto 2nd harddrive, with ubuntu drive disconnected, but have now formatted over it with ext3 for backup.

anyway, my ubuntu drive is master and backup slave and whenever i turn on my pc, it says "boot from cd:".  the way i bot is to use the dapper drake cd and "boot from first hard drive".  windoze probably erased over the mbr or something, but as a relatively new linux user, how to i setup lilo or grub again.  i uninstalled and reinstalled grub.

thanks
ben

---

### Post by steve.horsley on 2006-07-19
Is the CD the "alternate" installer CD? If so, you can choose rescue mode and it can give you a root prompt on the installed system. From there, use the command **grub-install /dev/hd0** which should re-install grub for you.

---

### Post by metricben on 2006-07-20
sorry i didn't make it clear: i can boot using the "boot from first hard drive" feature on the standard cd

```
ben@benspc:~$ grub-install /dev/hd0
/dev/hd0: Not found or not a block device.

```

so... i dont have a hard drive, which is strange, because i spent so much time opening my case adding 1 and creconfiguring the jumpers. lol

ben

(oh yeah, i did this from inside my running os, should i do it in livecd mode)

---

