---
title: "No ethernet connection in dual boot with Windows 10 and Kubuntu"
date: 2021-01-07
forum: General Help
---

### Post by lulonaut on 2021-01-07
I already posted this qustion here: [https://askubuntu.com/questions/1305790/no-ethernet-connection-in-dual-boot-with-windows-10-and-kubuntu](https://askubuntu.com/questions/1305790/no-ethernet-connection-in-dual-boot-with-windows-10-and-kubuntu) but got no useful answers.
This is the question:
[]("https://askubuntu.com/posts/1305790/timeline")  
          
                                            I am currently dual booting Kubuntu (20.04.1 LTS) and Windows 10 (should be up to date).
 I only started doing this yesterday and at the beginning everything  worked fine. However after switching to Windows to export some config  files and then switching back to Kubuntu I had no Internet (at all) and  no Sound (USB Headset). Both of these still work as of right now (typing  this in Windows 10).


 Im on a Ethernet connection with a Realtek controller (on my  motherboard), Windows won't say much more but this is the driver  version: 10.37.1028.2019
 My Headset is a Sound blaster XH6, also working fine on Windows but getting Ethernet working is my priority right now.


 Here is the (probably incomplete list) of what I tried:
 
[LIST]
[*]Shutting down Windows instead of restarting
[*]Disabling "Allow the computer to turn off this device to save power" in Device Manager
[*]Enabling/Disabling "Shutdown Wake-On-Lan" in Device Manager
[*]Running ipconfig /release before exiting Windows
[*]Setting up a new Ethernet connection in Kubuntu
[/LIST]


I am out of ideas from myself and already looked at tons of questions, none having an answer that also helped me.

 Please tell me if I need to provide more information.


 Output of running lscpi on Kubuntu: [https://pastebin.com/shmkpzRc](https://pastebin.com/shmkpzRc)

---

### Post by linerman on 2021-01-07
Hi,

Seems that you have same ethernet card as me. After upgrading kernel today I also had problem with my ethernet card, which has worked yesterday. Check out my solution here:
[https://ubuntuforums.org/showthread.php?t=2456227](https://ubuntuforums.org/showthread.php?t=2456227)

---

### Post by lulonaut on 2021-01-07
Thanks, I already fixed it by using an older kernel at boot but im going to take a look at your post.

---

### Post by farlander762 on 2021-01-07
I had a similar problem after kernel update with a Broadcom Wi-Fi/Bluetooth adapter in my laptop.  I had performed a couple of workarounds already with previous kernels but it finally gave up entirely in Ubuntu (still worked in Windows).  $15 and one laptop disassembly/reassembly later I installed an Intel adapter and my issues went away.  Support for Linux is not always assured.

---

