---
title: "Issue with Gparted Live CD"
date: 2008-03-25
forum: General Help
---

### Post by darth.k on 2008-03-25
I used the Ubuntu guided installation to partition my drive when I first installed the operating system giving 60gb to unbuntu and 240gb to Xp.

After using for about a week I've decided that I want to stick with ubuntu and make my Xp partition smaller.  However I seem to be having a problem with the Gparted Live Cd in that I cant get it to run.  I get to the following point;

> >>Determining root device
>>Determining loop type...
!!Invalid loop location /gparted.dat
!!Please export LOOP with a valid location, or reboot and pass a proper loop...
!!Kernal command line!

Busy v1.1.3 (2007.11.28-18:36+0000) Built in shell (ash)\Enter "help" for a list of built in commands

/bin/ash: can't access tty; job control turned off
/newroot#

also when i try to type a command ie 'help' it types each letter twice a in 'hheellpp'

thanks.

---

### Post by mc4man on 2008-03-25
If it  boots up to a selection screen choose 'force Vesa driver - 8th choice down I think

---

### Post by darth.k on 2008-03-25
this didn't work, produced the same outcome as the original problem.

---

### Post by mc4man on 2008-03-25
Thats' the only one that' ever worked for me - I guess I'd start at the top and try them all - I can't see any harm caused by it not loading (except that one about boot from usb/cd ?)
What pc do you have ?

a good place to search -  [http://gparted-forum.surf4.info/viewforum.php?id=3](http://gparted-forum.surf4.info/viewforum.php?id=3)

---

### Post by forestpixie on 2008-03-25
I had some problems with a new version of gparted a while back - got hold of parted magic and that worked without any problems. I read here somewher that gparted was not being supported/developed anymore.

You could use the version that's on the buntu livecd as well.

[http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Downloads](http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Downloads)

---

### Post by darth.k on 2008-03-26
tried parted magic, went through the load then it stopped at this;

i have no name

---

