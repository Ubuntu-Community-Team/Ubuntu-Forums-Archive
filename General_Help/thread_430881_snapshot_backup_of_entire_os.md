---
title: "snapshot backup of entire o/s"
date: 2007-05-02
forum: General Help
---

### Post by Bashed on 2007-05-02
I am using desktop version of Ubuntu FF 7.0.4

How do I do a full o/s snapshot backup to CD or DVD? I could not find this feature at all.

---

### Post by kolinab on 2007-05-02
TJ,

I would explore the following avenues: (really one solution) I have used Partimage successfully to do what you are describing. I no longer back up my entire OS however, I only back up my /home.

[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)
[http://ubuntuforums.org/showthread.php?t=287522&highlight=backup](http://ubuntuforums.org/showthread.php?t=287522&highlight=backup)
[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

It's easier than you think, try it!

Kolin

---

### Post by Bashed on 2007-05-02
Thanks. Now here's a question for you :)

The main sole purpose I wanted to do a full o/s snapshot style backup is to retain all my custom tweaks, modifications I've already done (countless hours) to Ubuntu.  If I solely backed up my entire /home directory say to my USB drive, how would I restore this SAFELY should I reload my entire hard drive with Ubuntu 7 (or any major new release in future), yet without losing all my modifications including font tweaks, themes, gdm setup, splash screen setup, etc?

---

### Post by kolinab on 2007-05-02
Your question is good - you're right, if you just back up /home then all those countless hours of tweaking and diddling and installing are not backed up. I guess a few things would be preserved, but mostly just data, and not the 'state of the system.'

Your best bet if you want to safely preserve all those tweaks and diddles is to use partimage as explained in the links above. I must admit I just got a little lazy to do it, even though it was as simple as storing an .iso on my external USB. It's pretty easy and fast to do, I just got lazy and now all I back up is /home. I run a pretty simple system and I don't really mind applying all those tweaks all over again.

Hope all that babbling makes sense.

K

---

### Post by Bashed on 2007-05-02
Thanks for your help. I'm trying to install it now, but I get this error:

configure: error: *** bzip2 library (libbz2) not found or too old: version 1.0.0 or more recent is need

Strange thing is I see this in synaptic

---

### Post by kolinab on 2007-05-02
Hmmm. It's been a while since I took these steps, and as I say I stopped using partimage, BUT if I remember correctly, I didn't even need to 'install' partimage at all. I think the simplest solution was to download and burn the 'System Rescue CD,' (see link above) which runs as a Live CD. From that session you can launch partimage. That way you can make an image of your hard drive while it is not mounted, which is important. I don't know if this would be possible while running a real, 'hard drive launched session' of Ubuntu.

Am I still making sense? Gold star for me if I am! :)

In short, I guess I took the long way around helping you with your installing problem by telling you that installing is not necessary . . .

---

### Post by scxtt on 2007-05-02
(assuming this is what you're doing): you don't need to install partimage to your install that you'll be backing up ... fire up a live CD, and install it in that session ... because you can't use partimage to backup a partition that's mounted ... i've done it at least a dozen times ...

---

### Post by ubnewbie2 on 2007-05-03
> **kolinab said:**
> Your question is good - you're right, if you just back up /home then all those countless hours of tweaking and diddling and installing are not backed up. I guess a few things would be preserved, but mostly just data, and not the 'state of the system.'

Your best bet if you want to safely preserve all those tweaks and diddles is to use partimage as explained in the links above. I must admit I just got a little lazy to do it, even though it was as simple as storing an .iso on my external USB. It's pretty easy and fast to do, I just got lazy and now all I back up is /home. I run a pretty simple system and I don't really mind applying all those tweaks all over again.

Hope all that babbling makes sense.

K

I'd at least back up the /etc directory as well as home.

and as someone else said, grab a copy of System Rescue CD. I used it, only last night, to back up my new feisty install.

---

### Post by Bashed on 2007-05-03
One thing I'm not understanding is how I'm supposed to boot off a live system recovery cd, yet to actual backup my o/s to a DVD? How will this work?

Also, where do I actually get system recovery? I've never done this before :)

---

### Post by kolinab on 2007-05-03
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page) is your key to making this work.

The reason you need to boot from a Live CD (which is what the system rescue CD is) is because if you try to backup all your OS files while your hard drive is mounted, it won't work. There will be a number of files and processes open, changing, etc. Your operating system will actively be using these files. 

The Live CD eliminates this problem. Follow the instructions on the System Rescue CD page above to download and burn the CD so you can load it 'live' (similiar to the way you installed Ubuntu probably). In the live session, your hard drive will be accessible, but the files will just be sitting there, waiting to be backed up. No open Ubuntu session to bungle things up.

Then you can launch partimage from the Live CD. As explained in one of the pyschocats links in my first email, you can select the partition you want to backup, decide on a file size for the backups, etc. The Partimage program just creates .iso images. That enables you to make one big .iso image to store on an external drive, or create smaller .iso images that you can write to as many CD's or DVD's as you need.

Hope that makes things clear!

K

---

