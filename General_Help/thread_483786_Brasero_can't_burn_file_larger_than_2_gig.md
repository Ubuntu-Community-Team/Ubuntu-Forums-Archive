---
title: "Brasero can't burn file larger than 2 gig?"
date: 2007-06-25
forum: General Help
---

### Post by zodmaner on 2007-06-25
Hello, I try burning a DVD using Brasero and it refuses to burn, giving error saying one of the file is larger than 2 gig and that Brasero can't read that file. (The file was about 2.2-2.4 gig)

I was able to burn the file in K3b, so is this problem with Brasero it self or am I missing something? Does anybody else have this problem? Thanks in advance. :)

---

### Post by pickarooney on 2007-06-25
2GB is, I think, the file-size limit in FAT32 (or was that FAT16, with 4GB the limit on FAT32?). Is your file on a shared Windows partition by any chance?

If not, have a look in the options (I'm not familiar with Brasero/Bonfire) and see if you can 
set ISO level to level 3 somewhere and try burning again.

---

### Post by zodmaner on 2007-06-27
My file is on a ext3 partition. I've look at Brasero options and found no option to set ISO level or something similar at all.

---

### Post by dabl on 2007-06-27
I was backing up my music to DVDs last night, using Brasero, and noticed some real weirdness regarding its calculation of "full".  It would show that I had selected 4.1G of files, for a 4.4G blank DVD, and then when I went to burn it would error out with "files exceed DVD space" or some such nonsense.  I had to cut the selected project size down to around 3.3G (according to Brasero), and then it would burn, and lo and behold the DVD had 4.2G of files on it.  So I'm saying Brasero can't count very well ....  :rolleyes:

---

### Post by kelvin spratt on 2007-06-27
ive never had a problem with Brasero only K3B on my system but all my files are on NTFS. but you do get problems with cheap DVDs so that could be your problems, i only use Verbatim and overburn by 200mb thats 4555 instead of 4335 with no problems also check, your firmware for your writer but be carefull to follow the instuctions.

---

