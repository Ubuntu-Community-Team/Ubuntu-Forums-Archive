---
title: "Grub problems"
date: 2013-03-01
forum: General Help
---

### Post by sanderj on 2013-03-01
> **bodhi.zazen said:**
> A fix has already been released.

[http://www.ubuntu.com/usn/usn-1750-1/](http://www.ubuntu.com/usn/usn-1750-1/)

[http://www.ubuntu.com/usn/usn-1751-1/](http://www.ubuntu.com/usn/usn-1751-1/)

[http://www.ubuntu.com/usn/usn-1749-1/](http://www.ubuntu.com/usn/usn-1749-1/)

[http://people.canonical.com/~ubuntu-security/cve/2013/CVE-2013-1763.html](http://people.canonical.com/~ubuntu-security/cve/2013/CVE-2013-1763.html)

Linux is not Windows and in general patches are released much faster.

You may wish to bookmark this page - [http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

In the future, it is worth searching that page for security bugs and fixes ;)


So kernel needs to be linux-image-3.5.0-25. Mine is 3.5.0-21. System is fully updated, and "import security updates" is checked. System's uptime is 1 day (so not a week or so).

Why don't I get the newer kernel?

---

### Post by sanderj on 2013-03-01
Strange: there is a lot of 3.5.0-25 stuff in /var/log/*. So why is it not activated on boot? It's not in the GRUB menu... :(

```
sander@R540:/var/log$ grep -i 3.5.0-25 * | grep -i generic | head -5
dpkg.log.1:2013-02-22 17:12:35 install linux-image-3.5.0-25-generic:amd64 <none> 3.5.0-25.38
dpkg.log.1:2013-02-22 17:12:35 status half-installed linux-image-3.5.0-25-generic:amd64 3.5.0-25.38
dpkg.log.1:2013-02-22 17:12:38 status unpacked linux-image-3.5.0-25-generic:amd64 3.5.0-25.38
dpkg.log.1:2013-02-22 17:12:38 status unpacked linux-image-3.5.0-25-generic:amd64 3.5.0-25.38
dpkg.log.1:2013-02-22 17:13:03 install linux-image-extra-3.5.0-25-generic:amd64 <none> 3.5.0-25.38
```

A manual update-grub2 does see the 3.5.0-25 kernel, but it's not in the actual GRUB menu list at boot.

Tips?

```

sander@R540:~$ sudo update-grub2
[sudo] password for sander: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-25-generic
Found initrd image: /boot/initrd.img-3.5.0-25-generic
Found linux image: /boot/vmlinuz-3.5.0-24-generic
Found initrd image: /boot/initrd.img-3.5.0-24-generic
Found linux image: /boot/vmlinuz-3.5.0-23-generic
Found initrd image: /boot/initrd.img-3.5.0-23-generic
Found linux image: /boot/vmlinuz-3.5.0-22-generic
Found initrd image: /boot/initrd.img-3.5.0-22-generic
Found linux image: /boot/vmlinuz-3.5.0-21-generic
Found initrd image: /boot/initrd.img-3.5.0-21-generic
Found linux image: /boot/vmlinuz-3.5.0-19-generic
Found initrd image: /boot/initrd.img-3.5.0-19-generic
Found linux image: /boot/vmlinuz-3.5.0-18-generic
Found initrd image: /boot/initrd.img-3.5.0-18-generic
Found linux image: /boot/vmlinuz-3.5.0-17-generic
Found initrd image: /boot/initrd.img-3.5.0-17-generic
Found linux image: /boot/vmlinuz-3.2.0-32-generic
Found initrd image: /boot/initrd.img-3.2.0-32-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Recovery Environment (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
Found Ubuntu 12.04.1 LTS (12.04) on /dev/sda5
done
sander@R540:~$ 

```

[IMG]http://d3j5vwomefv46c.cloudfront.net/photos/large/738712991.jpg?key=32642448&Expires=1362162732&Key-Pair-Id=APKAIYVGSUJFNRFZBBTA&Signature=hHPUm~SkRVX~4C193YkeI1jGU-70alEoTOLts7DjtqDtw8mn56rBUYwgsfhezAW8PPLlV6MONCQ6FzBw3XG871N8MDqsH9mG2aXtamnI4qd~-AVvkpI190S4lID7g32NOpt5Sh62235T~-StH8N4w0nKdOt8i07AluLzzzoNcUc_[/IMG]

---

### Post by ptn107 on 2013-03-01
```
dpkg -l | grep linux-image | awk '{print $2}'
```
from a terminal will list your installed kernels.  Is 3.5.0-25 definitely installed?

You should remove all those old ones btw.

---

### Post by sanderj on 2013-03-01
See below: it's seems to be there.

Maybe the GRUB list is too long to show the newest kernels? How do I remove old kernels from the system and/or GRUB list?

```
sander@R540:~$ dpkg -l | grep linux-image | awk '{print $2}'
linux-image-3.2.0-23-generic
linux-image-3.2.0-25-generic
linux-image-3.2.0-26-generic
linux-image-3.2.0-27-generic
linux-image-3.2.0-29-generic
linux-image-3.2.0-30-generic
linux-image-3.2.0-31-generic
linux-image-3.2.0-32-generic
linux-image-3.5.0-17-generic
linux-image-3.5.0-18-generic
linux-image-3.5.0-19-generic
linux-image-3.5.0-21-generic
linux-image-3.5.0-22-generic
linux-image-3.5.0-23-generic
linux-image-3.5.0-24-generic
linux-image-3.5.0-25-generic
linux-image-extra-3.5.0-17-generic
linux-image-extra-3.5.0-18-generic
linux-image-extra-3.5.0-19-generic
linux-image-extra-3.5.0-21-generic
linux-image-extra-3.5.0-22-generic
linux-image-extra-3.5.0-23-generic
linux-image-extra-3.5.0-24-generic
linux-image-extra-3.5.0-25-generic
linux-image-generic

sander@R540:~$ uname -a
Linux R540 3.5.0-21-generic #32-Ubuntu SMP Tue Dec 11 18:51:59 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
sander@R540:~$ 
```

---

### Post by Ms. Daisy on 2013-03-01
You canremove the old ones with synaptic package manager and search for linux generic (if my memory serves me correctly)

---

### Post by sanderj on 2013-03-01
I removed about 10 old kernels (via synaptic and/or "sudo apt-get purge linux-image-3.2.0-23-generic"), with a nice short list:

```
sander@R540:~$ dpkg -l | grep linux-image | awk '{print $2}'
linux-image-3.5.0-21-generic
linux-image-3.5.0-23-generic
linux-image-3.5.0-25-generic
linux-image-extra-3.5.0-21-generic
linux-image-extra-3.5.0-23-generic
linux-image-extra-3.5.0-25-generic
linux-image-generic
sander@R540:~$
```

 Then I ran "sudo update-grub2", also with a beautiful short list:

```

sander@R540:~$ sudo update-grub2
[sudo] password for sander: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-25-generic
Found initrd image: /boot/initrd.img-3.5.0-25-generic
Found linux image: /boot/vmlinuz-3.5.0-23-generic
Found initrd image: /boot/initrd.img-3.5.0-23-generic
Found linux image: /boot/vmlinuz-3.5.0-21-generic
Found initrd image: /boot/initrd.img-3.5.0-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Recovery Environment (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
Found Ubuntu 12.04.1 LTS (12.04) on /dev/sda5
done
sander@R540:~$ 

```

Shutdown computer, start it ... and GRUB still shows the old list with the old kernels.

[IMG]http://d3j5vwomefv46c.cloudfront.net/photos/large/738731087.jpg?key=32642448&Expires=1362167010&Key-Pair-Id=APKAIYVGSUJFNRFZBBTA&Signature=REQ7Hq4uGmCoDhDDSLptiT4e0HHY1FzLfTmcVitDTERmpXJ8LB~m895srqgLfq6WDPZfTCaQgKT6eiTQ7T72Gm0aokhzrl4QmkE0zBF~9S0NJwf2YvrfBtymQrgCpl2CCkMCNRIB8SZ26oplLFAkWjpv87nXBC~~~jQuPhdEwP8_[/IMG]

So the updates do not get into the actual GRUB list.

This is one year old laptop, one harddisk, a few partitions.

Tips how to solve this?

... in the meantime I will google "grub not updating" ...

---

### Post by sanderj on 2013-03-01
SOLVED!

```
sudo grub-install /dev/sda
```

did the trick.

The GRUB menu is now beautiful again; without ugly details. And I am now on the updated kernel:

```
sander@R540:~$ uname -a
Linux R540 3.5.0-25-generic #39-Ubuntu SMP Mon Feb 25 18:26:58 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
sander@R540:~$
```


Thank you for your help!

---

### Post by cariboo on 2013-03-01
Moved to a thread of it's own, as this really has nothing to do with the original post.

---

