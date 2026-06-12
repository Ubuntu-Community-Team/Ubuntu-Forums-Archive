---
title: "I think I broke Synaptic?"
date: 2004-11-17
forum: General Help
---

### Post by dubdubdub on 2004-11-17
I don't know if this has anything to do with the problem, it is just what I did last.

I wanted to see what KDE was like. Tried to install it using Synaptic and got an error. From what I could tell the basic KDE libraries and such were installed, so I took them off.

Next time I tried to run Synaptic, and everyime after, I have been getting this message:

```

Preconfiguring packages . . .
Setting up sed (4.1.2-2) . . .

No 'StART-INFO-DIR-ENTRY' and not 'This file documents'.
install-info(/usr/share/info/sed.info): unable to determine description for 'dir' entry - giving up
dkpg: error processing sed (--configure):
subprocess post-installation script returned error exit status 1

Failed to apply all changes! Scroll in this bugger to see what went wrong


```

Machine has been restarted and I have ran apt-get udpate and apt-get upgrade a couple times in the past week.

And yes I learned my lesson to keep using Gnome :)

Any suggestions?

---

### Post by sfw5000 on 2004-11-17
This is a bug that is fixed with the latest version of synaptic. You'll need to download the sed package and unzip it into the /usr/share/info directory to replace what's there. The sed.info.gz file has somehow been currupted. Bug report here: [https://bugzilla.ubuntu.com/show_bug.cgi?id=3771](https://bugzilla.ubuntu.com/show_bug.cgi?id=3771)
```
sudo dpkg -x sed_4.1.2-1_i386.deb /usr/share/info
```
that should do it -- i will look for the link where you can download that package.

---

### Post by zenwhen on 2004-11-17
Edit: Beaten.  :smile:

---

### Post by dubdubdub on 2004-11-17
This looks like the file you speak of. Now I try your instructions. 

[http://linux.org.by/debian/pool/main/s/sed/sed_4.1.2-1_i386.deb](http://linux.org.by/debian/pool/main/s/sed/sed_4.1.2-1_i386.deb)

---

### Post by dubdubdub on 2004-11-18
hrmmmm same message :(

```
Preconfiguring packages ...
Setting up sed (4.1.2-2) ...

No `START-INFO-DIR-ENTRY' and no `This file documents'.
install-info(/usr/share/info/sed.info): unable to determine description for `dir' entry - giving up
dpkg: error processing sed (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 sed
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Should I try a different version of sed? This version is available: 
[   ] sed_4.1.2-4_i386.deb    17-Nov-2004 20:02   198k

---

### Post by dubdubdub on 2004-11-18
My last post about this one. I tried "sudo dpkg -x sed_4.1.2-1_i386.deb /usr/share/info" after downloading the file numerous times, never gave me an error or work. 

Would reboot after each attempt. On the 3rd reboot I was greeted with "force check dev/hda5" something about it hasn't been checked in 30 startups?

I logged in as usual,  "sudo dpkg -x sed_4.1.2-1_i386.deb /usr/share/info" and everything seems to be fine now. Even fixed the Nvidia drivers I was griping about in aother thread. Thanks!

---

### Post by sfw5000 on 2004-11-18
your disk will be checked for errors after every 30 boot ups. That's normal. FYI -- you should not need to reboot for changes like that. If you just close the program you're trying to update/fix, then restart that it should be fine. Sometimes you need to log out and log back in to Gnome, but you rarely need to restart. That's one of the great things about linux. So, 30 reboots is a heck of a lot.

Anyway, glad you got it working!

Sam

---

### Post by jdong on 2004-11-18
ext3 , by default , keeps ext2's behavior of checking the drives every 31 mounts or 180 days.

You _CAN_ turn that off if it really bothers you, but just to be on the safe side, it's best to run those checks.

---

### Post by dubdubdub on 2004-11-18
Yeah 30 restarts is ALOT for a few weeks, but I am also dual booting into XP to play Doom 3 and XIII. A couple times Gnome would crash with what seemed as an unrecoverable error, which I had to force restart.

I am used to leaving computers on. My mac is only restarted if a security update :)

---

