---
title: "Sill having ttf-mscorefonts-installer issues"
date: 2016-05-15
forum: General Help
---

### Post by jooge on 2016-05-15
I first found and followed the info found in this thread: [http://ubuntuforums.org/showthread.php?t=2286648](http://ubuntuforums.org/showthread.php?t=2286648)

I did what was suggested and it appeared to have worked at the time. When I booted my computer this morning I got that same little annoying waring again. Why did it now work when I thought I fixed the issue last night?

---

### Post by Bucky Ball on 2016-05-15
You had this issue after running:

```
sudo apt-get install ubuntu-restricted-extras
```

? Then try this:

```
sudo apt-get install --reinstall ttf-mscorefonts-installer
```

---

### Post by Autodave on 2016-05-15
[h=2]I had the same problem and here is what fixed mine: 



			Re: ttf-mscorefonts-installer won't run/work[/h] 		 				 				 		 			 				[INDENT] 					This bug was reported fixed [https://answers.launchpad.net/ubuntu/+question/290405](https://answers.launchpad.net/ubuntu/+question/290405)

We may have to get rough with it
 	Code:
 	sudo rm -rf /var/lib/update-notifier/package-data-downloads/partial/* 
Followed by
 	Code:
 	sudo apt-get --purge --reinstall install ttf-mscorefonts-installer 
 				[/INDENT] 			
  			   		
<snip>

---

### Post by Bucky Ball on 2016-05-15
> **Autodave said:**
> 
We may have to get rough with it
 	Code:
 	sudo rm -rf /var/lib/update-notifier/package-data-downloads/partial/* 
Followed by
 	Code:
 	sudo apt-get --purge --reinstall install ttf-mscorefonts-installer 

<snip> 				 			


Where did you get this? If you use [code] tags it keeps the formatting and you don't have to add all those indents. Better without. ;)

---

### Post by jooge on 2016-05-15
Thanks for the help guys. Looks good now.

---

### Post by Bucky Ball on 2016-05-15
Protocol here to share with the community what fixed your issue. Please do. Thanks.

---

### Post by TBerk on 2016-06-10
I'm having the same issues; New clean install of Ubuntu Studio 16.04 (XFCE); I reformatted my OS partition but did nothing to my separate /Home partition.

I installed 'xubuntu-restricted-extras', like I normally would have but I keep gettig the 

"Information Available' & "Update Information" &Failure to download extra data files" nag screen.

After a reboot to clear the ram I ran 'sudo dpkg --configure -a'

"Setting up update-notifier-common (3.168) ..." 

ran OK, but then I got the same old stuck in the mud feeling...


```

ttf-mscorefonts-installer: downloading [http://downloads.sourceforge.net/corefonts/andale32.exe](http://downloads.sourceforge.net/corefonts/andale32.exe)
Get:1 [http://downloads.sourceforge.net/corefonts/andale32.exe](http://downloads.sourceforge.net/corefonts/andale32.exe) [969 B]
Err:1 [http://downloads.sourceforge.net/corefonts/andale32.exe](http://downloads.sourceforge.net/corefonts/andale32.exe)                  
  Hash Sum mismatch
Fetched 969 B in 3min 2s (5 B/s)                                               
```
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/andale32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
[/quote]

Previously Ive tried a number of things, including downloading the msfonts manually and I followed the 'Get Rough' instructions;

> We may have to get rough with it
Code:

sudo rm -rf /var/lib/update-notifier/package-data-downloads/partial/*

Followed by
Code:

sudo apt-get --purge --reinstall install ttf-mscorefonts-installer


All to no avail.

---

### Post by Bucky Ball on 2016-06-10
At TBerk: Probably better to post a new thread. The originator of this one didn't respond to my request to post the fix they used and haven't been around for two weeks, so ...

A new thread would probably improve your chances.

---

