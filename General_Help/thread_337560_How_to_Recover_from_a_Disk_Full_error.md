---
title: "How to Recover from a Disk Full error?"
date: 2007-01-13
forum: General Help
---

### Post by solderhead on 2007-01-13
I made the fatal error of letting bittorrent fill my hard drive.  The system locked up because some apps couldn't write to disk, and my only way out was to reboot.  Now I know that I should enable disk quotas.

I freed up some disk space by booting the system from a Live CD, and deleting the torrent data.  Then I rebooted the system.

When I attempt to reboot, I'm stuck in a GDM logon loop.  GDM accepts the username and password, and attempts to start X.  But then the user is dumped back at the GDM logon screen.

Any ideas?

---

### Post by dcstar on 2007-01-13
> **solderhead said:**
> I made the fatal error of letting bittorrent fill my hard drive.  The system locked up because some apps couldn't write to disk, and my only way out was to reboot.  Now I know that I should enable disk quotas.

I freed up some disk space by booting the system from a Live CD, and deleting the torrent data.  Then I rebooted the system.

When I attempt to reboot, I'm stuck in a GDM logon loop.  GDM accepts the username and password, and attempts to start X.  But then the user is dumped back at the GDM logon screen.

Any ideas?

Boot off the Live CD and do a fsck on the hard disk - that may repair some possible filesystem corruption that may be causing the problem.

You also may want to clean out the /tmp directory as well, just to ensure that you do have enough free space in the / directory.

---

### Post by OldSeaDog on 2007-01-15
I don't know if solderhead was helped but I have a similar problem.  I have a 200GB drive for home use (I am a musicphile) and I am currently setting it up.  I went to use it the other day, and it had crashed.  It promptly did the same thing two more times, and when I went to log in my home drive was full.  It should have been less than 10% full at that point.  When I login as root at tty1 and check, df shows it 100% full, but the actual directory at the 'root' of the drive shows only 8.9 GB present.  fsck came back with no errors, but showed the block count very high, at 98% full.  tmp is empty, as is the trash.  There are no 'hidden' files that I can see.

When I run df looking only at the inodes, the drive is only 1% in use, so that is not the problem, there has to be one or more monster files tying up all the inodes.  How can I find them?  baobab is running now, but I don't expect much luck - it is still scanning after 4 hours!

How can I find the offender(s)?

OldSeaDog, the Geekosaur

---

### Post by trace_on on 2007-02-27
I have got exactly the same problem, and I have not found an answer yet. What happened with your missing space? Did you manage to solve it? Any information would be very appreciated.
-Alex

---

### Post by Moses on 2007-02-27
I suspect I have the same problem, check out this thread [http://www.ubuntuforums.org/showthread.php?t=337560](http://www.ubuntuforums.org/showthread.php?t=337560)

Only problem, is I get no errors whatsoever, so I can't be too sure.

I am going to try free some space now, and then I will report back. ;)

---

### Post by Moses on 2007-02-27
I just booted into reocvery mode and deleted the game 'legends',  I then rebooted and was able to login. :)

---

