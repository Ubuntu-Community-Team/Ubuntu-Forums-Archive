---
title: "3 mins. booting, someone help me figure out what's wrong."
date: 2008-01-27
forum: General Help
---

### Post by Fireblend on 2008-01-27
Hey, so today, for some reason my computer has decided to take more than 3 minutes booting. My first suspicion is the HD is starting to fail, mainly because of the horrible noise that it does when booting, but well, it's been happening for a while and until now it hadn't effected the booting process. I've got bootchart, so I took a look at it, but I have no idea how to interpret these, so would anyone kindly tell me what's making my computer boot so slowly?

Here's the chart:
[http://i32.tinypic.com/x5s3a0.png](http://i32.tinypic.com/x5s3a0.png)

Thanks in advance.

---

### Post by Lord Illidan on 2008-01-27
That boot chart is way too tiny. I can't read any text properly, however, by zooming in, I think it was fsck doing a file system check. How long have you been using Ubuntu? This should take place periodically, every 30 boots or so.

---

### Post by steveneddy on 2008-01-27
Please repost the bootchart image to the forums directly. It is too small to read.

Are you on 32 or 64 bit Ubuntu.

Gnome or KDE?

---

### Post by Fireblend on 2008-01-27
Huh sorry, didn't check after uploading. Wonder why it got resized like that. Here it is, I'll attach it.

I've been using Ubuntu for about a year now. It's just that there was no "now checking" screen, just a blank screen with the blinking input....

Using Ubuntu 7.10, 32 bits.

---

### Post by articpenguin on 2008-01-28
its fsck.ext3. Fsck runs every 30 mounts if it does this every mount then there is something wrong with the filesysem.

---

### Post by gwpritch on 2008-01-28
You say you have just a blank screen...ie no boot splash...the ubuntu bar? If this is the case, try:

```
sudo gedit /etc/usplash.conf
```

Make sure the x and y resolutions are appropriate for your monitor.

eg
```
# Usplash configuration file
xres=1024
yres=768
```

reboot.

I had a similar problem with a long boot and no usplash. When I changed the res, everything sped up nicely.

---

