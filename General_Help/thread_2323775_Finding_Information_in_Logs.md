---
title: "Finding Information in Logs"
date: 2016-05-08
forum: General Help
---

### Post by peter228 on 2016-05-08
There are many log files to be found at /var/log and those logs tend to be in huge detail and difficult to understand.

I am trying to understand an event I have noticed and wonder if anyone has any suggestions?

I have noticed that between Grub loading and the Ubuntu splash screen appearing there are some apparent error messages.  They list for a second and then go away.  It looks like they say something like Recovering Journal Clean ... but who knows, there are many lines and it is really fast.

Also when the system shuts down there are perhaps ten lines that also sometimes appear and disappear in about a second.  They mention something about Cleaning Orphaned but I cannot read more.

Since the system works I am not hugely concerned but since I have never seen this happen in previous Ubuntu releases I wonder if I should explore a bit.

I have tried to learn more using tools like dmesg | tail and journalctl to look at the syslog but nothing leaps out as a problem.  What is the best way of finding these messages?


I also experience random system failures.   With Ubuntu 14.04 this happened every few days.  Now with 16.04 the failure still happens but it is a longer interval.   The system totally crashes and reboots. No warning and it can be with any program running although Thunderbird is common to all events.  What tool should I use to try and figure out what happened there?

---

### Post by TheFu on 2016-05-08
use grep.
[http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files](http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files)

Little issues tend to grow into bigger issues. For the last few months, there were errors in my logs related to ATA stuff.  Last week, the system failed to boot.  Traced it back to a lose SATA cable. All that time, the system ran slower because all the error correction that was necessary.

Install **logwatch** and get daily summaries. Address any warnings or errors ASAP.  Sometimes, especially for GUI programs, it isn't possible to do anything.  I see font errors with Thunderbird all the time - that and notification errors (because I don't run any notification daemons).

---

### Post by peter228 on 2016-05-08
nice suggestion but a few problems .... 

the linked command showed use of egrep.  Well that will not run since egrep is not installed.  It is not in the repositories.  So I edited the command down to use grep and it still would not run ..

The 'Ubuntu Software' suggested to use glogg instead,  Whilst that would install it will not run .... 

logwatch sounds to be very interesting from the support page but it is server software and not found in the repositories.

---

### Post by steeldriver on 2016-05-08
egrep is just a (mildly deprecated) synonym for grep -E, it should be provided on Ubuntu 14.04 by the standard grep package:

```

$ dpkg -L grep | grep 'bin'
/bin
/bin/grep
/bin/egrep
/bin/fgrep
/usr/bin
/usr/bin/rgrep

```

If for some reason it's not on your system you can use plain grep and add the -E (or --extended-regexp) command line switch

---

### Post by TheFu on 2016-05-08
I use egrep because I like extended regex and saving 2 extra characters - I'm lazy.
Never heard of glogg.
I install logwatch on every box I have, period. Never had to add any repos, that I can recall.
```
$ dpkg -l |grep logwatch
ii  logwatch          7.4.0+svn20130529rev144-1ubuntu1      all      log analyser with nice output written in Perl

```
Logwatch is purely for convenience. You can make your own with a small script that greps through all the log file entries for the last 24 hrs.

How you look at the log files is your business.  Just showing how I do it, but I've only be a Unix admin since '93 and still have much to learn. There is always someone smarter or doing it better than me.

A few other log links ... (web search using "log files ubuntu")
* [https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)
* [http://askubuntu.com/questions/186276/where-are-all-the-major-log-files-located](http://askubuntu.com/questions/186276/where-are-all-the-major-log-files-located)

Any issues in the logs?

---

### Post by peter228 on 2016-05-09
thank you for your response.  The links at the end are also very interesting.

glogg is found here
[https://apps.ubuntu.com/cat/applications/precise/glogg/](https://apps.ubuntu.com/cat/applications/precise/glogg/)
I was able to install but it hanged when I opened it.   One of those teething 16.04 problems I guess ... 

I ran your command and did a 
which logwatch
but no path was returned so I guess it is not there.

I need a bit of time to figure this out ...  egrep and grep -E are apparently deprecated so I need to do a bit more reading.

One general thing that sort of dawns on me though is that there is a huge amount of information available in the log files and something like 99.5% of users overlook these since they are difficult to read through and difficult to find errors.   If there was something more user friendly I think a lot more people would be able to get better control of their systems and see problems before they become a headache.

---

### Post by TheFu on 2016-05-09
Don't fight Unix.  Embrace it and the methods is uses.  grep, egrep, grep -E ... are closely related. grep -E isn't going anywhere. It is too powerful.
If that command isn't working for you, post the **exact** command and all the output so we can help.  Without it, we can't help at all.  That is also why I much prefer CLI/shell commands over any GUI.  copy/paste is easy. taking a screen capture, finding a place to post it, providing a link back here - that's a hassle.

If you are just getting started with Linux, my best advice for learning is here: [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux)  Learning in an organized way will help recognize bad advice, teach skills that are dependent on previous learning, and not waste your time.  

Start with the essentials 
* how Linux is different from Windows, but similar.
* how the Linux _culture_ is different from all other OSes, which will avoid frustration because the Linux community has expectations for YOUR effort to learning and solving issues.

Start Thinking the Unix way (Linux is Unix BTW)
* Solving problems with Unix is very different than the Windows way. Thinking differently is required.
* a GUI is not usually the most efficient way to solve problems and usually prevents automation.  I get an email from each of my systems with the important information from log files daily.  I don't have to look for it. I don't have to login to each system (though that is trivial too). I don't have to egrep looking for only the relevant parts. The important answers, and no more, are provided to me, in an email, daily. Takes 3-5 sec to scan that output and I get a feel for how each system behaves.

Start Learning all the tiny little commands that, when put together, make Unix extremely flexible to solve any problem.  Most importantly, to automate that solution, so the answers are provided to you and you don't have to wait.  That is what logwatch is about. Logwatch isn't pre-installed, so ... 

[B]sudo apt-get install logwatch
[/B]
Then there is a little setup needed. It likes/needs/requires an MTA to send email. This is needed for most Unix systems - it is the Unix way. That is the hardest part - setting up an MTA to be allowed to email your normal email account. My MTA setup is configured the way that businesses do it, not the way that home users do it, so I cannot really help with that. For outbound-only email, ssmtp is probably the easiest answer (but I don't know - never used it).

---

### Post by steeldriver on 2016-05-09
I have no idea why you would believe that grep -E is deprecated - as explained on the man page

```

       In  addition,  three  variant  programs  egrep,  fgrep  and  rgrep  are
       available.   egrep  is  the  same  as  grep -E.   fgrep  is the same as
       grep -F.  rgrep is the same as grep -r.  Direct  invocation  as  either
       egrep  or  fgrep  is  deprecated,  but  is provided to allow historical
       applications that rely on them to run unmodified.

```

Also

```

       grep understands three different versions of regular expression syntax:
       “basic” (BRE), “extended” (ERE) and “perl” (PRCE). [B]In  GNU grep,  there
       is  no difference in available functionality between basic and extended
       syntaxes.[/B]

```

For simple queries it doesn't really matter whether you use basic or extended expression syntax since literal strings are identical either way e.g.

```

$ grep -i 'error' /var/log/{syslog,dmesg,kern.log}
/var/log/syslog:May  9 07:00:11 T61p kernel: [69599.401457] ata3: SError: { PHYRdyChg 10B8B }
/var/log/syslog:May  9 07:23:58 T61p kernel: [71026.201908] ata3: SError: { PHYRdyChg 10B8B }
/var/log/dmesg:[    1.688211] tpm_tis 00:09: A TPM error (6) occurred attempting to read a pcr value
/var/log/dmesg:[    3.003854] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:May  9 07:00:11 T61p kernel: [69599.401457] ata3: SError: { PHYRdyChg 10B8B }
/var/log/kern.log:May  9 07:23:58 T61p kernel: [71026.201908] ata3: SError: { PHYRdyChg 10B8B }

```

If you want help formulating a grep search then you will need to be more specific about what you're looking for - you can upload your log files somewhere (such as pastebin) if you wish

---

### Post by TheFu on 2016-05-09
I read about a year ago that egrep was being phased out (don't know why, it just takes an inode).

```
$ grep -iE 'error|warning' /var/log/{syslog,dmesg,kern.log}
/var/log/dmesg:[    2.086340] [drm:qxl_pci_probe] *ERROR* qxl too old, doesn't support client_monitors_config, use xf86-video-qxl in user mode
/var/log/dmesg:[    2.087242] qxl: probe of 0000:00:02.0 failed with error -22
/var/log/dmesg:[   12.921657] EXT4-fs (vda1): re-mounted. Opts: errors=remount-ro

```
Just QXL video driver issues in mine. Meh. Doesn't matter, since I'm not using QXL video. Could clean that up by removing the drivers in the VM settings. Not a big deal.
On another machine, 
```
$ grep -Ei 'error|warning' /var/log/{syslog,dmesg,kern.log}
/var/log/syslog:May  9 08:50:15 hadar kernel: [117004.837763] mce: [Hardware Error]: Machine check events logged
/var/log/dmesg:[    5.989181] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
/var/log/dmesg:[    7.571009] ACPI Warning: 0x0000000000000828-0x000000000000082f SystemIO conflicts with Region \PMRG 1 (20131115/utaddress-251)
/var/log/kern.log:May  9 08:50:15 hadar kernel: [117004.837763] mce: [Hardware Error]: Machine check events logged

```
Ah ... the machine check events. Those are due to over heating issues with that box. The CPUs automatically slow down for a few minutes.  I can't fix the cooling issue - it is a small, custom, case with specialized cooling already from the manufacturer. The MB is custom and won't fit into any other cases.  The ACPI issue is due to my bridge setup in support of virtualization.  

Without the -E, it don't work. Extended regex is a thing of beauty, even for something this simple.

BTW, that ata3 error could be a loose SATA cable - unless you hot-plugged it. ;)

---

### Post by steeldriver on 2016-05-09
@TheFu without -E, the | is treated literally - in BRE you just need to escape it i.e.

```

grep -i 'error\|warning' /var/log/{syslog,dmesg,kern.log}

```

Same goes for + (ERE) versus \+ (BRE)

As noted in the manpage, the capabilities are the same in GNU grep's BRE and ERE, you just need to escape things differently

---

### Post by TheFu on 2016-05-09
> **peter228 said:**
>  
the linked command showed use of egrep.  Well that will not run since egrep is not installed.  It is not in the repositories.  So I edited the command down to use grep and it still would not run ..

Please post the exact command with the output so we can help. Some blog software changes characters to make things more readable, but that breaks copy/paste.  If you copy/pasted, check for `'" character mistakes, for example.

---

### Post by peter228 on 2016-05-10
I think for me this has been a useful exercise so far.  

I have found quite a lot of errors.  Most (634 of them) were caused by an inappropriate file extension from the distant past.  Actually no big deal because they relate to data on a separate partition but ... now fixed that.

But I have still got lots of things to explore,  everything from  weather indicator errors to desktop gnome session to pulse audio to variety ...  Lots of fun I guess .. well really it will take time with google to see what is worth exploring.

Nothing about the original messages though.  This morning on boot I saw one of them appear for a longer time.   It was on two lines, "/dev/sda1 recovering journal" and "clean blocks".   Now I have a clearer idea what that is.

The other thing I will need to do is to get the log rotation program working or I will otherwise drown in detail.

---

### Post by TheFu on 2016-05-10
Excellent!  Happy to have helped.

BTW, file extensions generally do not mean a thing in Unix/Linux.  It is the permissions that matter, unless a specific program is written to look for a specific extension.  For example, since 2.4, Apache has required configuration files to end in .conf, but that is a relatively new change.  Extensions are generally more for humans than the computer.  The computer uses the "magic number" - basically this is the file header (first few lines) to determine the file contents.  Use the 'file' command to see.  
```
$ file /bin/*grep
```
Some interesting results with that. ;)

Unix knowledge is like the ocean.  Some things are exactly as they seem on the surface and other things require diving 29Kft, deep, into a crevice to learn. The vast majority of interesting things happens in the first 100ft, however.

---

