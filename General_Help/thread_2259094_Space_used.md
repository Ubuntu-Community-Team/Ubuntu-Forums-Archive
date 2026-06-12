---
title: "Space used"
date: 2015-01-01
forum: General Help
---

### Post by davidafranklin on 2015-01-01
Hello,

I have a 72 GB drive with Lubuntu 14.10 installed. I only installed a few additional softwares like Teamviewer, Bleach, Gparted and Chromium.
However, when I look at the space I have available, I only have 45 GB.I cannot see where almost 30 Gb are being used.
I have downloaded Baobab Disk Space Analyzer but I can only see the used space (my 45 GB).
I used bleach to see if some obsolete files were taking space but this releases only a few hundred MB at best.
I checked with Gparted if there was some disk space not being used and there is not. The entire drive is for Lubuntu.

Any suggestion on how to find out here my space is being used?

Thanks

Edit: Something worth mentioning, I had upgraded my Lubuntu from version 14.04. Maybe there are some files liked to 14.04 that can be deleted. I just have no idea where there would be if this is the case.

---

### Post by yancek on 2015-01-01
Did you upgrade from 14.04 to 14.10 or install?  Do you have both installed maybe?    You can see the partitions, their size and the percentage of space used on each mounted partition with the command:  df -h

You can use the find command to find large files, some examples at the link below:

[http://www.cyberciti.biz/faq/find-large-files-linux/](http://www.cyberciti.biz/faq/find-large-files-linux/)

---

### Post by davidafranklin on 2015-01-01
I upgraded from 14.04 to 14.10.

```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        73G   58G   12G  84% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            927M  4.0K  927M   1% /dev
tmpfs           188M  1.2M  187M   1% /run
none            5.0M  4.0K  5.0M   1% /run/lock
none            938M   14M  924M   2% /run/shm
none            100M   28K  100M   1% /run/user
```

I have removed lots of files so I free up 12 GB. I have 34GB being used for my personal files. Free space is 12 GB. So total only equal to 48 GB. 25 GB cannot be for Lubuntu 14.10 alone and a few softwares.

---

### Post by schragge on 2015-01-01
Check if something spams your logs in /var/log:
```
du -sh /var/log
```
and how many old kernels you have installed:
```
ls /boot/vmlinuz*
```

---

### Post by davidafranklin on 2015-01-01
not sure, result is:
du: cannot read directory &#8216;/var/log/samba/cores&#8217;: Permission denied
3.3M	/var/log

---

### Post by schragge on 2015-01-01
aha. Now, try the same with sudo:
```
sudo du -sh /var/log
```

---

### Post by davidafranklin on 2015-01-01
it just gives me:
3.3M	/var/log

When I type [COLOR=#000000][FONT=Ubuntu Mono]ls /boot/vmlinuz*
I get:
[/FONT][/COLOR]/boot/vmlinuz-3.16.0-28-generic


[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]

---

### Post by schragge on 2015-01-01
Ok, still nothing, now let's try it like this
```
sudo du -sh /var/{backups,cache,crash,mail,spool,tmp}
```

---

### Post by davidafranklin on 2015-01-01
does not seem much. I get:
3.8M	/var/backups
159M	/var/cache
4.1M	/var/crash
4.0K	/var/mail
44K	/var/spool
4.0K	/var/tmp

---

### Post by schragge on 2015-01-01
Hmm, really strange then. Ok. Let's try
```
sudo du -cxhd1 /
```
This one will take some time.

---

### Post by davidafranklin on 2015-01-01
Interesting. It is still running but we might have found the issue. The trash in "Places" is empty but shows here 20Gb

So far:

12M	/sbin
35G	/home
20G	/.Trash-0
256M	/opt
1.6G	/usr
11M	/bin
32K	/tmp
8.0K	/srv

after about 20 mn, nothing more to [COLOR=#000000][FONT=Ubuntu Mono]sudo du -cxhd1 /.

[/FONT][/COLOR]The trash is the issue. cannot dete it (cannot acess it)

---

### Post by schragge on 2015-01-02
You definitely can access it as root, otherwise the previous command (du -cxhd1 /) would complain about it. Try
```
sudo ls -l /.Trash-0
``` If there is nothing of value, you can delete it with ```
sudo rm -r /.Trash-0
```

---

### Post by mörgæs on 2015-01-02
Davidafranklin, please use CODE tags when posting terminal output. I have edited post #2.

---

### Post by davidafranklin on 2015-01-02
> **schragge said:**
> You definitely can access it as root, otherwise the previous command (du -cxhd1 /) would complain about it. Try
```
sudo ls -l /.Trash-0
``` If there is nothing of value, you can delete it with ```
sudo rm -r /.Trash-0
```



This finally worked I now have an extra 20 Gb. Thanks a lot. Is there  way to prevent this from happening?

> **mörgæs said:**
> Davidafranklin, please use CODE tags when posting terminal output. I have edited post #2.

Sure, no problem.

---

### Post by yancek on 2015-01-02
> This finally worked I now have an extra 20 Gb. Thanks a lot. Is there  way to prevent this from happening?


Yes.  If you select the option to send to Trash it is still on the drive just in another location.  When you Delete, it's deleted.

---

### Post by pfeiffep on 2015-01-02
> **davidafranklin said:**
> This finally worked I now have an extra 20 Gb. Thanks a lot. Is there  way to prevent this from happening?

Sure, no problem. If by 'Bleach' you installed BleachBit there's an option to empty trash.

---

### Post by davidafranklin on 2015-01-02
> **pfeiffep said:**
> If by 'Bleach' you installed BleachBit there's an option to empty trash.

yes, ok. tks

---

