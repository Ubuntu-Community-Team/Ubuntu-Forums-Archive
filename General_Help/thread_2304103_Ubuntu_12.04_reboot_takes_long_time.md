---
title: "Ubuntu 12.04 reboot takes long time"
date: 2015-11-24
forum: General Help
---

### Post by meuser1 on 2015-11-24
Hi
I am facing issue when trying to reboot my dell laptop loaded with Ubuntu 12.04. On hard boot I am seeing below message and it takes very long time (more than 90 min) to boot
resume: libgcrypt version : 1.5.0
Looking for splash system ... none
Cannot open input directory: No such file or directory
resume: Compressed image
Loading image data pages (314960 pages) .... 7% -----> this goes forever, for each percentage change it takes not less than 5 to 10 minutes.

Any idea how to resolve this issue

Thanks a lot in advance

---

### Post by matt_symes on 2015-11-24
Hi

You have an encrypted drive ?

```
resume: Compressed image
```

This looks like it could be a hibernation image. Are you sure it's not hibernating ?

Kind regards

---

### Post by meuser1 on 2015-11-24
Hi
Yes I am also using hibernating. Is that the problem. If so how to resolve this.

Thanks

---

### Post by matt_symes on 2015-11-24
Hi

Is the drive encrypted ? Is your home partition encrypted ? Is your swap partition encrypted ?

You have re-enabled the hibernation option in 12.04 ? I thought it was hidden from the menu. How have you been hibernating ?

You can get rid of the hibernation image from easy enough but it sounds like you don't want to do that.

Can we get some basic stats. Open a terminal and post the output of these commands into your next post.

```
free -m
```

```
swapon -s
```

```
echo $(($(cat /sys/power/image_size) / (1024 * 1024)))
```

```
cat /proc/cpuinfo
```

It may be taking time to uncompress the image but it does seem like it's taking too long from your description.

```
cat /var/log/pm-suspend.log 
```

This log file may be large so if you could trim it down to your last resume, that would be useful.

**EDIT:**

Can you also post the output of this command.

```
dpkg -l uswsusp
```

Kind regards

---

