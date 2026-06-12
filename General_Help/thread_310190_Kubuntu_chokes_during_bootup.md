---
title: "Kubuntu chokes during bootup"
date: 2006-11-30
forum: General Help
---

### Post by dgray_from_dc on 2006-11-30
I was experiencing what I think is a common problem with Kubuntu Edgy upgraded from Dapper.  When I booted my machine, the screen went blank after usplash.  My work-around was to use a Ctrl-Alt-*Fx* key to log in on a text-mode console and startx manually.  Once I did that, everything worked fine.  I scanned the forums looking for a solution and found a thread which seemed to solve my problem. (post #19)

[http://www.ubuntuforums.org/showpost.php?p=1585026&postcount=19]("http://www.ubuntuforums.org/showpost.php?p=1585026&postcount=19")

After doing this, Kubuntu will no longer boot.  From GRUB, it selects the appropriate kernel says that it's booting and then just hangs.  The only way I can access Linux is in Single-User-Mode.  I figure all that I have to do is reverse what I did.  However, in Single-User-Mode the root file system is read-only so dselect won't work, nor will dpkg, nor apt-get.

How do I run dselect in Single-User-Mode?

Do I need to burn a CD and change my access method or can I enable networking from Single-User-Mode?

If so, how do I enable eth0?

---

### Post by dgray_from_dc on 2006-12-06
OK, so I've burned a copy of the Kubuntu Edgy Alt CD, chosen Rescue broken system boot option, changed my sources.list to disable all web-based repositories (due to lack of DNS resolution), and done an

apt-get cdrom add

There is no sysvinit on the install CD!!!!

I removed upstart, and reinstalled, at which point my machine reboots and get stuck at the same point.  This gives me the distinct impression that upstart is my problem.  As soon as its' setup finishes, the machine reboots and hangs just like my original upgrade caused it to.

I have a Hoary CD and tried to add it through apt-get and it isn't recognized.

I have come to love Kubuntu, I've used it almost exclusively for over a year because up until now, it's been rock-solid.  I was even confident enough in it to risk storing irreplaceable data in my home directory without creating a separate partition for it.  (Not the wisest thing I know).  However, at this point, I'm considering trying to mine my data out, giving up, and doing a reinstall.   (NOT desirable because I'll still lose quite a bit of stuff).  I figure with a problem as seemingly simple as this, there'd be a solution out there somewhere.  I however lack the knowledge to do this alone.

What am I doing wrong?

HELP!!

---

### Post by dgray_from_dc on 2006-12-18
I give up!  Being unable to use Kubuntu for a rescue CD, I turned to Knoppix.  I booted into Knoppix, formatted my USB stick ext2, copied my /home directory, and started from scratch.  Once I reinstalled all of my software, and restored my files to my /home **_partition_** the system snapped back to its old self, settings, preferences and all.

**_Note:_** It was necessary to reformat my USB stick due to FAT16's inability to distinguish case in filenames.

---

### Post by 454redhawk on 2006-12-18
Give up on Kubuntu! If you like KDE then give MEPIS a try. MEPIS is better in every way compared to Kubuntu. Its based on Ubuntu so these wonderful forums will still apply.:)

---

