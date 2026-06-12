---
title: "how do I force fsck"
date: 2006-11-28
forum: General Help
---

### Post by btboudreaux on 2006-11-28
How do I force a fsck on the next reboot?

I've tried 

sudo shutdown -rF now
sudo shutdown -F -r now

and various other combinations I've read but none of them make the fsck come up.

When I look at shutdown --help, -F isnt even listed

Is there something else I have to do???

---

### Post by Shay Stephens on 2006-11-29
Try this:
```
sudo shutdown -Fr now
```

I also found the shutdown flags and what they mean:
OPTIONS
       -a     Use /etc/shutdown.allow.

       -t sec Tell init(8) to wait sec seconds between sending processes  the
	      warning  and  the	 kill signal, before changing to another run-
	      level.

       -k     Don't really shutdown; only send the warning messages to every-
	      body.

       -r     Reboot after shutdown.

       -h     Halt after shutdown.

       -n     [DEPRECATED]  Don't  call	 init(8) to do the shutdown but do it
	      ourself.	The use	 of  this  option  is  discouraged,  and  its
	      results are not always what you'd expect.

       -f     Skip fsck on reboot.

       -F     Force fsck on reboot.

       -c     Cancel  an  already running shutdown. With this option it is of
	      course not possible to give the  time  argument,	but  you  can
	      enter  a	explanatory  message on the command line that will be
	      sent to all users.

---

### Post by bettlebrox on 2006-11-29
Looks like the version of shutdown with Ubuntu doesn't support the -f or -F flags. The version with Debian does.

What you can try is to create a file in / called forcefsck

sudo touch /forcefsck

---

### Post by ciscosurfer on 2006-11-29
> **btboudreaux said:**
> How do I force a fsck on the next reboot?

I've tried 

sudo shutdown -rF now
sudo shutdown -F -r now

and various other combinations I've read but none of them make the fsck come up.

When I look at shutdown --help, -F isnt even listed

Is there something else I have to do???[This page will solve the problem for you]("https://ubuntu.wordpress.com/2005/10/12/tuning-the-filesystem-check-at-bootup/").  Read the whole post as its quite insightful.  If you need any other help with this, just post back. ;)

---

### Post by btboudreaux on 2006-11-30
Thanks that link was helpful. And I'll just put the blank forcefsck file in the root when I want to force a check.

---

### Post by adam.tropics on 2006-11-30
If you're a fan of choice, you might [like to look at this]("http://www.ubuntuforums.org/showthread.php?t=295262&highlight=Bonager"). It sits in the notification tray. If you hover over it, it will tell you when the next scheduled scan is (how many more boots), and if you click it, it gives you the option to force a scan on the next boot. I have tried it, and it seems pretty good.

---

### Post by ciscosurfer on 2006-11-30
> **adam.tropics said:**
> If you're a fan of choice, you might [like to look at this]("http://www.ubuntuforums.org/showthread.php?t=295262&highlight=Bonager"). It sits in the notification tray. If you hover over it, it will tell you when the next scheduled scan is (how many more boots), and if you click it, it gives you the option to force a scan on the next boot. I have tried it, and it seems pretty good.I use Bonager as well and it does work just like its supposed to.  Very handy if you don't feel like messing with the command line. :D

---

### Post by Ramses de Norre on 2006-11-30
In edgy the shutdown -F and -f options seem to be broken.. Maybe due to upstart? I now just use touch /forcefsck too and that works perfect.

By the way, you can also do touch /fastboot to disable fsck for the next boot. (similar to the -f option from shutdown)

---

