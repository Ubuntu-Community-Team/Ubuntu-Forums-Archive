---
title: "Dell inspiron 7559 - Cannot Restart/Suspend"
date: 2016-06-16
forum: General Help
---

### Post by Wickd on 2016-06-16
Hi All

I have recently bought the Dell Inspiron 7559 i7 6700 laptop, smacked in a 500 gb ssd evo 850 and an additional 8 GB of RAM. I set up the Dual boot with Windows 10 and Ubuntu 16.04 LTS and all was well.

The only issue that I have is that I cannot restart or suspend at all...

Many Thanks!

---

### Post by Jason_Hunter on 2016-06-16
wow, that's like no information at all. 

Any error message?  

what happens?

---

### Post by Wickd on 2016-06-17
You are right. Horribly little information. Let me add some more information!

Upon shutdown/restart i get the following error: NMI Watchdog: BUG: soft lockup CPU #4 stuck for 22 ms. From my readins some people blame the power supply, which I think is highly unlikely in my situation as the machine is less than 2 weeks old. Some think it is related to a recent kernel update that is to blame...

[URL="https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1530405"]https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1530405
[/URL]

Lot of people reporting this issue on a system with a combination of i7 6700hq and Nvidia GTX960M...

---

### Post by Wickd on 2016-06-17
Ok so solved my own problem. Turns out this is indeed related to the nvidia driver. I added the relevant repo and installed version 364 and voila I can now restart and suspend my system...

Here are the steps:

```
sudo apt-add-repository ppa:graphics-drivers/ppa
apt-get update
sudo apt-get install nvidia-364
```

I got this from the following [http://askubuntu.com/questions/768959/ubuntu-16-04-nvidia-drivers-for-geforce-gtx-960m](http://askubuntu.com/questions/768959/ubuntu-16-04-nvidia-drivers-for-geforce-gtx-960m)

Cheers!

---

### Post by Andrew F in Australia on 2016-11-13
Another machine with the intel i7-6700hq chip and NVidia GTX965M with an identical problem.  I'll add the driver above and reboot, let you know if it solved my issue as well.

Regards,

Andrew F

---

### Post by Andrew F in Australia on 2016-11-13
Thanks for this post, Wickd.

Another i7 6700HQ and NVidia GTX965M laptop that was hanging with the NMI Watchdog: BUG: Soft Lockup.

This driver upgrade worked perfectly.  Current version is nvidia-367

Regards,

A

---

### Post by dspjmr on 2016-11-20
I don't know why, this doesn't work for me. Tried everything, every driver, every version of ubuntu. Only works on 16.04 with the dysfunctional shutdown.

---

