---
title: "Apport reports error after editing /etc/default/grub"
date: 2016-09-27
forum: General Help
---

### Post by Ralph L on 2016-09-27
I edited /etc/default/grub to change the scheduler to cfq.  I changed the line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" elevator=cfq
After that apport reports an error on each startup.  I had saved the original file, so I reverted to it.  apport still gives an error.  Does anybody know what triggers apport to report errrors???  I see on the web that a lot of people just disable all its error reporting, but I would like to know about errors and fix them.
I am running a recently installed xubuntu 16.04.01 that was updated today.

---

### Post by cariboo on 2016-09-27
When a crash occurs, a crash report is created in /var/crash eg:

```
/var/crash$ ls -l
total 53320
-rw-r----- 1 cariboo  whoopsie  5112843 Sep 26 19:29 _usr_bin_compiz.1000.crash
-rw-r--r-- 1 cariboo  whoopsie        0 Sep 26 19:29 _usr_bin_compiz.1000.upload
-rw------- 1 whoopsie whoopsie        0 Sep 26 19:29 _usr_bin_compiz.1000.uploaded
-rw-r----- 1 cariboo  whoopsie  9921686 Sep 24 14:03 _usr_bin_qbittorrent.1000.crash
-rw-r----- 1 cariboo  whoopsie 39558740 Sep 24 14:02 _usr_bin_vlc.1000.crash
```

the files with the .uploaded extension have been uploaded to [https://errors.ubuntu.com/](https://errors.ubuntu.com/)
to stop seeing the messages, just delete all files in /var/crash.

---

### Post by deadflowr on 2016-09-27
Any generated reported is in /var/crash.
Clicking on any of said reports will open the crash report utility and allow you to read the crash report and report it to the developers.

You may also want to look to see if something is buggy with apport by viewing any apport logs in /var/log.

Ninja'd cuz I'm slowwww.

---

### Post by Bucky Ball on 2016-09-28
You have this:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" elevator=cfq
```

'elevator=cfq' is supposed to be inside the quotation marks I'd say. The dangling bit outside the quotations is probably what causing the glitch.

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash elevator=cfq"
```

What outcome adding that option has is another story of course ... :)

---

### Post by Ralph L on 2016-09-29
Thanks for the responses!!
Bucky BAll:  I found instructions for changing the scheduler to cfq at this web site:  [http://www.hecticgeek.com/2014/10/change-disk-i-0-scheduler-cfq-ubuntu-14-10/](http://www.hecticgeek.com/2014/10/change-disk-i-0-scheduler-cfq-ubuntu-14-10/) .  You are correct. It specifies that 'elevator=cfq' should be inside the double quotes.  Also I did ```
cat /sys/block/sda/queue/scheduler
noop [deadline] cfq 

``` which I believe shows that the scheduler was changed from deadline to cfq (Complete Fairness Queueing).  Whether it makes my computer more responsive is another question.  Some people claim cfq is better, when running from hard disks, and that deadline scheduling is more responsive, when running from SSD.  I really don't understand either, but I am using an old computer with, by today's standards, a slow cpu.  I am going to try cfq and see if I notice better responsiveness.

---

