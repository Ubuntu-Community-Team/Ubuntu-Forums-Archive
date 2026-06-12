---
title: "System backups - how do people manage this?"
date: 2008-05-27
forum: General Help
---

### Post by agamotto on 2008-05-27
I have been using various Ubuntu flavors for two years now, and I keep coming back to the same annoyance with all of them.  How do you manage to actually back up your computer?  I talk something more advanced than just backing up /home.  What I am seeking is a program/live cd that will backup partitions/drives to a USB 2.0 external unit without my having to be a bloody expert at the command line.

I have tried partimage, but the program is simply infuriating.  
There is g4l, but that doesn't seem to be able to use USB at anything near normal 2.0 speeds.  All I expect to have to do as the user is pick source, pick target, and have the machine do the rest, allowing me to do a total backup of the computer so that when a disaster happens, I can just restore from the other drive and move on with my life.

What software do you lot use to achieve this?  I don't care if it is commercial software, but it MUST be dead simple, and MUST not give me trouble with external USB drives.

---

### Post by tamoneya on 2008-05-27
have you looked at remastersys.  It allows you to make a custom ISO that will install ubuntu with all of your programs installed.  That way you dont have to do a days work of work installing all your favorites and removing all the extra stuff you dont need.

---

### Post by agamotto on 2008-05-27
I appreciate the suggestion, but you miss my point entirely.  I want to regularly back up my complete computer (ie, everything) onto an external USB hard drive.  This will eliminate me having to install anything.  Plug drive in, run program, restore stuff, go on with life.

:)

---

### Post by bwhite82 on 2008-05-27
There's flyback: [http://bernaz.wordpress.com/2008/01/19/flyback-a-time-machine-backup-utility-for-linux/](http://bernaz.wordpress.com/2008/01/19/flyback-a-time-machine-backup-utility-for-linux/)

---

### Post by bwhite82 on 2008-05-27
Also, TimeVault (beta):

[https://launchpad.net/timevault/+download](https://launchpad.net/timevault/+download)
[http://www.howtoforge.com/snapshot-backups-with-timevault-ubuntu-7.10](http://www.howtoforge.com/snapshot-backups-with-timevault-ubuntu-7.10)

---

### Post by PadreSol on 2008-05-27
Use dd to create a exact copy. man dd

---

### Post by tamoneya on 2008-05-27
> **agamotto said:**
> I appreciate the suggestion, but you miss my point entirely.  I want to regularly back up my complete computer (ie, everything) onto an external USB hard drive.  This will eliminate me having to install anything.  Plug drive in, run program, restore stuff, go on with life.

:)

In that case I recommend that you use sbackup.  It has a nice GUI and can easily be installed:```
sudo apt-get install sbackup
```

---

### Post by noynac on 2008-05-27
> **agamotto said:**
> ...What I am seeking is a program/live cd that will backup partitions/drives to a USB 2.0 external unit without my having to be a bloody expert at the command line....All I expect to have to do as the user is pick source, pick target, and have the machine do the rest, allowing me to do a total backup of the computer so that when a disaster happens, I can just restore from the other drive and move on with my life. What software do you lot use to achieve this?  I don't care if it is commercial software, but it MUST be dead simple, and MUST not give me trouble with external USB drives.

I use Acronis True Image, and it will do everything that you describe. If you have a Windows partition, you can run True Image from within Windows; otherwise you have to use a CD. Backing up to an external hard drive is drop-dead simple. I've restored individual partitions and the entire drive more times than I can count, and True Image has never failed me. It is commercial software, although the cost is only about $30.00.

Seagate and Maxtor have OEM versions of True Image 10 that are free for download, although you do have to have a Seagate or Maxtor drive in you machine. Someone told me that a Seagate or Maxtor external drive will pass the software's drive check, but I haven't confirmed this.

The Seagate software is called DiscWizard. You can download it from and read the manual at:

[http://www.seagate.com/ww/v/index.jsp?locale=en-US&name=DiscWizard&vgnextoid=d9fd4a3cdde5c010VgnVCM100000dd04090aRCRD](http://www.seagate.com/ww/v/index.jsp?locale=en-US&name=DiscWizard&vgnextoid=d9fd4a3cdde5c010VgnVCM100000dd04090aRCRD)

---

### Post by VMC on 2008-05-28
I agree with noynac! I use either Ghost or Acronis. Nothing else. I've tried the Linux versions and they are either way to slow or too confusing. It's worth it. Nothing else comes close.

---

### Post by agamotto on 2008-06-09
Hmmm ok.  I now have a few options to play with/test.  Thanks for all the advice, now I just need to set aside some time to play with the various suggestions.

---

