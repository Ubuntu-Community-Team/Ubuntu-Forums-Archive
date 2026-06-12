---
title: "Virtualbox with Kernel 5.3"
date: 2019-09-20
forum: General Help
---

### Post by montfox on 2019-09-20
Is it possible to run Virtualbox with the mainline 5.3 kernel? I run qemu for most things, but I need virtualbox for anbox. I'm not able to run /sbin/vboxconfig without errors

```
[FONT=monospace][COLOR=#000000]WARNING: The vboxdrv kernel module is not loaded. Either there is no module[/COLOR]
         available for the current kernel (5.3.0-050300rc6-generic) or it failed to
         load. Please recompile the kernel module and install it by

           sudo /sbin/vboxconfig

         You will not be able to start VMs until this problem is fixed.

[/FONT]
```

---

### Post by deadflowr on 2019-09-20
Why not follow the recommended anbox installation by anbox developers:
[https://docs.anbox.io/userguide/install.html]("https://docs.anbox.io/userguide/install.html")

---

### Post by montfox on 2019-09-20
Awesome! Thanks! I thought I needed virtual box

---

### Post by sdsurfer on 2019-09-24
I get this all the time, off and on. I attempt to run the suggested command, still broken. The only thing that seems to work is to uninstall and reinstall VB. The good news is it doesn't lose the machines I've configured.

Be sure to mark your thread as solved, if it is.

---

### Post by SeijiSensei on 2019-09-24
I've never had a problem using the Oracle repository for VirtualBox: [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)

Installing that will bring in the compiler and DKMS which are need to create the kernel module.

---

### Post by madscintist on 2019-10-11
I need help getting virtualbox 6.0.12 with kernel 5.3 as well it wont build with this kernel does anybody know how to get it to work?

---

### Post by SeijiSensei on 2019-10-12
I installed a [test build]("https://www.virtualbox.org/wiki/Testbuilds") successfully on 19.10 with 5.3.0-13-generic.

---

### Post by timgood on 2019-10-12
> **madscintist said:**
> I need help getting virtualbox 6.0.12 with kernel 5.3 as well it wont build with this kernel does anybody know how to get it to work?

VB does not work with kernel 5.3 and this is a known problem. I have started using VM Ware Player instead - much faster as well.

---

### Post by guiverc on 2019-10-12
fyi:  I use the standard Ubuntu packaged version of virtualbox (6.0.12-dfsg-1), and have no issues running using 5.3 kernel (5.3.0-17-generic though it'll be -18 when I allow reboot), nor have I since the 5.3 upgrade.  I've used on this box doing `do-release-upgrade -d` testing for the upcoming 19.10 release in the last week.

---

### Post by madscintist on 2019-10-12
[SIZE=2]
[/SIZE]
[SIZE=1][/SIZE][COLOR=#DD4814][COLOR=#000000][SIZE=3]Thank you all for your help i will try it out again with kernel 5.3[/SIZE] [SIZE=1][SeijiSensei]("https://ubuntuforums.org/member.php?u=698195")[/SIZE][/COLOR][/COLOR][COLOR=#000000]  [/COLOR][[COLOR=#000000]timgood[/COLOR]]("https://ubuntuforums.org/member.php?u=186361")[COLOR=#000000] [/COLOR][guiverc]("https://ubuntuforums.org/member.php?u=2074246")

[SIZE=3]I was running kernel 5.3.6 on ubuntu 18.04 and couldn't get virtualbox to run with that kernel? I shoulkd have been more specific  [/SIZE]

---

