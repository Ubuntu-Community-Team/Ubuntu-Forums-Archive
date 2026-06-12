---
title: "Need help fixing the Cmos time."
date: 2012-11-11
forum: General Help
---

### Post by Extol11 on 2012-11-11
So I want to change the settings in Lubuntu so that they read the cmos time as UTC = no so that windows doesn't go all derp with the time after I boot ubuntu from the secondary hard drive. The thing is I used to do this in regular ubuntu with the following command 
```
gksu gedit /etc/default/rcS
```
It seems lubuntu doesn't use gedit so I tried the same command using leafpad but it did not work either. Can anyone tell me the right command so I can edit that file and change UTC from yes to no? Thanks a lot for your help.

---

### Post by efflandt on 2012-11-12
Not sure what you are trying to do there, but typically you use **hwclock** to tell the kernel what the CMOS clock/calendar is in relation to localtime.  I thought Ubuntu normally automatically uses localtime if you installed Windows before Linux and selected proper timezone, so it has been awhile since I needed to do that.

See: [B]man hwclock
[/B] 
If system time is correct, to set CMOS to system time and tell Linux that CMOS is localtime
```
sudo hwclock -w --localtime
```
If system time is wrong and CMOS is still localtime set by Windows, to set system time to CMOS time and tell the kernel that CMOS is localtime:
```
sudo hwclock -s --localtime
```

After either, Linux will consider CMOS to be localtime.

---

### Post by kjohri on 2012-11-12
The following link gives the details regarding setting the hardware clock:

[http://www.softprayog.in/tutorials/hwclock-the-hardware-clock-query-and-set-program]("http://www.softprayog.in/tutorials/hwclock-the-hardware-clock-query-and-set-program")

---

### Post by Extol11 on 2012-11-12
Well, when I boot up windows after using linux, the time in windows is four to five hours ahead of what it should be. I just normally edited that file and changed the UTC setting. I always works but since I installed lubuntu now it doesn't have gedit. I don't want to install gedit just for this. I'll see that new method but I am not sure it is what I'm looking for. Thanks.

---

### Post by Extol11 on 2012-11-12
Ok. I fixed it. I just used sudo, then leafpad and passed the directory as a parameter like this: 
```
sudo leafpad /usr/default/rcS
```

---

