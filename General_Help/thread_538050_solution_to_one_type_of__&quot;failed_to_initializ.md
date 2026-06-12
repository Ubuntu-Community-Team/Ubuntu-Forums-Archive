---
title: "solution to one type of  &quot;failed to initialize HAL&quot; -- upgrade"
date: 2007-08-29
forum: General Help
---

### Post by xiang on 2007-08-29
Hi

Here I describe a type of "failed to initialize HAL" problem and its solution. (There are so many types of  "failed to initialize HAL", so please check whether your symptom is the same as mine first).

symptom:
install ubuntu 7.04 by wubi
when login, a pop-out window said "internal error, failed to initialize HAL". You will also found "no network connection" on the network icon at the systemtray. In addition, you can't open "power management" and "hardware information" in "preference".

solution:
search "hal" in synaptic, you will find  the below packages
hal
hal-device-manager
libhal-storage1
libhal1

check the properties of them, you can notice they have 2 versions. !!! force them to the old version. Everything will be OK.

(BTW, I also do a little other changes. I am not sure whether they also have effects but you can try if something goes wrong.
force kdebase-kio-plugins to old version
install hal-cups-utils libopenexr2c2a initscripts)

conclusion
This problem is due to the upgrade of HAL related packages. It seems that this problem just occurs in the systems installed by wubi but not in standard systems. I also encountered other problems (slow system) when upgraded, I am not sure what caused them, ubuntu itself or wubi? So my experience is if your system run well, do not upgrade.

---

### Post by ago on 2007-08-29
That's an interesting bug,

It's not the first time I saw bug reports abou hal upgrade, but I was never able to reproduce that on my machine. If you could digg the exact reason, it would help a lot.

---

### Post by bibobx on 2007-08-31
hi ijust posted this in other thread: i found this kind of solution:
copy the simlink  S12Dbus from /etc/rc3.d to /etc/rc2.d it worked for me

---

### Post by xiang on 2007-08-31
This method is not suitable for me because I had S12dbus in /etc/rc2.d when I encountered the problem. As noted, there are many reasons leading to  "failed to initialize HAL" , so it will be helpful if you can provide the description of your specific "failed to initialize HAL" with this solution.

---

### Post by moulin on 2007-09-06
I experience the same problem. I had to go for xiang's solution. Is there a way I can send in some log files so the hal development team can have a look at it?

Kind regards,

Marco

---

### Post by ago on 2007-09-06
> **moulin said:**
> I experience the same problem. I had to go for xiang's solution. Is there a way I can send in some log files so the hal development team can have a look at it?

Kind regards,

Marco

If you think there is a bug, you can open a ticket in launchpad.net. Be as specific as possible.

---

### Post by moulin on 2007-09-06
> **ago said:**
> If you think there is a bug, you can open a ticket in launchpad.net. Be as specific as possible.

[https://launchpad.net/hal](https://launchpad.net/hal) ? Or might this be a bug for wubi?

---

### Post by ago on 2007-09-06
I don't know since I cannot reproduce that on my machine and no user so far has submitted detailed info on it.

---

### Post by moulin on 2007-09-10
Any idea what command I can try to create a log file I can submit?

---

### Post by ago on 2007-09-11
I am not that familiar with hal, I guess /var/log/syslog is a good starting point, moreover you may try to stop the hal daemon and then start it manually on a console with --daemon=no --verbose=yes

---

### Post by jryprt on 2007-09-13
> **xiang said:**
> Hi

Here I describe a type of "failed to initialize HAL" problem and its solution. (There are so many types of  "failed to initialize HAL", so please check whether your symptom is the same as mine first).

symptom:
install ubuntu 7.04 by wubi
when login, a pop-out window said "internal error, failed to initialize HAL". You will also found "no network connection" on the network icon at the systemtray. In addition, you can't open "power management" and "hardware information" in "preference".

solution:
search "hal" in synaptic, you will find  the below packages
hal
hal-device-manager
libhal-storage1
libhal1

check the properties of them, you can notice they have 2 versions. !!! force them to the old version. Everything will be OK.

(BTW, I also do a little other changes. I am not sure whether they also have effects but you can try if something goes wrong.
force kdebase-kio-plugins to old version
install hal-cups-utils libopenexr2c2a initscripts)

conclusion
This problem is due to the upgrade of HAL related packages. It seems that this problem just occurs in the systems installed by wubi but not in standard systems. I also encountered other problems (slow system) when upgraded, I am not sure what caused them, ubuntu itself or wubi? So my experience is if your system run well, do not upgrade.

This worked for me Thanks xiang

---

### Post by genXesis on 2007-10-15
This describes the exact problem I'm having with 7.04.  However, when I go to downgrade the versions, it seeks to download files.  Since a part of the problem is my network device isn't found, how can I download files to downgrade versions?

---

### Post by lebrun on 2007-10-27
I got this error after I enabled the backports repository and updated hal from it. A way to avoid this is to pin the hal version to the one installed. You can do this by placing this text on /etc/apt/preferences:

```
Package: hal
Pin: version 0.5.8*
Pin-Priority: 990

Package: libhal1
Pin: version 0.5.8*
Pin-Priority: 990

Package: libhal-storage1
Pin: version 0.5.8*
Pin-Priority: 990
```

While it won't help if you already got the error, this allows you to enable the backports repository without a hal update ruining you installation.

---

### Post by Six_Digits on 2007-10-30
This soloution worked for me:
```
sudo /usr/lib/hal/hald-generate-fdi-cache
```

[[COLOR="Navy"]http://ubuntuforums.org/showthread.php?t=583940[/COLOR]]("http://ubuntuforums.org/showthread.php?t=583940")

---

### Post by ago on 2007-10-31
Good tip Six_Digits looks interesting.

Guys can you check what is the status of hal with wubi 7.10?

---

### Post by pienose on 2007-11-04
I exactly the same problem, but in gusty. There is only version of the pacages, so is there a fix for gusty?

---

