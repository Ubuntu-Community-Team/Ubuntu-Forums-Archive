---
title: "Black screen after suspend, Ubuntu 16.04LTS"
date: 2017-07-24
forum: General Help
---

### Post by jdmr4815 on 2017-07-24
As the title says, when I return to my computer and open the lid I sometimes get nothing but a black screen. It doesn't always happen.

I've tried these solutions:

[https://ubuntuforums.org/showthread.php?t=2263908&page=2&highlight=Black+screen+suspend%2C+Ubuntu+16.04LTS](https://ubuntuforums.org/showthread.php?t=2263908&page=2&highlight=Black+screen+suspend%2C+Ubuntu+16.04LTS)
(adding the back light fix script).

[https://ubuntuforums.org/showthread.php?t=2115441&highlight=black+screen+suspend](https://ubuntuforums.org/showthread.php?t=2115441&highlight=black+screen+suspend)
(checking out various parameters, none of which fit my situation)

[https://askubuntu.com/questions/899454/black-screen-after-waking-from-suspend](https://askubuntu.com/questions/899454/black-screen-after-waking-from-suspend)
(Adding nomodset to the BIOS options)

[https://askubuntu.com/questions/760374/ubuntu-16-04-nvidia-driver-blank-screen?rq=1](https://askubuntu.com/questions/760374/ubuntu-16-04-nvidia-driver-blank-screen?rq=1)
(This last one doesn't really even apply since I don't have nvidia drivers.)

I've also tried changing the kernel to another version that apparently fixed the problem for others, without luck. 

Here is some info about my computer:

OS: Ubuntu 16.04.2 LTS x86_64 
Model: Inspiron 5558 01 
Kernel: 4.10.0-27-generic 
Uptime: 13 mins 
Packages: 2118 
Resolution: 1366x768  
DE: Unity 
WM: Compiz 
WM Theme: Ambiance 
Theme: Ambiance [GTK2/3] 
Icons: Ubuntu-mono-dark [GTK2/3] 
Terminal: gnome-terminal 
CPU: Intel i3-4030U (4) @ 1.800GHz 
GPU: Intel Integrated Graphics  
Memory: 1193MiB / 15962MiB 


This problem doesn't happen every time. I've seen it happen when my second monitor was connected, so I always disconnect it before I suspend. I've also seen it happen when I had a virtual machine running, so I make sure to shut it down before suspend. I can't find any common denominator. And it hasn't always done this. It only started in the last few months.

---

### Post by h2opolo2 on 2017-07-26
I have the same problem in two machines, with no solution, any?

---

### Post by Phil Walsh on 2017-07-26
After accepting software upgrade a couple days ago I now have the same problem--after the screen turns off due to inactivity timeout, it never comes back--back light comes on, cursor appears and reacts to mouse movement, but nothing else ever appears on screen. Box has to be powered off and back on.

           $ hostnamectl status
Chassis: laptop
           ....
  Operating System: Ubuntu 16.04.2 LTS
            Kernel: Linux 4.10.0-27-generic
      Architecture: x86-64

---

### Post by Phil Walsh on 2017-07-26
I was able to solve my problem by going into BIOS settings on my ThinkPad and changing the graphics setting from "Discrete Graphics" to "Integrated Graphics."

---

### Post by BenginM on 2017-07-26
> **jdmr4815 said:**
> As the title says, when I return to my computer  and open the lid I sometimes get nothing but a black screen. It doesn't  always happen.

I've tried these solutions:

[https://ubuntuforums.org/showthread.php?t=2263908&page=2&highlight=Black+screen+suspend%2C+Ubuntu+16.04LTS](https://ubuntuforums.org/showthread.php?t=2263908&page=2&highlight=Black+screen+suspend%2C+Ubuntu+16.04LTS)
(adding the back light fix script).

[https://ubuntuforums.org/showthread.php?t=2115441&highlight=black+screen+suspend](https://ubuntuforums.org/showthread.php?t=2115441&highlight=black+screen+suspend)
(checking out various parameters, none of which fit my situation)

[https://askubuntu.com/questions/899454/black-screen-after-waking-from-suspend](https://askubuntu.com/questions/899454/black-screen-after-waking-from-suspend)
(Adding nomodset to the BIOS options)

[https://askubuntu.com/questions/760374/ubuntu-16-04-nvidia-driver-blank-screen?rq=1](https://askubuntu.com/questions/760374/ubuntu-16-04-nvidia-driver-blank-screen?rq=1)
(This last one doesn't really even apply since I don't have nvidia drivers.)

I've also tried changing the kernel to another version that apparently fixed the problem for others, without luck. 

Here is some info about my computer:

OS: Ubuntu 16.04.2 LTS x86_64 
Model: Inspiron 5558 01 
Kernel: 4.10.0-27-generic 
Uptime: 13 mins 
Packages: 2118 
Resolution: 1366x768  
DE: Unity 
WM: Compiz 
WM Theme: Ambiance 
Theme: Ambiance [GTK2/3] 
Icons: Ubuntu-mono-dark [GTK2/3] 
Terminal: gnome-terminal 
CPU: Intel i3-4030U (4) @ 1.800GHz 
GPU: Intel Integrated Graphics  
Memory: 1193MiB / 15962MiB 


This problem doesn't happen every time. I've seen it happen when my  second monitor was connected, so I always disconnect it before I  suspend. I've also seen it happen when I had a virtual machine running,  so I make sure to shut it down before suspend. I can't find any common  denominator. And it hasn't always done this. It only started in the last  few months.



Hiya , am not sure if your suspending to RAM or disk , or both .. since this is on a laptop it's most likely the suspend state is to RAM .. do you hear the fan running and see the lights still on!

is the laptop connect to wifi while this suspend black screen issue occurs , if so .. I'm curious as to which wireless card is in use ..
lspci | grep Network

should tell ...

if your machine is mostly connected to AC versus running off battery,   try changing your power settings to "Don't Suspend" for AC operation!

Also, is the BIOS up-to-date ..?

---

### Post by h2opolo2 on 2017-07-27
i have up to date bios, and no have option for change "graphics settings" in bios, on my Dell precision T3500.

---

### Post by giddensdb on 2017-07-28
I have this same problem on a desktop machine with directly connected internet. Started after a kernel update. Hope there is a fix soon.

---

### Post by h2opolo2 on 2017-08-08
> **giddensdb said:**
> I have this same problem on a desktop machine with directly connected internet. Started after a kernel update. Hope there is a fix soon.


Any with this problem, i can't solve.

---

### Post by BenginM on 2017-08-08
is swapon , #see $ swapon -s and

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by sputtie on 2017-09-11
I have this problem with 32 iMacs (Early 2008) that I've converted to Ubuntu for an elementary school.  This computer lab had been working very well last year until updating introduced this bug.  Please if anyone has found a solution can you post it here.

---

### Post by kwalters on 2017-09-14
May I add my name to the list of people suffering.

I did not describe it in exactly the same terms, but it seems very similar.  When the inactivity limit is reached, I get a black screen; but moving the mouse and pressing a key will not recover the OS. Only the power switch reboot will do it.

I have improved things slightly by setting the inactivity limit to 1 Hour.  I am reluctant to set it to "never" but I might yet have to

KW

---

### Post by rattskjelke on 2017-09-14
I have the same or similar problem on a HP Pavilion g7 laptop but it deosn't happen all the time.
I tried to diable suspend and only turn off the display and lock the session but that didn't help.
I tried Ubuntu MATE, Xubuntu, Lubuntu, Linux Mint and it does it on all of those but never on Windows 7.
There are no BIOS settings for the display on this machine.

---

### Post by zoepiel on 2017-09-15
Same issue for me on a Dell desktop. I have a wireless keyboard and a wired MS Intellimouse. The laser on the mouse stays lit, but no response after the machine has idled. Also, my display shows a blue LED as opposed to the amber one (the typical sign of a correct suspended state for my setup). I’m new here, recently migrated from Windows, and will be watching this thread with interest.

---

### Post by scotc on 2018-05-24
I have a very similar issue.  It may be the same "sometimes blank screen after suspend" that you have.  [https://ubuntuforums.org/showthread.php?t=2392448](https://ubuntuforums.org/showthread.php?t=2392448)
Mine was more serious though - it caused a filesystem corruption preventing a reboot.
I'm not seeing too much help for this issue across the forum

---

### Post by farlander762 on 2018-11-27
My monitors just say no signal.  Nvidia GeForce GT 420.  Problem started when I upgraded to 18.04.  Changed to the proprietary driver without any effect.

---

### Post by ricardo-pedri on 2018-11-30
Similar issue here. In my case, I get the password screen, but after entering the password I get a black screen.

---

### Post by im.tak on 2018-12-04
I had the same problem, after i close the lid, the screen will not turn on. I followed instructions given by ubuntu faqs and it worked in one shot. 

**'INFO: This will not work for 12.04, resume from hibernate work differently in 12.04.**' 

[LIST=1]
[*]Pull up a Terminal again and run cat /proc/swaps  and hopefully you see the path to your swap partition listed there. If  not chances are something went wrong in the steps above. Here's my  output: 
[/LIST]
Filename                                Type            Size    Used    Priority
/dev/sda2                               partition       2676732 73380   -1
[LIST=1]
[*]gksu gedit /etc/default/grub & to pull up the boot loader configuration 

[*]Look for the line GRUB_CMDLINE_LINUX="" and make sure it looks like this (using your UUID of course) GRUB_CMDLINE_LINUX="resume=UUID=41e86209-3802-424b-9a9d-d7683142dab7" and save the file 

[*]sudo update-grub and wait for it to finish 

[*]gksu gedit /etc/initramfs-tools/conf.d/resume & and make sure its contents are resume=UUID=41e86209-3802-424b-9a9d-d7683142dab7 (with your UUID of course in place of mine). Save the file! 

[*]sudo update-initramfs -u 

[*]Reboot!
[/LIST]

[https://askubuntu.com/a/1098390/899820](https://askubuntu.com/a/1098390/899820)

---

### Post by tbrodbeck on 2019-03-06
I have the same issue here with my MacBook Pro late 12. Any help appreciated!

The only thing that helps is to use xrandr (in a script or with second screen) to disable and reenable my display.

> **im.tak said:**
> I had the same problem, after i close the lid, the screen will not turn on. I followed instructions given by ubuntu faqs and it worked in one shot. 

**'INFO: This will not work for 12.04, resume from hibernate work differently in 12.04.**' 

[LIST=1]
[*]Pull up a Terminal again and run cat /proc/swaps  and hopefully you see the path to your swap partition listed there. If  not chances are something went wrong in the steps above. Here's my  output:
[/LIST]
Filename                                Type            Size    Used    Priority
/dev/sda2                               partition       2676732 73380   -1
[LIST=1]
[*]gksu gedit /etc/default/grub & to pull up the boot loader configuration
[*]Look for the line GRUB_CMDLINE_LINUX="" and make sure it looks like this (using your UUID of course) GRUB_CMDLINE_LINUX="resume=UUID=41e86209-3802-424b-9a9d-d7683142dab7" and save the file
[*]sudo update-grub and wait for it to finish
[*]gksu gedit /etc/initramfs-tools/conf.d/resume & and make sure its contents are resume=UUID=41e86209-3802-424b-9a9d-d7683142dab7 (with your UUID of course in place of mine). Save the file!
[*]sudo update-initramfs -u
[*]Reboot!
[/LIST]

[https://askubuntu.com/a/1098390/899820](https://askubuntu.com/a/1098390/899820)

Did you also have the issue only sometimes or every time of waking up your device from sleep? It seems to me these are two different issues.
Additionally gksu is deprecated in 18.04

---

