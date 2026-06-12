---
title: "Suddenly File System Errors"
date: 2014-05-08
forum: General Help
---

### Post by Kurushimi on 2014-05-08
So last night as I was about to go to bed, I tried to save the file I was working on but the computer refused because it said the folder I was saving to was read only. This didn't make any sense because I had saved it to that location just a few minutes earlier. I tried to open firefox to see if I could look up the cause of this error but firefox reported that it was still running, even though I had just closed it and there were no copies of it running. I tried shutting down my computer and starting it again, but when I do, the computer halts at a black screen (before it even displays the ubuntu logo with the loading bar).  I have no idea what the problem could be or how I could have caused it, since the computer worked absolutely fine recently (I had some problems a while back, but haven't had any problems at all for months). 

What could the problem be, and what could I do to fix it?

---

### Post by sandyd on 2014-05-08
It may be that your hard disk has issues.

Have you tried booting into recovery mode and checking the disk from there?

---

### Post by pfeiffep on 2014-05-08
Like sandyd suggested boot into recovery mode - access it by holding shift key down on boot so grub presents the option

---

### Post by tgalati4 on 2014-05-08
Boot to Rescue Shell--a root command line:

```
smartctl -a /dev/sda
```

During boot up you will be asked to "fix errors", reply yes and hope that your disk comes back.  Otherwise, dig out a an Ubuntu USB stick or DVD and use that to boot from in the future until you diagnose your disk issue.  Although rare, a disk failure while you are working happens and causes such symptoms.  Normally  you would use a USB stick to save your data if the hard disk doesn't respond.  Shutting down the computer means you probably lost some work--any open files that didn't get saved properly.

What were the problems that you had earlier?  Perhaps your disk has been failing for a while and you didn't realize it.

---

### Post by Kurushimi on 2014-05-16
I don't know how to boot to rescue shell. Is that what this calls recovery mode?

I tried booting to recovery mode but as its loading it begins to print the error "timeout: killing sbin/modprobe/ ..." followed by a really long string of numbers and some letters. It prints this over and over. Recovery mode starts anyways, but this keeps getting printed over everything. I didn't know what option to select from there so I just hit resume normal boot and as it was going it asked if I wanted to fix file system errors. I said I did and after printing some stuff about fixing "orphaned inodes" it rebooted and the system ran normally. But only for a day or two, and then I had to do it again. And then again. 

I remember I tried running the option for checking the disk in recovery mode but I can't remember what it said. I'll do that again now and see.

Edit: 
Yeah, I remember now. When I ran fsck in recovery mode it just told me there were three files in the folder /sda/something and how much space they took. And then it said it was done and to click enter. 

Also, I don't know what the cause of the problems were from before. While I was running windows the computer suddenly couldn't start up. I don't even remember the details but I couldn't use the computer. I didn't know how to fix it and felt that it would just be easiest to reinstall the OS and chose ubuntu since that was easy to obtain.

---

### Post by tgalati4 on 2014-05-16
Sounds like classic hard disk failure.  Find a new disk and recover your personal files as soon as possible.

---

### Post by Kurushimi on 2014-05-16
What do you think I might have done to cause a hard disk failure? This laptop is less than a year old.

---

