---
title: "initramfs  error on encrypted HD after failed attempt to mount"
date: 2019-01-01
forum: General Help
---

### Post by raul-mccai on 2019-01-01
A hard disc with an encrypted  Ubuntu OS   (some ver of 16)  
I tried to mount it with another OD of ubuntu
The  volume appears and is detected by the OS when I plugged it in my front bay and then when I sought to access it and  entered the passphrase to access it it disappeared.
POOF gone
So I pulled it from the front bay - while powered up. 

Then when I tried to load that hard disk as the prime drive it  returned  INITRAMFS and I can get no further
Oddly the disk  begins the ubuntu count down which should not happen until after the  passphrase is entered. 

I've looked over a slew of  posts and solutions for  some  kind or other  of initramfs errors  and nothing has helped
I've read this [https://wiki.ubuntu.com/Initramfs](https://wiki.ubuntu.com/Initramfs)  It seems not to offer any assist. 

Any ideas?

---

### Post by wildmanne39 on 2019-01-01
Let's make sure you are using an supported version of Ubuntu before someone jumps in to help you get it working please post the output of:
```
cat /etc/lsb-release; uname -a
```
Thanks

---

