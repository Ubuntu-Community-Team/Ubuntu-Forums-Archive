---
title: "Help with installing nvidia drivers in ubuntu 15.04"
date: 2015-05-22
forum: General Help
---

### Post by imokpro on 2015-05-22
I am a new user to ubuntu 15.04, so I basically do not know much.

I did a clean install on my laptop with 15.04 version through DVD and chose the overwrite option.

First attempt I proceeded to chose the 340.06 nvidia proprietary drivers from settings, it gave me a reboot loop with "ACPI Probe Failed".

I reinstalled ubuntu again and tried installing 340.06 version through terminal, same thing happened. This time I uninstalled it through root kernel and laptop booted up again.

I tried 346.x version, same thing happened.

How can I fix this?

Graphic card is nvidia geforce 820m.

Regards

---

### Post by QDR06VV9 on 2015-05-22
> **imokpro said:**
> I am a new user to ubuntu 15.04, so I basically do not know much.

I did a clean install on my laptop with 15.04 version through DVD and chose the overwrite option.

First attempt I proceeded to chose the 340.06 nvidia proprietary drivers from settings, it gave me a reboot loop with "ACPI Probe Failed".

I reinstalled ubuntu again and tried installing 340.06 version through terminal, same thing happened. This time I uninstalled it through root kernel and laptop booted up again.

I tried 346.x version, same thing happened.

How can I fix this?

Graphic card is nvidia geforce 820m.

Regards

It is a harmless bug just ignore [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1430625](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1430625)
Unless you are not able to boot to your OS, is that the case?
Regards

---

### Post by imokpro on 2015-05-22
No, I can use the stock drivers that comes with linux. It just sucks cause I want to play some games that require nvidia graphic drivers.

But it was my own fault for installing 15.04 I guess, missed reading that it was under development.

Oh well, I can love without the games.

Thanks.

---

### Post by QDR06VV9 on 2015-05-22
If you want to get the nvidia driver installed?
Try doing
```
sudo apt-get remove nvidia*
```
Then if there was anything removed reboot.
**Setup for 14.04 and later**

 You need to open your [terminal]("https://help.ubuntu.com/community/UsingTheTerminal") and enter the commands below. 

[LIST=1]
[*]Enable the [Universe and Multiverse]("https://help.ubuntu.com/community/Repositories/Ubuntu") repositories in order to allow the bumblebee and nvidia packages to be installed: 
```
sudo apt-get install bumblebee bumblebee-nvidia primus linux-headers-generic
```
Reboot. 
More info here [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
To run your application with the discrete NVIDIA card run in the terminal: optirun [options] <application> [application-parameters] For example: 
optirun firefox For a list of options for optirun execute: 
optirun --help  Normally you do  not use optirun for your window manager,  installations, or other non-graphic, resource intensive programs. The  optirun command is mainly used for graphic demanding programs (ex.  games). 
[/LIST]
Best of Luck I used the exact method on a couple of my friends lappy's

---

### Post by monkeybrain20122 on 2015-05-22
> **runrickus said:**
> If you want to get the nvidia driver installed?
Try doing
```
sudo apt-get remove nvidia*
```
Then if there was anything removed reboot.
**Setup for 14.04 and later**

 You need to open your [terminal]("https://help.ubuntu.com/community/UsingTheTerminal") and enter the commands below. 

[LIST=1]
[*]Enable the [Universe and Multiverse]("https://help.ubuntu.com/community/Repositories/Ubuntu") repositories in order to allow the bumblebee and nvidia packages to be installed: 
```
sudo apt-get install bumblebee bumblebee-nvidia primus linux-headers-generic
```
Reboot. 
More info here [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
To run your application with the discrete NVIDIA card run in the terminal: optirun [options] <application> [application-parameters] For example: 
optirun firefox For a list of options for optirun execute: 
optirun --help  Normally you do  not use optirun for your window manager,  installations, or other non-graphic, resource intensive programs. The  optirun command is mainly used for graphic demanding programs (ex.  games). 
[/LIST]
Best of Luck I used the exact method on a couple of my friends lappy's


Maybe I am missing something. But where did OP say that he has an Optimius enabled machine? If Optimus is absence and you install bumble-bee with the Nvidia driver you will boot into a blackscreen. Bumble-bee automatically disables the Nvidia card since it asumes that there is an onboard Intel card. If there is no Intel card then you are left with nothing.

---

### Post by QDR06VV9 on 2015-05-22
> **monkeybrain20122 said:**
> Maybe I am missing something. But where did OP say that he has an Optimius enabled machine? If Optimus is absence and you install bumble-bee with the Nvidia driver you will boot into a blackscreen. Bumble-bee automatically disables the Nvidia card since it asumes that there is an onboard Intel card. If there is no Intel card then you are left with nothing.
See here  [http://www.geforce.com/hardware/notebook-gpus/geforce-820m](http://www.geforce.com/hardware/notebook-gpus/geforce-820m)

---

### Post by grahammechanical on 2015-05-22
I do not think that "ACPI PCC probe failed" is anything to do with the video driver. I have been seeing that through most of the 26 week development period of 15.04, which, by the way has been now released and and is described a "stable release."

I am still seeing that message now that I have moved on to the development version of 15.10. It does not stop Ubuntu from loading. The linked to bug report says this
>                         PCC (Platform  Communication Channel)  is a recent ACPI 5.0 addition. The driver does  not find a PCC communications mailbox and just exits with that error  message.  It is not something to worry about, most machines don't have  an ACPI PCCT table and they don't use this mechanism.

 References:

 ACPI specification Chapter 14.0 "Platform Communications Channel"
Linux source: drivers/mailbox/pcc.c


              



When you install the Nvidia driver through the terminal do you get any errors? When you restart does Ubuntu loaded to a working desktop?

Regards.

---

### Post by efflandt on 2015-05-22
Why would anyone want to install bumblebee when nvidia-prime works now (at least in 14.04)? I used bumblebee in 13.10 just because that was all that worked for me then with hybrid Intel/Nvidia graphics, but some games required extra parameters for optirun to work. And I never could get primusrun to work for anything at all.

Not sure which nvidia driver versions are available in 15.04 or which might be required for 820m, but for my older GTX 765m simply installing nvidia-331-updates worked in 14.04. NVIDIA X Server Settings allows switching from default Nvidia to Intel graphics, which requires relogging into X, but stays that way through reboots until you change it. Switching from Intel to Nvidia requires a reboot, but then that sticks through reboots until you change it. That may not be instant, but easier to figure out than which extra parameters might be needed for optirun.

---

### Post by mc4man on 2015-05-22
Try the highest version available, seems to be nvidia-346. 
Be aware that when on nvidia there will be no vsync if using Ubuntu (unity, compositing) So if that bothers you then use nvidia for games, intel the rest of the time.

To note - currently in 14.04.x the only mobile nvidia version is 331 which is broken on kernel 3.19. So if not fixed or if 34x nvidia isn't made available then the upcoming 14.04.3 should not be used on laptops with nvidia optimus if using nvidia drivers matters -
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331-updates/+bug/1409190](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331-updates/+bug/1409190)

---

