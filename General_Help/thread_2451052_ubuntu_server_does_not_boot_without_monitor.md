---
title: "ubuntu server does not boot without monitor"
date: 2020-09-25
forum: General Help
---

### Post by danielstephens81 on 2020-09-25
Hello there,

Problem : ubuntu server does not boot without a monitor connected. It worked fine as a headless unit for over a year, this is a new issue on my intel nuc. I recently did an apt update / apt upgrade that required a restart and this is when the issue started.

I have tried editing my /etc/default/grub as was suggested [here]("https://askubuntu.com/questions/825687/what-could-prevent-an-ubuntu-server-from-booting-without-a-vga-connected-monitor"). But it still does not work without a monitor. dmesg shows a hw error of some sort, I have no idea what that is....

I am running .... 
Linux ubuntu_server 4.15.0-118-generic #119-Ubuntu SMP Tue Sep 8 12:30:01 UTC 2020 x86_64 x86_64 x86_64 GNU/LinuxLinux ubuntu_server 4.15.0-118-generic #119-Ubuntu SMP Tue Sep 8 12:30:01 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

The following files are attached
* grub file
* output of dmesg | grep 'Error'

Any suggestions welcome. Thank you.

Kind regards,
d

---

### Post by HermanAB on 2020-09-26
I think that all you need to do is delete the xorg.conf file. Worth a try since it is easy to do.

---

### Post by danielstephens81 on 2020-09-26
Hello Herman, 

Thank you for your suggestion, but I do not have this file in my system.... (I think it is only there on the desktop installations.)

I checked the following locations...
```
~# ls -l /etc/X11/
total 56
-rwxr-xr-x 1 root root   709 Jan 20  2017 Xreset
drwxr-xr-x 2 root root  4096 Oct 30  2019 Xreset.d
drwxr-xr-x 2 root root  4096 Oct 30  2019 Xresources
-rwxr-xr-x 1 root root  3730 May  3  2017 Xsession
drwxr-xr-x 2 root root  4096 Sep 18 06:14 Xsession.d
-rw-r--r-- 1 root root   265 Jan 20  2017 Xsession.options
drwxr-xr-x 2 root root  4096 Nov 24  2019 app-defaults
drwxr-xr-x 4 root root  4096 Sep 25 20:31 fonts
-rw-r--r-- 1 root root 17394 Jan 20  2017 rgb.txt
drwxr-xr-x 2 root root  4096 Feb  2  2018 xkb
```

```
~# ls /usr/share/X11/xorg.conf.d/
10-quirks.conf

```

Kind regards,

Daniel

---

### Post by HermanAB on 2020-09-26
If you have one, then it will be here:
/etc/X11/xorg.conf

If you don't have it, then X will look for the screen on each boot and configure whatever it finds, automatically.
If you do have, it, then X will do whatever is in the xorg.conf file.

So, since you don't have it and it doesn't work in autoconfigure mode, you could try to make a dummy one with no display.

Here is a nicely confusing discussion on these issues:
[https://askubuntu.com/questions/4662/where-is-the-x-org-config-file-how-do-i-configure-x-there](https://askubuntu.com/questions/4662/where-is-the-x-org-config-file-how-do-i-configure-x-there)

---

### Post by danielstephens81 on 2020-09-26
Hello Herman, 

Thank you for your suggestion. I have found a solution, one that I ignored initially as I did not find anything worth editing in the BIOS. I just did a BIOS update on my intel NUC. After re-flashing the unit it appears to work headless once again. Perhaps it could be that the hdmi driver used in the bios was outdated and not suited for the recent ubuntu upgrades. Thank you for your time and patience.

Kind regards,

ds.

---

