---
title: "Ubuntu13.11 packaged as Ubuntu12.04?"
date: 2014-03-10
forum: General Help
---

### Post by newbie2244 on 2014-03-10
Why do I see Ubuntu 13.11 in GRUB when I downloaded 12.04LTS? My login screen has 12.04LTS at the bottom. 
  I have n HP Pavilion quad core A8. Other problems also. But I do have a functioning dual boot system - w/ Ubuntu the default OS. 
  BIOS fn F9 shows Toshiba was the source mirror.:confused:

---

### Post by varunendra on 2014-03-10
Welcome to Ubuntu Forums newbie2244! :)

Are you sure it is "**13**.11"? I think it should be like this -
> Ubuntu, with **Linux 3.11.**...
Where 3.11... is the "Kernel" version, not the version of Ubuntu. There is no version called Ubuntu 13.11

Ubuntu is released each year in April (month 04), and October (10). The version number indicates the "Year.Month" of release. As such, there is 12.04, 12.10, 13.04, 13.10. The release after 13.10 will be numbered 14.04 (Year 20**14**, month 04).

The kernel (the 'Engine' upon which the OS is build) is upgraded very frequently. The latest point release of 12.04 (12.04.4) comes with kernel **3.11 **by default. I think that is what you are seeing.

Hope it helps. :)

---

### Post by newbie2244 on 2014-03-10
Why do I see Ubuntu 13.11 in GRUB when I downloaded 12.04LTS? My login screen has 12.04LTS at the bottom. I have n HP Pavilion quad core A8. Other problems also. But I do have a functioning dual boot system - w/ Ubuntu the default OS. BIOS fn F9 shows Toshiba was the source mirror.

---

### Post by raja.genupula on 2014-03-10
An Image may help us a lot !!
Thank you.

---

### Post by grahammechanical on 2014-03-10
I think that you are misunderstanding what you are seeing in the Grub menu. For a start we do not have a Ubuntu 13.11. We have Ubuntu 12.04, 12.10, 13.04, 13.10 and soon we will have Ubuntu 14.04.

What you are seeing is a Linux kernel version number. I am running Trusty Tahr (14.04 under development ) and this Ubuntu has Linux kernel 3.13 or 3.13.0-16-generic to be specific. Two commands for you to run:

```
lsb_release -a
uname -a
```

It may not make things clearer but it may prove to you that you are not running Ubuntu 13.11 but Ubuntu 12.04 Precise. This is what those two commands show me:

> No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Trusty Tahr (development branch)
Release:    14.04
Codename:    trusty
> 
Linux 3.13.0-16-generic #36-Ubuntu SMP Tue Mar 4 23:02:40 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Regards.

---

### Post by newbie2244 on 2014-03-10
Thank-you all. After the first post to my ?, i went back to check the GRUB listing. Got a magnifying glass and I did misread it. - In fact it is 3.11. Grub listing is in very fine print and very long.  I have a working? dual boot system since yesterday but I'm still finding my way around. Hence the name newbie2244. Thank-you all.

---

### Post by raja.genupula on 2014-03-10
ok please mark the thread as solved from thread tools.

---

### Post by newbie2244 on 2014-03-10
Thank-you ...After reading your post I got a magnifying glass and restarted and you were of course right. My grub listing is in very fine print and very long. And although I managed to get a ?working dual boot system since yesterday, I am still finding my way through it. Hence the name newbie2244.  Thank-you again.

---

### Post by varunendra on 2014-03-10
You're welcome! :)

Please mark the thread as [SOLVED] using the "Thread Tools" link above the top post.

---

### Post by bapoumba on 2014-03-10
Threads merged.

---

