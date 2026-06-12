---
title: "Corrupted GIMP file causing rage."
date: 2013-12-10
forum: General Help
---

### Post by michaelcanlbel on 2013-12-10
Alright so, I downloaded Ubuntu 13.10 about 2-3 days after it came out, and I've been using my computer normally ever since then. 2 days after I updated Ubuntu, the computer shut down by itself. I rebooted it, and realised that everything was normal, but GIMP was gone (it had dissapeared on the toolbar), And for some reason I ignored It. For the past 3 days I've been struggling to find a solution to this problem, and considering I'm a teenager that has barely had any experience with ubuntu aside from using it casually (i've used the terminal maybe 2-3 times before this week) It probably wasn't the best position to find myself in.

Anyways, My main issue is that this Gimp file is causing errors and frustration. My computer can not do anything aside from browse online because if I play a game (such as minecraft) of sometimes even watch a youtube video, The system will shut itself off (not heat or power related issues). I also can't go sudo apt-get Install, remove, autoremove or upgrade because after the command is almost finished, this pesky line always shows up at the end: 
dpkg: unrecoverable fatal error, aborting: files list file for package `gimp' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)


At the start, I attempted to put it in trash and and clear it (eventually I managed To get the file to dissapear) which due to my in-experience, I assumed I fixed the problem. How ever, I realised that it kept on shutting down, and when even i'd try to install updates (from the pop-up that checks for updates daily) They would always say they ended up failing.
So a few days ago I decided to do something about it. I tried many and many different terminal commands though none did anything. And I can't force remove or purge the GIMP file itself.
Example of my attempting to remove gimp file 
```
leblanc@Leblancfamilydesktop:~$ sudo apt-get remove gimp -fReading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  lsb-core lsb-security ncurses-term pax
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  gimp
0 upgraded, 0 newly installed, 1 to remove and 37 not upgraded.
After this operation, 15.3 MB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: unrecoverable fatal error, aborting:
 files list file for package `gimp' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)
leblanc@Leblancfamilydesktop:~$ 



```

If anybody has any suggestions at all, Please help. (It would be VERY appriciated)

---

### Post by michaelcanlbel on 2013-12-10
Also to be noted that another line that I'm seeing frequently is:
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

---

### Post by steeldriver on 2013-12-10
Is the gimp package still in your package cache?

```
find /var/cache/apt -name 'gimp*'
```

---

### Post by michaelcanlbel on 2013-12-11
```

leblanc@Leblancfamilydesktop:~$ find /var/cache/apt -name 'gimp*'
/var/cache/apt/archives/gimp_2.8.6-1ubuntu1.1_i386.deb
/var/cache/apt/archives/gimp_2.8.6-1ubuntu1_i386.deb
/var/cache/apt/archives/gimp-help-common_2.6.1-1_all.deb
/var/cache/apt/archives/partial/gimp-help-en_2.6.1-1_all.deb
/var/cache/apt/archives/gimp-data_2.8.6-1ubuntu1.1_all.deb


``` 

I'm assuming that's a yes....

---

### Post by michaelcanlbel on 2013-12-15
bump, still having consistent problems, Also to be noted that when I ran a memtest, it shut down in the first five minutes, same thing when I tried using clamtk.

---

### Post by steeldriver on 2013-12-15
I think a shutdown during memtest is likely to be a hardware / power management / overheating issue and nothing to do with your gimp filelist file

Those filelist files are a bit of a PITA. The reason I asked about the deb file is that the gimp.list file contains essentially the same information that you can get by running 'dpkg-deb -c' on the deb file. However the format is not the same, I spent some time recently trying to come up with a simple 'converter' and could get to the point that it had all the right files (as confirmed by grepping one against the other) but not necessarily in the right order (as confirmed by a straight 'diff'). That *may* be good enough - at least to keep the package management system happy for long enough to reinstall the package (which should fix the file).

If you want to try that route lmk and I will take another shot at it. You can also get the files list from packages.ubuntu.com but again it does not have the right format.

---

### Post by michaelcanlbel on 2013-12-15
I had to get my hard drive wiped/reformatted before I changed to ubuntu so my computer wasn't exactly in a stable condition before hand either, so yeah it's probably a hardware issue. And as far as what you just said, I would have to admit that I am fairly confused with what I should do now.

---

### Post by steeldriver on 2013-12-15
OK so I notice you cache contains both gimp_2.8.6-1ubuntu1_i386.deb and gimp_2.8.6-1ubuntu1**.1**_i386.deb - can we just confirm which is actually installed before we proceed?

```
dpkg -l gimp
```

---

### Post by michaelcanlbel on 2013-12-15
Result:
```

leblanc@Leblancfamilydesktop:~$ dpkg -l gimp
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ri  gimp           2.8.6-1ubunt i386         The GNU Image Manipulation Progra


```

---

### Post by steeldriver on 2013-12-15
that output seems to be truncated - can we try 

```
dpkg -s gimp | grep Version
```

just to double check?

---

### Post by michaelcanlbel on 2013-12-15
Sure

```

Version: 2.8.6-1ubuntu1

```

---

### Post by steeldriver on 2013-12-15
OK so I have tested this to the best I can (by backing up my own gimp.list file and then creating an empty one - which produced the same error as yours on trying to upgrade) but **I cannot guarantee it will work - use at your own risk**

1. back up the existing file (I know it's broken, but let's take no chances)

```
sudo cp /var/lib/dpkg/info/gimp.list /var/lib/dpkg/info/gimp.list.bak
```

2. generate a new list file from the archived deb file

```
dpkg-deb -c /var/cache/apt/archives/gimp_2.8.6-1ubuntu1_i386.deb | awk 'NR==1 {print "/."; next}; {sub("^.","",$6); sub("/$","",$6); print $6}' > gimp.list
```

3. if that works without errors, then move the generated file in place of the broken one

```
sudo mv gimp.list /var/lib/dpkg/info/gimp.list
```

After doing that I was able to upgrade successfully - and I also ran a diff

```

$ diff -s /var/lib/dpkg/info/gimp.list /var/lib/dpkg/info/gimp.list.orig
Files /var/lib/dpkg/info/gimp.list and /var/lib/dpkg/info/gimp.list.orig are identical

```

Hope this helps

---

### Post by michaelcanlbel on 2013-12-15
*sigh* well I got through the first step, then I got this from running the second:
```

dpkg-deb: error: failed to read archive `/var/cache/apt/archives/gimp_2.8.6-1ubuntu1_i386.deb': No such file or directory

```

At this rate. considering that I don't exactly have anything of importance on my computer, Would simply wiping the hard drive be an option? (I really appreciate your help though)

---

### Post by steeldriver on 2013-12-15
Hmm... that's odd, it seemed to be there when you did the 'find' command (post #4) - have you run an 'apt-get clean' or 'apt-get autoclean' in the meantime?

It shouldn't be hard to fix this, if the deb is gone from the archive you can download another copy from packages.ubuntu.com - your call

---

### Post by michaelcanlbel on 2013-12-17
*sorry for the delayed response*
Once again, fairly new to this, somewhat confused with what you just said.
If you want some context, this is the full response from the command:
```

  dpkg-deb -c /var/cache/apt/archives/gimp_2.8.6-1ubuntu1_i386.deb | awk 'NR==1 {print "/."; next}; {sub("^.","",$6); sub("/$","",&6); print $6}' > gimp.listdpkg-deb: error: failed to read archive `/var/cache/apt/archives/gimp_2.8.6-1ubuntu1_i386.deb': No such file or directory
awk: cmd. line:1: NR==1 {print "/."; next}; {sub("^.","",$6); sub("/$","",&6); print $6}
awk: cmd. line:1:                                                         ^ syntax error
awk: cmd. line:1: NR==1 {print "/."; next}; {sub("^.","",$6); sub("/$","",&6); print $6}
awk: cmd. line:1:                                                           ^ 0 is invalid as number of arguments for sub


```
I Preformed the command, Tried an autoclean/clean then tried it again, same response.

---

### Post by steeldriver on 2013-12-17
If you've run a clean/autoclean then the deb will be gone from the archive, I think. It looks like the gimp_2.8.6-1ubuntu1_i386.deb file is no longer available (having been superseded by a security update gimp_2.8.6-1ubuntu1**.1**_i386.deb, which I think we saw in your /var/cache/apt/archive)

You can download it from [http://packages.ubuntu.com/saucy/i386/gimp/download](http://packages.ubuntu.com/saucy/i386/gimp/download) or use wget in a terminal (which will download it to the current directory)

```
wget http://security.ubuntu.com/ubuntu/pool/main/g/gimp/gimp_2.8.6-1ubuntu1.1_i386.deb
```

You can check the MD5 sum if you like but we are not going to install any of the files it contains, just generate a new 'fileslist file' from it. If you used wget, then in the same directory you can just do

```

dpkg-deb -c gimp_2.8.6-1ubuntu1.1_i386.deb | 
awk 'NR==1 {print "/."; next}; {sub("^.","",$6); sub("/$","",$6); print $6}' > gimp.list

```

(I've split it on two lines to make it easier to read - it shouldn't matter whether you split it or put it on one long line - I suggest you copy and paste it though because you made a couple of typos e.g. **&**6 instead of **$**6)

---

### Post by michaelcanlbel on 2013-12-17
..... I was not previously aware that it was possible to simply copy and paste commands into the terminal instead of typing them out... *Facepalm*
Anyways, I have ran all commands that you suggested I try and they all worked with out errors.
 Also, I ran apt-get update, upgrade, and autoclean, and they also all went through without errors.
It seems that this has solved the problem so far (chances are I'll report if any other errors occur) and considering that this is the first major problem I've come across while using ubuntu, I can't thank you enough for helping me fix it.

Cheers

---

### Post by steeldriver on 2013-12-17
Happy to help - I hope it turns out to be a permanent fix, but do post back if you experience further issues

---

### Post by michaelcanlbel on 2013-12-18
Well victory was short lived I guess.
My computer still shuts down when I put even a bit of strain on the graphics card (watching a video, playing a game etc).
It only started happening after I updated to Ubuntu/Xubuntu 13.10 but I really can't figure out what's been causing this problem.

---

### Post by philinux on 2013-12-18
> **michaelcanlbel said:**
> Well victory was short lived I guess.
My computer still shuts down when I put even a bit of strain on the graphics card (watching a video, playing a game etc).
It only started happening after I updated to Ubuntu/Xubuntu 13.10 but I really can't figure out what's been causing this problem.

i would start a new thread "Computer shuts down ...... whatever title you think appropriate".

Include spec of the machine and graphics card. And are you sure temperature is not an issue?

---

### Post by michaelcanlbel on 2013-12-18
Ok, and no, I'd say I have appropriate cooling. 2 fans and 1 side panel is removed, It's also in a fairly open space.

---

