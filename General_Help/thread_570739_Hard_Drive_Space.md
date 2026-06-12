---
title: "Hard Drive Space"
date: 2007-10-08
forum: General Help
---

### Post by Rival9999999999 on 2007-10-08
OK, I have my Ubuntu installe on a 60 GB Partition. I installed VMware server to run some windows applications, before i switched completely over. I rcently deleted the files and they are not in my trash. Disk manager is still showing that only 11 GB ae free out of the 60 GB.  I scanned the Hard drive with Filelight and found that, including the File system, I am only using 13.5 GB. That means i should have 46.5 GB free. What am I doing wrong? Where is all of my hard drive space?

---

### Post by Shazaam on 2007-10-08
Open a terminal and post the output here. 
```
sudo fdisk -l 
```
(small L)

P.S. You may still have the files in the /root/.trash directory.

---

### Post by thirddeep on 2007-10-08
Further more, you can quickly see how much space your using by :
```
sudo du -shx /home/USER
```

Or any directory actually :-)

Thd

---

### Post by Rival9999999999 on 2007-10-08
My old deleted Files were in \root\.trash. How come they did not show in my trash can? could they have been protected?

---

### Post by Rival9999999999 on 2007-10-08
I guess if they were protected, I would not have been able to delete them.

---

### Post by Nehvrook on 2007-10-08
As far as I know you shouldn't have been able to delete them without sudo. You aren't running as root are you?

---

### Post by Rival9999999999 on 2007-10-08
Yes. I did open nautilus through the terminal using sudo. So i guess I was deleting them as root and they were staying in the trash can of root. Thats why i did not see them in the trash can?

---

### Post by Nehvrook on 2007-10-08
Yeah. They were in roots trash can not yours if you origionally delted them as root. And they are proteced (Requiring admin rights) but if you sudo nautilus then all the files you touch will be as Administrator so it won't have challanged you looking at them or deleting them.

---

### Post by Shazaam on 2007-10-08
> **Rival9999999999 said:**
> Yes. I did open nautilus through the terminal using sudo. So i guess I was deleting them as root and they were staying in the trash can of root. Thats why i did not see them in the trash can?
Correct.

---

### Post by Rival9999999999 on 2007-10-08
Thanks Guys

---

