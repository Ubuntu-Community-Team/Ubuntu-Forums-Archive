---
title: "Remastersys backup problem"
date: 2013-06-12
forum: General Help
---

### Post by uzumakifahim on 2013-06-12
Hi,
I'm trying to backup my system using Remastersys 2.0.12-1. There is no problem during the ISO file creation period. After creating the ISO file, I've install that on my USB drive using UNetBootin. Everything is successful, but problem ocuurs just duing boot. Boot menu appears perfectly, but when I press enter, then it shows the following message

```
Could not find ramdisk image: /ubninit
boot: 
```

I can't understand why this is happening. I've used Remastersys before, faced no issue then, but this error is happening again and again. 

Experts help me please. Need to solve this quickly.

Thanks in advance.

---

### Post by tea for one on 2013-06-12
> **uzumakifahim said:**
> Hi,
I'm trying to backup my system using Remastersys 2.0.12-1. There is no problem during the ISO file creation period. After creating the ISO file, I've install that on my USB drive using UNetBootin. Everything is successful, but problem ocuurs just duing boot. Boot menu appears perfectly, but when I press enter, then it shows the following message

```
Could not find ramdisk image: /ubninit
boot: 
```

I can't understand why this is happening. I've used Remastersys before, faced no issue then, but this error is happening again and again. 

Experts help me please. Need to solve this quickly.

Thanks in advance.

Good afternoon

Instead of using UnetBootin, why not try to create your live USB using Ubuntu's installed utility - Startup Disk Creator.

Best wishes

---

### Post by uzumakifahim on 2013-06-12
Thanks for our reply. I'll try that, but I have tried ubuntu 12.04 ISO with UNetBootIn and that was perfect. Problem only occurs when I'm trying with my customized ISOs. Same problem is happening again and again. That's why I thought it is not a problem related to UNetBootIn. Whatever I'll post the update here.

---

### Post by tea for one on 2013-06-13
As a little experiment, try to create an ISO of your OS without any personal data or extreme modifications. For example, a copy of 12.04 with some extra software added.

I have read that there is a limit on the ISO size but I am not sure what it is.

---

