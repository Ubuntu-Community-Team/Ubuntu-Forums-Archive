---
title: "how do i install mainline kernel 4.7 from ppa download on ubuntu 16.04 successfully?"
date: 2016-07-30
forum: General Help
---

### Post by craymore on 2016-07-30
how do i install mainline kernel 4.7 from ubuntu canonical ppa and sudo dpkg -i the kernels debs on ubuntu 16.04 successfully without breaking any modules and for successful reboot ?


i do not mind using nouveau instead of nvidia driver if it must be done.  

thank you

---

### Post by pqwoerituytrueiwoq on 2016-07-30
this tool makes it easier 
[https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater)
if you want to know which beds you need to do it manually i need to know if you are using 32 or 64bit

---

### Post by craymore on 2016-07-30
> **pqwoerituytrueiwoq said:**
> this tool makes it easier 
[https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater)
if you want to know which beds you need to do it manually i need to know if you are using 32 or 64bit

thank you very much.  for some reason despite it download the correct debs it does not patch it for ubuntu 16.04 despite it being on the Ubuntu ppa.

can you or anyone assist me with Kernel 4.7 ?


thanks

---

### Post by craymore on 2016-07-30
:popcorn:

i can confirm kernel 4.7 does work with this script despite me trying to do it manually failing and just with nouveau driver as i desired it.  

thanks !  :D

ubuntu 16.04 LTS

sorry for the panic.   i watched it in real time and didn't believe it would work.

---

### Post by DuckHook on 2016-07-30
*Please mark thread **solved** using *Thread Tools* in the top toolbar for the benefit of others searching for solutions*.

---

### Post by jeremy31 on 2016-07-30
You should file a bug report about your issue with the 4.4 kernel so it helps others that may have the same problem.  See [https://ubuntuforums.org/showthread.php?t=1011078](https://ubuntuforums.org/showthread.php?t=1011078)

By using a 4.7 kernel you may miss some of the security updates Ubuntu will have in the newer 4.4 kernels as Grub will keep using the 4.7 kernel even if the newest 4.4.0-? has better security updates

---

### Post by pqwoerituytrueiwoq on 2016-07-30
if you want the nvidia driver you may need this ppa when using the mainline kernel
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
if you don't plan to use the nvidia driver or virtualbox you probably will not need the header package, the script defaults to giving that to you, see the --help options for more info

---

