---
title: "ubuntu booting problems. read please"
date: 2007-06-17
forum: General Help
---

### Post by m4ttjirM on 2007-06-17
Hi,

here is my situation - I am running ubuntu feisty and I have a lot of settings that I love.

I have ubuntu installed on my 2nd hard drive, and windows xp installed on my first hard drive (2 seperate drives)  Recently my windows isntall went to **** so I had to reformat windows.  After I reformatted windows, I lost grub.  So I read the instructions online to get grub back.  

I now have grub back, but I can't log-in to UBUNTU or Windows anymore.

once again I have XP on my 1st hard drive, and UBUNTU on my 2nd hard drive.  

Should I go into the live cd terminal and try to restore my grub again?  Maybe I just restored grub wrong?  Any suggestions would be appreciated

I have read a lot of past forums on google and it  gets a little confusing because most of the problems are for people with ubuntu and windows on the same HD, mine are seperated. (they are both on the same IDE cable, XP Hd is primary, and UBUNTU HD is the slave)

I know that all my files are still intact on both the drives. Just some booting problems.

Thank you,

Matt

---

### Post by merlinus on 2007-06-17
This may help:

[http://ubuntuforums.org/showthread.php?t=474734&highlight=two+hard+drives](http://ubuntuforums.org/showthread.php?t=474734&highlight=two+hard+drives)

and this:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

-merlin

---

### Post by m4ttjirM on 2007-06-17
Thank you so much.

The guide I read was a little sketchy so what I did was set both commands to 0,1 instead of the second one to just 0.

The first guide had instructed me to do both to 0,1

Now can a "broken grub" still be fixed the same way as a "missing grub" ?

Because the first time, the grub just wasn't there.  The grub is there now, but just not working.

Also - does anybody know if this will fix my problems for logging into windows as well?

The only reason i still have windows on here is to use Counter strike, with ventrilo because I have a team that I play counterstrike with and I don't want there to be any performance issues, otherwise I would be 100% ubuntu. Oh yea I also use frontpage on XP. Still looking for a good substitute for that on ubuntu.

Thank you,

Matt

---

### Post by confused57 on 2007-06-17
> **m4ttjirM said:**
> Thank you so much.

The guide I read was a little sketchy so what I did was set both commands to 0,1 instead of the second one to just 0.

The first guide had instructed me to do both to 0,1

Now can a "broken grub" still be fixed the same way as a "missing grub" ?

Because the first time, the grub just wasn't there.  The grub is there now, but just not working.

Also - does anybody know if this will fix my problems for logging into windows as well?

The only reason i still have windows on here is to use Counter strike, with ventrilo because I have a team that I play counterstrike with and I don't want there to be any performance issues, otherwise I would be 100% ubuntu. Oh yea I also use frontpage on XP. Still looking for a good substitute for that on ubuntu.

Thank you,

Matt

Your grub boot entries would depend on which drive you're booting to first...if you have grub installed on your Window's drive that you're booting to first, then your Ubuntu root would be (hd1,#); however, if you're booting first to your Ubuntu drive then Ubuntu's root would be (hd0,#)...you can experiment by highlighting your Ubuntu entry in the grub boot menu, press "e" to edit, then change your root, then press "b" to boot...it's a temporary change, but may be worth trying...it can be made permanent, if it works.

---

### Post by m4ttjirM on 2007-06-17
To me, it doesn't really matter what I boot to first.  As long as they are both listed in my grub, and I can use which one I need to when I prefer.  Everything was setup perfectly until I had to reformat the XP hard drive.  Neither of them work now and I am on the live cd, I am going to try some things and hopefully it works :)

Thank you.

---

### Post by m4ttjirM on 2007-06-17
Okay I got the ubuntu to work, now im gonna work on getting the new XP install bootable :)

---

### Post by LinuxNathan on 2007-07-11
Beleive it or not, microsoft operating systems are designed to seek out and kill linux operating systems.
So when you ran that XP reinstall it decided to screw some things in your linux drive.

The only way XP can't do this if, they are on the same harddrive, but different partitions.

 - Nathan. :)

---

