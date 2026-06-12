---
title: "System won't boot from the hard drive"
date: 2008-04-16
forum: General Help
---

### Post by kjt422 on 2008-04-16
My computer was running fine then I turned around to look at it and the screen was black and there was an error message on the bottom of the screen.  Stupidly, I rebooted it quickly without writing the message down and now it won't start Ubuntu.  

I turn it on it says "kernel alive" and then I get a black screen and nothing happens.  The monitor is working fine and I booted Ubuntu from the CD but I have no idea how to analyze or repair whatever is wrong with my HD.  I tried running fsck but it won't let me.  I'm posting some of the stuff from terminal I got in the hopes this will help

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
/dev/sda1 on /media/disk type ext3 (rw,nosuid,nodev)
ubuntu@ubuntu:~$ fsck.ext3 -p /dev/sda1
fsck.ext3: Permission denied while trying to open /dev/sda1
You must have r/w access to the filesystem or be root
ubuntu@ubuntu:~$ 


Any help would be greatly appreciated.  Thanks!

-Kyle

---

### Post by oilchangeguy on 2008-04-16
please explain what you were doing, before you took your eyes off the screen.

---

### Post by kjt422 on 2008-04-16
Thanks for the quick responses!   I was just listening to music

---

### Post by oilchangeguy on 2008-04-16
> **kjt422 said:**
> Thanks for the quick responses!   I was just listening to music

ok, but as a general rule, computers don't just die on their own (most of the time). they require some type of operater error (not operating system) first. were you doing something to the computer, while you were playing music?

---

### Post by kjt422 on 2008-04-17
I played an entire album for the first time that I had just download via torrent.  Maybe there was a virus hidden on a song in the middle of the album?  Sorry I can't give you any more info.  Thanks for the help guys!

-kyle

---

### Post by kjt422 on 2008-04-17
was online for a while(about a week) prior to getting my security systems up and running.  I received a warning from my Ubuntu OS that an error occurred that was "consistent with someone trying to access my computer remotely"  This was about two days ago.  This is all the info I have.  I am a brand new user to Linux so I am at a bit of a loss.  Thanks so much for all the help.

cheers,
       Kyle

---

