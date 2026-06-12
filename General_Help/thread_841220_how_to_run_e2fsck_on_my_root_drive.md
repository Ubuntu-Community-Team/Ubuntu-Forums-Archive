---
title: "how to run e2fsck on my root drive?"
date: 2008-06-26
forum: General Help
---

### Post by breadbin on 2008-06-26
hiya anyone tell me how to run e2fsck on my linux partitions. i know the command is e2fsck -f -y -v /dev/sda1 or whatever but what if the partition is mounted and busy. my root drive is /dev/sda2 and my home is /dev/sda4 and i cannot umount either of them. how do i go about this? thanks

---

### Post by Nepherte on 2008-06-26
Use the live cd.

---

### Post by brian_p on 2008-06-26
> **breadbin said:**
> hiya anyone tell me how to run e2fsck on my linux partitions. i know the command is e2fsck -f -y -v /dev/sda1 or whatever but what if the partition is mounted and busy. my root drive is /dev/sda2 and my home is /dev/sda4 and i cannot umount either of them. how do i go about this? thanks

Boot into rescue mode. Or take the system to single-user level with

 ```
sudo init 1
```

---

### Post by breadbin on 2008-06-26
thanks i'll try that. thats sort of what i was thinking of but couldn't remember how to do it. thanks

---

### Post by chrisccoulson on 2008-06-26
No need to boot to a live CD, and booting to recovery mode is no use as your root filesystem will still be mounted.

To run fsck on all volumes, just do the following in a terminal:
```
sudo touch /forcefsck
sudo reboot
```
...this will cause the system to reboot and perform a full check of all volumes

---

### Post by brian_p on 2008-06-26
> **chrisccoulson said:**
> No need to boot to a live CD, and booting to recovery mode is no use as your root filesystem will still be mounted.

To run fsck on all volumes, just do the following in a terminal:
```
sudo touch /forcefsck
sudo reboot
```
...this will cause the system to reboot and perform a full check of all volumes

```
shutdown -F now
```

Less typing!

---

### Post by chrisccoulson on 2008-06-26
> **brian_p said:**
> ```
shutdown -F now
```

Less typing!

You're correct ;)

---

### Post by brian_p on 2008-06-26
> **chrisccoulson said:**
> You're correct ;)

I'm also lazy.

Nice though these one or two line commands are I'm inclined to advocate getting some practice with the single-user run level. It's easy to get in via rescue and there may be a time when it's needed.

---

### Post by Taxman415a on 2008-06-26
> **brian_p said:**
> ```
shutdown -F now
```

Less typing!

Also not in the manpage. Mind filing a bug report? ;)

---

### Post by brian_p on 2008-06-26
> **Taxman415a said:**
> Also not in the manpage. Mind filing a bug report? ;)

It's in mine on Debian stable. Nothing to file!

```
-F     Force fsck on reboot.
```

---

### Post by chrisccoulson on 2008-06-26
It's not in the manpage on Hardy...

---

### Post by brian_p on 2008-06-26
> **chrisccoulson said:**
> It's not in the manpage on Hardy...

Strange. I've just looked at man 8 shutdown on my Hardy machine. -F is in between -f and -c.

---

### Post by chrisccoulson on 2008-06-26
man 8 shutdown:

```
shutdown(8)                                                        shutdown(8)



NAME
       shutdown - bring the system down

SYNOPSIS
       shutdown [OPTION]... TIME [MESSAGE]

DESCRIPTION
       shutdown arranges for the system to be brought down in a safe way.  All
       logged-in users are notified that the system is going down and,  within
       the last five minutes of TIME, new logins are prevented.

       TIME  may  have  different  formats, the most common is simply the word
       &#8217;now&#8217; which will bring the system down immediately.  Other  valid  for&#8208;
       mats  are  +m,  where m is the number of minutes to wait until shutting
       down and hh:mm which specifies the time on the 24hr clock.

       Once TIME has elapsed, shutdown sends a request to the  init(8)  daemon
       to bring the system down into the appropriate runlevel.

OPTIONS
       -r     Requests  that  the system be rebooted after it has been brought
              down.

       -h     Requests that the system be either halted or powered  off  after
              it has been brought down, with the choice as to which left up to
              the system.

       -H     Requests that the system be halted after  it  has  been  brought
              down.

       -P     Requests  that  the  system  be  powered  off  after it has been
              brought down.

       -c     Cancels a running shutdown.  TIME is  not  specified  with  this
              option, the first argument is MESSAGE.

       -k     Only  send  out  the warning messages and disable logins, do not
              actually bring the system down.

NOTES
       This tool is provided for compatibility with the traditional  System  V
       init(8).   Upstart  has  no  notion  of  runlevels itself, this and the
       telinit(8) tool are provided to emulate their behaviour.

       When invoked it generates a runlevel event, with an argument containing
       the new runlevel.

AUTHOR
       Written by Scott James Remnant.

REPORTING BUGS
       Report bugs at [https://launchpad.net/products/upstart/+bugs](https://launchpad.net/products/upstart/+bugs)

COPYRIGHT
       Copyright © 2007 Canonical Ltd.
       This is free software; see the source for copying conditions.  There is
       NO warranty; not even for MERCHANTABILITY or FITNESS FOR  A  PARTICULAR
       PURPOSE.

SEE ALSO
       init(8) telinit(8)



Upstart                           March 2007                       shutdown(8)
```

---

### Post by brian_p on 2008-06-26
> **chrisccoulson said:**
> man 8 shutdown:

Did I say I had looked at the shutdown manual on on Hardy machine? Well, I would have if I had used the correct path to the partition it resides on! But I've learned something. Ubuntu uses upstart and it looks like the shutdown manual in that package replaces the one from the sysvinit package. Seems -F is off the menu for Ubuntu users.

---

### Post by chrisccoulson on 2008-06-26
That makes a bit more sense now!

---

### Post by brian_p on 2008-06-26
> **chrisccoulson said:**
> That makes a bit more sense now!

Bug #74139 is also informative.

---

### Post by breadbin on 2008-06-27
thanks for the suggestions, i'll keep a note of them but got it done the hard way. used the init 1 way for the /home partition and then also found the system was still mounted so had to use the live cd for that one but got it done. 

something that was bothering me can e2fsck be trusted? i recently changed the partitions around and grew the /home partition from 100Gb to 200Gb. i let it go and came back after about 20 minutes and it was still going but said it would be finished in 8 hours 30 miuntes. i cancelled it and risked the damage but i seemed to have gotten away with it so far. is the e2fsck check enough?

---

### Post by unutbu on 2008-06-27
If you were doing a resize operation that was estimated to take 8+ hours, I suspect you were moving the left end point of the partition. (Am I right?) Files might have been in the process of being moved when the resize operation was cancelled. 
Those files (if there were any -- this is just speculation) would have left the filesystem in a semi-broken state which e2fsck could fix, but in the process of doing so e2fsck might have thrown away the broken inodes (that is, thrown away the half-moved files).

The bottom line is, I'd try to verify that all my files are present and accounted for.

---

