---
title: "Problems with screen resolution / blurry"
date: 2015-10-01
forum: General Help
---

### Post by Stosskraft on 2015-10-01
Hello all,

I am at a complete loss here. I have a fresh install of ubuntu 15 on my brand new HP 23' all in one desktop. For some reason the display is very blocky and blurry almost like 8bit graphics. I normally run Linux Mint KDE but it had the same problem and some members over at the forum suggested I try the newest ubuntu as it might have the correct intel display drivers. Here are some photos from the mint install but the ubuntu is exactly the same: 

[img][[IMG]http://i300.photobucket.com/albums/nn35/yrolling/snapshot1_zpse2gdards.png[/IMG]]("http://s300.photobucket.com/user/yrolling/media/snapshot1_zpse2gdards.png.html")[/img] 

[img][[IMG]http://i300.photobucket.com/albums/nn35/yrolling/mag2.jpeg_zpso5pf6jma.png[/IMG]]("http://s300.photobucket.com/user/yrolling/media/mag2.jpeg_zpso5pf6jma.png.html")[/img]

The photos do not show how bad it is really, it is even hard to see what I am typing. I do feel that ubuntu is the most current of the distros and this is my last resort before going back to window 8.1.
I did update to the lastest Kernal in mint and nothing happened.
I have also tried on live usb : Kubuntu, Cinnomon, Mint Mate

All have the same problem.

The  Windows 8.1 that came pre installed on the computer was perfect, really  incredible display on this computer, and now the display is really hard  to even read fonts.

I am not sure what to try now. Any suggestions are greatly appreciated.

---

### Post by QDR06VV9 on 2015-10-01
Open a terminal and paste back the output of
```
[COLOR=#111111][FONT=Consolas]lshw -C video[/FONT][/COLOR]
```

---

### Post by Stosskraft on 2015-10-01
```
lshw -C video
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: 4th Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:36 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.


```

---

### Post by QDR06VV9 on 2015-10-01
Huumm?
One more if you don't mind.
```
apt-cache policy [COLOR=#111111][FONT=Consolas] xserver-xorg-video-intel[/FONT][/COLOR]
```
Paste that back also.

---

### Post by Stosskraft on 2015-10-01
Dont mind at all :)

```
yanek@yanek-23-r009:~$ apt-cache policy  xserver-xorg-video-intel
xserver-xorg-video-intel:
  Installed: 2:2.99.917-1~exp1ubuntu2.2
  Candidate: 2:2.99.917-1~exp1ubuntu2.2
  Version table:
 *** 2:2.99.917-1~exp1ubuntu2.2 0
        500 http://us.archive.ubuntu.com/ubuntu/ vivid-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     2:2.99.917-1~exp1ubuntu2build1 0
        500 http://us.archive.ubuntu.com/ubuntu/ vivid/main amd64 Packages


```

---

### Post by QDR06VV9 on 2015-10-01
My friend I am at a loss here.
There is a PPA for vivid and intel drivers that shows a little hope
Found here [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers)
Bear in mind I have no experience with that PPA but a few posts showed good results.(Fingers Crossed)
Sorry i was not more helpful.
Kind Regards

---

### Post by Stosskraft on 2015-10-01
Thanks for the attempt, after 8 years with linux I am going to have to return to windows until there is a fix.

Thank you again

---

