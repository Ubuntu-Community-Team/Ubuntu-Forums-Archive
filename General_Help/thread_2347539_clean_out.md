---
title: "clean out"
date: 2016-12-26
forum: General Help
---

### Post by pete1977x on 2016-12-26
I have a dual boot ubu 14 with windows 10. Its working good. But I checked my disk utility and my ubu filesystem has 77 gigs full and only 5 free. This is not the Windows partition
but one of the 2 ubu partitions. I have VERY little on my PC. Just a few things I need, I dont store movies  or any of that. A few flac files maybe 10 gig.Iso maybe 10 gig.
How can there possibly be that much on there??? I ran the clean commands and purge and that freed up maybe 3 gig.
What is going on here and how can I clean it. If I had to guess there is at least 40 gigs of mystery files in here.....

---

### Post by howefield on 2016-12-26
Have a look at var/log/ - how much disk space is it taking ?

---

### Post by pete1977x on 2016-12-26
thats where it is  about 55 gigs....What the hell  is in there????  my partition is about 70 gigs.... i saw on the disk usage utility..
I am on a cable internet connection which is unusual for me.... comcast...

---

### Post by howefield on 2016-12-26
Whatever it is it indicates a problem which should be investigated before deleting.

Are you able to determine which log is the troublesome (large) one ?

---

### Post by pete1977x on 2016-12-26
my ubuntu froze and wouldnt boot. I think I lost all disk space. I re installed from my iso  ubuntu again and its ok now. How can I make sure var doesnt copy too many files again??
or do I have to delete files manually??

---

### Post by howefield on 2016-12-26
If there is a problem that is spamming the logs it'll most likely resurface, in other words reinstalling may not resolve the issue.

So keep an eye on the size of the logs and if you spot one of them growing quickly have a look at the contents to inspect for recurring lines.

---

### Post by pete1977x on 2016-12-26
will this code stop it..

sudo sed -i '/^LOGLEVEL/s/=.*/=low/' /etc/ufw/ufw.conf

---

### Post by oldfred on 2016-12-26
What brand/model system?

If an Asus:
 Asus x555u w/o pci=nomsi - space issue on drive and runaway log files filling drive
[https://ubuntuforums.org/showthread.php?t=2327103&page=3](https://ubuntuforums.org/showthread.php?t=2327103&page=3)
[https://ubuntuforums.org/showthread.php?t=2327570](https://ubuntuforums.org/showthread.php?t=2327570)

---

### Post by pete1977x on 2016-12-26
isnt there a simple app to delete .gz files in var...???? I dont trust bleachbit...

---

### Post by Keith_Helms on 2016-12-26
Are you referring to the gzipped logfiles under /var/log?  The logrotate command is supposed to take care of deleting archived logfiles.  The configuration files /etc/logrotate.conf and in the /etc/logrotate.d directory control how often to archive a logfile and how many past generations to keep.

---

### Post by oldos2er on 2016-12-26
rm? ```
sudo rm /var/log/*.gz
```

---

### Post by howefield on 2016-12-26
Threads merged.

---

### Post by pete1977x on 2016-12-26
obviously something wasnt working with logrotate.

---

### Post by Keith_Helms on 2016-12-26
> **pete1977x said:**
> obviously something wasnt working with logrotate.

We would have to see a listing of the log directory before confirming logrotate isn't working.  Logrotate just runs daily and is supposed to keep n generations of various logfiles depending on the configuration files.  It does NOT do anything to prevent any logfile from becoming extremely huge.

If something is filling up a partition on your system, you would need to figure out the problem before reinstalling and wiping out the evidence.

If you notice the free space is getting smaller, you can investigate where it is going.

To see the biggest files under /var, you can run a command string like this:
```
find /var -type f -print0 2>/dev/null | xargs -0 -I{} ls -l {} 2>/dev/null | sort -nr -k 5,5 | head -n10
```
That would show the 10 biggest files under /var.  On my system, I get the following:
```
-rw-r--r-- 1 root             root             58733428 Dec 19 11:24 /var/cache/apt/archives/chromium-browser_55.0.2883.87-0ubuntu0.16.04.1263_amd64.deb
-rw-r--r-- 1 root             root             48877898 May 11  2016 /var/cache/pepperflashplugin-nonfree/google-chrome-stable_50.0.2661.102-1_amd64.deb
-rw-r--r-- 1 root             root             45855918 Nov 30 14:44 /var/cache/apt/archives/firefox_50.0.2+build1-0ubuntu0.16.04.1_amd64.deb
-rw-r--r-- 1 root             root             45824006 Dec 13 10:07 /var/cache/apt/archives/firefox_50.1.0+build2-0ubuntu0.16.04.1_amd64.deb
-rw-r--r-- 1 root             root             45477248 Dec 26 13:32 /var/cache/apt/pkgcache.bin
-rw-r--r-- 1 root             root             45415455 Dec 26 13:32 /var/cache/apt/srcpkgcache.bin
-rw-r--r-- 1 root             root             41813552 Apr 21  2016 /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_xenial_universe_binary-amd64_Packages
-rw-r--r-- 1 root             root             41649086 Apr 21  2016 /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_xenial_universe_binary-i386_Packages
-rw-r--r-- 1 root             root             38633266 Dec  5 09:40 /var/cache/apt/archives/linux-image-extra-4.4.0-53-generic_4.4.0-53.74_amd64.deb
-rw-r--r-- 1 root             root             38615822 Nov 28 15:33 /var/cache/apt/archives/linux-image-extra-4.4.0-51-generic_4.4.0-51.72_amd64.deb

```

Package files for browsers and linux kernels - nothing unexpected.

If /var doesn't seem to be the problem, you can search on / to check all files or you can add multiple paths to the find command like *find /var /boot /lib -type f ...*

---

### Post by pete1977x on 2016-12-27
that code didnt work.  how surprising in linux.

---

### Post by oldfred on 2016-12-27
I copied & pasted into my terminal, and it worded just fine.
Then added to my page on housecleaning.
It did take a bit as it has to scan all of /var then sort files. And my system is SSD. 
If on hard drive may have to just let it run for a bit.

---

### Post by Keith_Helms on 2016-12-27
It takes about 12 seconds to scan /var on my system with a hard drive not an SSD.  To scan all of / takes a few minutes.

---

### Post by vasa1 on 2016-12-27
> **pete1977x said:**
> that code didnt work.  how surprising in linux.
What exactly do you mean by the second part of this post?

---

