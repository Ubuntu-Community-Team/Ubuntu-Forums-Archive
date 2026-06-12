---
title: "Problem with resume from suspend"
date: 2014-04-19
forum: General Help
---

### Post by shadytv on 2014-04-19
My Toshiba Satellite A665-S6065 won't wake from suspend, this problem started occuring around 2 weeks ago and i'm pretty sure an update to apport has caused it. It has been a problem on both 13.10 and 14.04. What happens is when i close the lid on my laptop (power settings set to suspend) the laptop goes into hibernate like it should, but when I try to wake it up, The fan starts running really hard and the computer kills. When i boot the system back up apport freaks out and puts around 8 or 9 error reports that say "apport checkresume crashed". If i try to submit them It asks for my password then just closed I have no clue if they even submitted. I've tried reinstalling apport and it's still giving problems.


I not sure how I should go about submitting this, If anybody has any tips/suggestions it would be greatly appreciated.


[https://wiki.ubuntu.com/DebuggingKernelHibernate](https://wiki.ubuntu.com/DebuggingKernelHibernate) told me I should give this information:


cat /proc/cmdline:


```
BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=9c4d08d1-43b9-4baf-82d0-e0481f665d2c ro crashkernel=384M-:128M
```


cat /etc/initramfs-tools/conf.d/resume:


```

#RESUME=UUID=bc13c376-b933-45fb-9bda-83cb1ae9365c
RESUME=/dev/disk/by-uuid/bc13c376-b933-45fb-9bda-83cb1ae9365c

```

P.S. I have no proprietary drivers on my system (I've tried switching to them and got nothing).


EDIT: I looked at the bug report and it seems to be an issue with wpa_supplicant, I've had a lot of problems with this damn thing is the past :/ like constant dropping WiFi and general instability. so needless to say wpa_supplicant is a peice of crap!

---

### Post by shadytv on 2014-04-19
Anyone? Am I really the only person?

---

