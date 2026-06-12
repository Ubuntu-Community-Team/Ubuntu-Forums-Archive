---
title: "Run bash script on USB Flash Drive Mount?"
date: 2008-01-16
forum: General Help
---

### Post by xelapond on 2008-01-16
I am trying to make a script to automatically back up my flash drive when I plug it in.  Right now I have the bash script working, but I have click on it every time I plug my flash drive in.  Is there a way to make it autorun when I plug the drive in?

Also, Im using KDE4 if that makes any difference.

Thanks, 

Alex

---

### Post by Keith Hedger on 2008-01-16
I dont know about kde but in gnome you have to have an executable file in the root of your drive called "autorun" and have autorun selected in the "removable drives" prefs I would asume that kde uses a similar system

---

### Post by kpkeerthi on 2008-01-16
Check this out [http://ubuntuforums.org/showthread.php?t=502864](http://ubuntuforums.org/showthread.php?t=502864). Someone has already posted this tip in Tutorials section.

---

### Post by xelapond on 2008-01-16
Thanks, I got that working, 

What It does when it gets plugged in is cp everything to a backup directory on my computer.

I have a 4 gig drive, so this takes awhile,

Would it corrupt my data if I editied and saved  file while it was copying?

Thanks, 

Alex

---

### Post by Keith Hedger on 2008-01-16
Almost certainly!

---

### Post by Sir.Babau on 2008-02-10
> **xelapond said:**
> Thanks, I got that working, 

What It does when it gets plugged in is cp everything to a backup directory on my computer.

I have a 4 gig drive, so this takes awhile,

Would it corrupt my data if I editied and saved  file while it was copying?

Thanks, 

Alex

Try using rsync rather than cp. Since a lot of your data's probably the same from one day to the next rsync will likely speed things up and let you get to work faster.

---

