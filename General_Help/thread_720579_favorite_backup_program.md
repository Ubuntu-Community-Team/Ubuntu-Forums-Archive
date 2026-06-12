---
title: "favorite backup program"
date: 2008-03-10
forum: General Help
---

### Post by reeseslover531 on 2008-03-10
I was just wondering what your favorite backup program.  I am not sure which one I want to use and I am looking for some recommendations.  thanks!

---

### Post by cmnorton on 2008-03-10
tar piped into gzip

---

### Post by Het Irv on 2008-03-10
QuickStart 6.0 (see sig). It has a great gui, easy to use, and from the people that use it nothing but compliments.

---

### Post by amyst on 2008-03-10
I like QuickStart ... but how does tar.gz restore a broken file system exactly? Say somehow after messing up with a perfectly working ubuntu, the configuration files and data in /sys are missing or corrupted. Should I start the safemode and untar everything backed up with QuickStart back to all files in /? Would the o.s. be literally restored to the working ubuntu? 

Thanks in advance.

---

### Post by Het Irv on 2008-03-10
Use the Quick Start program to restore the tar files.  QuickStart doesn't have to be installed, just keep a copy of the program with your backups and run it as needed.  It will untar and replace all of your current files with the backed up ones.  That should put everything back to the way it was when you started.  Post in the QuickStart Thread if you have any more questions, I don't know exactly how it works, but mdplow is the developer and he can answer the questions best.

---

### Post by Kerry_W on 2008-03-10
I find Acronis True Image does a great job
[http://www.acronis.com/homecomputing/products/trueimage/](http://www.acronis.com/homecomputing/products/trueimage/)

Kerry

---

### Post by Therion on 2008-03-10
> **Het Irv said:**
> QuickStart 6.0 (see sig). It has a great gui, easy to use, and from the people that use it nothing but compliments.
Seconded on all points.  Greatest little app since Envy.

---

### Post by ajgreeny on 2008-03-10
I simply backup my home with grsync to an external usb hard drive, along with the contents of /var/cache/apt/archives.  I always set synaptic (apt-get) to keep all files in the archive as it means if I need to reinstall, I don't need to download anything new as it's all in the archive from the time of installation in the first place.  Saves a huge amount of time and network downloads, and makes sure I have a good clean new system, not just a copy of what I had before.  Let's face it, you have to keep backups of home, anyway, and that is a great deal bigger than /, or it is in my case.  It is so quick to reinstall the system, why bother to copy it all?

---

### Post by Oldsoldier2003 on 2008-03-10
> **cmnorton said:**
> tar piped into gzip

+1
simple, elegant, time tested

---

### Post by Rocket2DMn on 2008-03-10
I use a program called Simple Backup, it is available in the repos as "sbackup".  It is built of rsync and can do incremental backups, including to remote locations.  It uses gzip compression as well (annoying when backing up large amounts of already compressed multimedia, but it is convenient once you get past the compression time).

---

### Post by reeseslover531 on 2008-03-11
> **Kerry_W said:**
> I find Acronis True Image does a great job
[http://www.acronis.com/homecomputing/products/trueimage/](http://www.acronis.com/homecomputing/products/trueimage/)

Kerry

does acronis work from within linux? I have used acronis for years on windows boxes

---

### Post by Kerry_W on 2008-03-11
> **reeseslover531 said:**
> does acronis work from within linux? I have used acronis for years on windows boxes

I just use the Acronis Boot CD to make my backup images.
there is [Acronis True Image Echo Server for Linux](http://www.acronis.com/enterprise/products/ATISLin/) if you want to run from within linux.

Kerry

---

### Post by dje on 2008-04-14
You could take a look at my new project linbaku, it creates complete backups of your ubuntu installation into tar archives, for more information click the blue linbaku link in my signature

hope that helps,
dje

---

### Post by mdpalow on 2008-06-05
> **Therion said:**
> Seconded on all points.  Greatest little app since Envy.

Wow! That's one heck of a compliment. Thanks!

---

