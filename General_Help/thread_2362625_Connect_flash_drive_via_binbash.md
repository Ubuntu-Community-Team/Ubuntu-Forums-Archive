---
title: "Connect flash drive via /bin/bash"
date: 2017-05-31
forum: General Help
---

### Post by nuttapat007 on 2017-05-31
I tired to connect usb via /bin/bash
When plugged in , display print the device details. I run this command ```
fdisk -l 
``` but the output doesn't show flashdrive 's information.

---

### Post by ajgreeny on 2017-05-31
Usually when you attach a USB mass storage device such as a flash drive it is detected and mounted automatically; depending on the filesystem on that drive it may or may not immediately be writeable though that is usually easily solved.

What do you mean when you say you are trying to connect by /bin/bash?

What output do you see from commands ```
sudo fdisk -l
sudo parted -l
sudo blkid -c /dev/null
```run one by one; your comment above about the fdisk output is not helpful and we need to see everything please.

Starting with the drive unattached plug it in and immediately run command ```
dmesg | tail
```and show us the output from that.

Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by nuttapat007 on 2017-05-31
> **ajgreeny said:**
> 

What do you mean when you say you are trying to connect by /bin/bash?



I mean root shell prompt

---

### Post by Habitual on 2017-05-31
You're not booting from it are you?

---

### Post by ajgreeny on 2017-05-31
> **nuttapat007 said:**
> I mean root shell prompt

I'm afraid that still does not tell us anything meaningful.

Tell us in detail what you are trying to do and the commands you've used so far which have not worked.

---

