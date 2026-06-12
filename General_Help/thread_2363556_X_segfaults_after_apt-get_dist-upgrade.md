---
title: "X segfaults after apt-get dist-upgrade"
date: 2017-06-11
forum: General Help
---

### Post by SagaciousKJB on 2017-06-11
Yesterday I performed apt-get dist-upgrade and ever since my X server has been randomly crashing. At least I think it's X because it keeps referring to libX11.so  On the other hand, it seems that several processes are causing it.

```
Jun 11 13:53:48 AMD kernel: [144667.528387] LogForward[386]: segfault at 7fd33401cd00 ip 00007fcfa93c7b46 sp 00007fcf8103cd80 error 4 in libmythbase-0.28.so.0.28.0[7fcfa92a1000+1f8000]
Jun 11 13:55:02 AMD kernel: [144741.808255] chrome[19447]: segfault at 968 ip 00007f2578e53d0d sp 00007ffe5d000fd0 error 4 in libX11.so.6.3.0[7f2578e2c000+130000]
Jun 11 13:55:03 AMD kernel: [144742.481544] chrome[19497]: segfault at 968 ip 00007f08c034ad0d sp 00007ffdf78d3550 error 4 in libX11.so.6.3.0[7f08c0323000+130000]
Jun 11 13:58:29 AMD kernel: [144948.281471] chrome[20721]: segfault at 968 ip 00007f617a044d0d sp 00007fffd7f30ad0 error 4 in libX11.so.6.3.0[7f617a01d000+130000]

```

How can I undo the changes dist-upgrade did to cause this?  Been running this setup literally for years with no problems like this so I can only assume it's a change apt-get made yesterday.

Does apt keep a log of updates? Maybe I can see what X I upgraded from and revert?

Ubuntu 14.04.05 LTS, XFCE 4 window manager, really not sure what else relevant info to go here.  Graphics drivers?  Like I said, haven't had an issue until this last upgrade.

---

### Post by deadflowr on 2017-06-11
> Does apt keep a log of updates? Maybe I can see what X I upgraded from and revert?

Yes it does.
Look in /var/log/apt.
the history.log will show what was updated.
the term.log will give more verbose info on what apt was doing.

---

### Post by SagaciousKJB on 2017-06-11
Thank you.

I tried to grep for xorg, xserver, or x11, and only found this line referring to x11

```
libva-x11-1:amd64 (1.3.0-2, 1.4.0~trusty)
```

Wouldn't that be the vesa drivers though? I'm using the nvidia drivers.  I did notice that it installed something to do with vdpau that I don't think I had before...

```
vdpau-va-driver:amd64 (0.7.3-2ubuntu1.2, automatic)
```

I'm using a fairly older NVIDA driver because my hardware is also old, so it's on 173, but I was looking at the nvidia packages installed and I think that this other one is new

```
kenny@AMD:~$ apt list --installed | grep nvidia

WARNING: apt does not have a stable CLI interface yet. Use with caution in scripts.

nvidia-173/trusty,now 173.14.39-0ubuntu3 amd64 [installed]
nvidia-opencl-icd-304/trusty-updates,trusty-security,now 304.135-0ubuntu0.14.04.1 amd64 [installed,automatic]
nvidia-settings/trusty,now 331.20-0ubuntu8 amd64 [installed,automatic]

```

The nvidia-opencl-icd one seems to have been picked up with the dist-upgrade, but I'm not sure, maybe it just got upgraded? This is the only line mentioning nvidia in the apt log

```
nvidia-opencl-icd-304:amd64 (304.134-0ubuntu0.14.04.1, 304.135-0ubuntu0.14.04.1)
```


As far as I know I am not configuring anything to use vdpau, but on the other hand the two applications that seem to have made this libx11.so file segfault are ones that I know do use vdpau to some level. With Chrome, I was trying to get WebGL to run so I know it's doing hardware acceleration, but I didn't know if it had anything to do with chrome. My MyhTV client on the other hand, I don't think I have it set to run anything with vdpau, but I know there are sometimes different profiles for different resolutions of media and maybe one tried to run it.  I guess the next thing would be to try to figure out what's even causing it to crash, because it seems totally random.

I think chrome is the probably the more likely culprit, because the first time this happened I was listening to music in MythTV's MythMusic plugin, typing a paper in Google Docs on chrome and the X screens just totally died.  I was just left looking at like, what the terminal would look like during the init launches, and my music was still playing in the background. That particular time I had to restart the computer, but every time afterward it's just restarted lightdm and brought me back to a login screen.

---

