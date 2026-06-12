---
title: "NTFS-3g &amp; Special Characters"
date: 2007-04-30
forum: General Help
---

### Post by deevus on 2007-04-30
I have my music on an NTFS drive so I have it mounted using NTFS-3g, but I noticed that it doesn't seem to see artists folders with special characters such as Bjork. 

I noticed this because I used Amarok to organise my collection, and then when I was browsing in Windows, I saw that there were several artist folders not organised - Ones with special chars.

Is this just a limitation of NTFS-3g or is there a workaround? If not Ill just change the special characters to normal ones.

---

### Post by Aarohi on 2007-05-01
I have the exact same problem.

Anyone?

---

### Post by PrinceArithon on 2007-05-01
It sounds more like something that has to do with another part of your set up and not the program.  Have you installed the proper fonts for the special characters??

---

### Post by Aarohi on 2007-05-06
All the files and folders with special characters are shown on an ext3 partition.. but they can't be copied to ntfs-3g partitions because they have special characters.

---

### Post by mseewald on 2007-05-06
Hi,

I believe I had the same problem. I activated write support for NTFS with ntfs-3g and could not see special characters (German Umlaute). Interestingly, it helped to just umount and mount the partition. After doing so, files and folders with special characters reappeared. Bizarre, not?

What really helped: To specify locale=de_DE.UTF-8 instead of nls=utf8 in /etc/fstab

Now, fstab reads:
/dev/sda6 /media/windoze_e ntfs-3g defaults,locale=de_DE.UTF-8,umask=007,gid=46 0 1

For Ubuntu developers: Please use the "locale" setting for ntfs-3g instead of "nls".

HTH,
Michael

---

### Post by Aarohi on 2007-05-14
\\:D/ 

Thanks a lot dude.

---

