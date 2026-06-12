---
title: "File sharing between ubuntu and xp"
date: 2007-03-05
forum: General Help
---

### Post by dreadh3ad on 2007-03-05
Currently I am dual booting Ubuntu and windows xp.  I have two internal Hd's 40 and 250 gig 
i would like to set up a file system on the 250 that will allow me to share mp3s, movies and other data.  Can somebody point me in the right direction?

---

### Post by Icarosaurus on 2007-03-05
The best solution should be a Fat32 partition.
But you should remember that it cannot handle single files bigger than 4GB. So if you plan to use such huge files (such as iso images of DVDs) you should use ntfs.
Actually you can read-write on ntfs using ntfs-3g but I experienced some problem in moving big files (such as divx movies).
So I'll opt for fat32 (files bigger than 4GB are not very common)
Regards. :)

---

### Post by finer recliner on 2007-03-05
ntfs-3g is still beta. use at your own risk.

---

### Post by Ric95 on 2007-03-05
I thought Windoz could read/write to ext2 ?
That would be better.

---

### Post by ffxr on 2007-03-05
ntfs-3g is now out of beta..

i recommend getting xp to read ext3 tho... [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

---

### Post by rsambuca on 2007-03-05
> **finer recliner said:**
> ntfs-3g is still beta. use at your own risk.

Actually, version 1 stable has been released.  No longer beta!

---

### Post by kpkeerthi on 2007-03-05
Format the 250 GB partition to ext3. Ubuntu reads/writes to it. Install [http://www.fs-driver.org/](http://www.fs-driver.org/) in your XP and it can read/to from/to the partition as well. Simple. I use it. No problems whatsoever.

---

### Post by strabes on 2007-03-05
You have three options. They are fat32, ntfs, and ext3. The downside to fat32 is that it can't handle file sizes bigger than 4gb. If you have files bigger than 4gb, then you can use NTFS or ext3. If you choose ntfs, you can install ntfs-3g in linux to add read/write support to linux. If you choose ext3, you can install the driver from [www.fs-driver.org](www.fs-driver.org) in windows to add ext3 read/write support. This is what I do and I haven't experienced any problems other than that the partition has to be unmounted cleanly in linux before you can read or write to it in windows.

Hope this helps.

---

### Post by konungursvia on 2007-03-05
I'd partition the 250 GB into two parts, one with 150 GB Fat32, and one with 100 GB NTFS, accesible with the new ntfs-3g, which is working all right for the most part. You can also download a windows shareware exe to split  large movies into 3 GB parts.

---

### Post by konungursvia on 2007-03-05
> **Ric95 said:**
> I thought Windoz could read/write to ext2 ?
That would be better.

It can, but you have to install a third party driver for that.

---

### Post by finer recliner on 2007-03-05
sorry, i was unaware of the stable version being released :oops: 

ill have to go check it out when i get home!

---

### Post by dreadh3ad on 2007-03-05
Thanks for all the support.  I havent made my final decision but now i have another question.  
I need to reformat and start from scratch, whats the best way to do this?

---

### Post by Hallvor on 2007-03-06
I use a shared NTFS-drive and the ntfs-3g driver. Don`t have any problems with it - even with large files. (High cpu was a problem when the driver was in beta, but on average, I now use something like 2-5% cpu on my amd 2500+ xp. And that`s not just the driver, but Ubuntu.) I didn`t want to reformat the drive because I was lazy and had close to 100 gb of data on it. But as long as it works, I`m happy.

---

### Post by anaconda on 2007-03-06
If you use windows more than linux go with the NTFS route
And 
If you use linux more than windows go with ext3 route

Simple as that..

and I wouldn't recommend fat32 because of the annoying 4GB limit and because it hasn't got rights.. I mean if you have a .txt file in fat32 partition and you doubleclick it in ubuntu it will ask "Do you want to run this file or display the contents of this file..."  annoying.  This is because in fat32 all files have "rwx"- rights so they are all marked as executables..

---

