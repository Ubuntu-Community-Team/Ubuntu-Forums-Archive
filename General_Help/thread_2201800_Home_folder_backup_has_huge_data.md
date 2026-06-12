---
title: "Home folder backup has huge data"
date: 2014-01-26
forum: General Help
---

### Post by Gnusboy on 2014-01-26
I'm trying to understand a backup problem with Deja-Dup.
I want to upgrade from 12.04 to the latest version. I was running duplicity with weekly backups to a local folder, but stopped because it was using far too many resources and slwed my whole system. Today, I wanted to reset it, but when I checked the properties of my home file, it shows the file size as 60 GB!

**15,728 items, totalling 60.4 GB**

 It also shows that my 640GB HDD is down to 211 GB.

 I don't have that much data on the system.
I looked at my other Deja Dup backups which shows
 
duplicity-full.20130109T052521Z.vol52.difftar.gz
Gzip archive (application/x-gzip)
52.4 MB (52,426,588 bytes

So ... I can't backup 60 GB to my Ubuntu 1 cloud space that shows I have used about 1.5 GB of the 5 GB allowed.

Can anyone make sense of all this and let me know what is what?

Thanks

---

### Post by jeanjd63 on 2014-01-26
Hello

To find where are bigs files on /home/$USER folder you can do :
*for hidden files and directories*
**du -sh /home/$USER/.??*  |  sort  -rh**  
*for normal files and directories*
**du -sh /home/$USER/*  |  sort  -rh**

---

