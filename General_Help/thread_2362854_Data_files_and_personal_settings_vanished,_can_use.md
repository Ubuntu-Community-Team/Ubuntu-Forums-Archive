---
title: "Data files and personal settings vanished, can user profile be corrupt Lubuntu"
date: 2017-06-02
forum: General Help
---

### Post by ecapoe on 2017-06-02
Hello,
I use Lubuntu 16.04 and after an apparently minor crash (trouble with saving files in Libre Office and Rstudio, so I closed and rebooted), I lost access to all my files, and, strangely enough, to all my personnal settings. The desktop changed and is back to default, all Firefox bookmarks vanished. 
Since Firefox settings are not stored as my data file, I wonder if it can be a problem of user profile.
It seems I get logged as guest !
How can I solve that ?
Regards,
André

---

### Post by TheFu on 2017-06-02
A failing HDD might not be able to write to the disk and cause a crash.
So, it the HDD ok?  What do the logs say? What about SMART data.

Do you have backups? If not, get some, quick.

After that, create a new userid and see if the problem goes away or not.

---

### Post by ecapoe on 2017-06-03
Hello,
Thanks for answer.
Drive seems now ok. It runs perfectly but my session looks brand new, as if i were logged as guest.
Can you give me instruction to access to log ? Smart data ?? Sorry i am not specialist.
Regards, andre

---

### Post by ecapoe on 2017-06-03
Hi again,
I can do the smartctl from smartmontools (running from live cd).
But result is quite long. What is needed ?

---

### Post by leunam12 on 2017-06-03
Just open the DISKS utility and see if there are any errors, reallocated sectors, sector pending reallocation, uncorrectable sector count, read error rate or spin-up retry errors (look at the raw values), they should be zero.

---

### Post by oldfred on 2017-06-03
If logged in as different user, your files & user configurations should still be in your old user.
If you in Nautilus go to Computer and drill down to home, do you have more than one user shown? And it show have old user.

Or:
fred@Z170N:~$ cd /home
fred@Z170N:/home$ ls
fred

I show only user fred.

---

