---
title: "Installing Firmware DVBSky S952."
date: 2016-12-28
forum: General Help
---

### Post by jbamford92 on 2016-12-28
Hi. I need some help. Im new to Linux so i have a lot of learning to do with Terminal of course. Im tryng to install Firmware for my DVB Sky S952 how ever ive installed Ubuntu 12.04 because i think thats what my card requires. Could someone please help me with the terminal commands. I dont understand this sorry to be a bit thick. 

---Compile and install driver
1)Enter the source code directory

2)Check and choose one of the target systems, run â&#8364;&#732;uname -aâ&#8364;&#8482; to get os informaton.
./v4l/build_x86.sh if build for 32 bit system os to support multi-standard, include DVB-T,DVB-T2 and DVB-C.
./v4l/build_dvbc_x86.sh if build for 32 bit system os to support DVB-C.
./v4l/build_x64.sh if build for 64 bit system os to support multi-standard, include DVB-T,DVB-T2 and DVB-C.
./v4l/build_dvbc_x64.sh if build for 64 bit system os to support DVB-C.

3)Compile the source code:
make

4)Install driver, which need super user privilege:
sudo make install

5)Install firmware
unzip dvbsky-firmware.tar.gz file, then run bst-firmware.sh
or copy *.fw to /Lib/Firmware.

6)Reboot computer.

7)Verify the installation is successful or not:
ls /dev/dvb
If the adaptor0 is list here so the driver is installed properly.

---FAQ
Situation:
Kernel message when loading the drivers.
"Unknown symbol..."
"Invalid parameter..."
"disagrees about version of symbol..."
Fix:
Step 1)
[s]sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/media/[/s] ***#Destructive command. Struck over by forum staff.***
Step 2)
sudo make install
Step 3)
reboot computer


Im trying to follow this. [https://www.linuxtv.org/wiki/index.php/DVBSKY_S952](https://www.linuxtv.org/wiki/index.php/DVBSKY_S952)

Thanks.

Jack.

---

### Post by DuckHook on 2016-12-28
Welcome to the forums, jbamford92

I have not looked at the rest of your post in great detail, but "Step 1" of your quoted FAQ is *atrocious* and will break your system. Any command of the type:```
sudo rm -rf
```…must be handled like hot nitroglycerin. It's application as per the quoted instructions:```
[s]sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/media/[/s]
```…is utterly irresponsible and will wipe out drivers needed for every bus on your computer. I know that you are new to Linux and you definitely haven't the slightest responsibility in this matter, but you may wish to contact the original authors of these instructions and demand that they retract such perniciously destructive advice.

Will look at the rest later, but for now, wanted to make sure that neither you nor others who may happen on this thread will execute such awful commands.

---

### Post by DuckHook on 2016-12-28
Now that I've had a chance to review the rest of it, here are some observations and advice:

Firstly, to the matter of safety and security:

[LIST=1]
[*]You showed great wisdom coming onto the forums seeking advice and guidance. While we encourage users to first Google for knowledge and instructions, you have clearly done so and turned to the community when you were not sure what results such instructions might yield. This is an excellent example of how to make good use of the forum resources and my hat is off to you.
[*]Your posting is a good example of the rule: only carry out commands when you *know* what they are designed to achieve. Never invoke commands that are blindly downloaded from the internet. There are a lot of malicious and/or incompetent people out there giving out bad instructions, both intentionally and unintentionally. The internet can be a dangerous place.
[/LIST]
Secondly, to the matter of your drivers:

[LIST=1]
[*]The instructions for creating your drivers are not trivial. They must be compiled from source. This is usually attempted only after a user has attained a certain amount of knowledge in and comfort with Linux. In the case of a user new to the OS, it is fraught with potential pitfalls.
[*]Is it impertinent of me to suggest that you may wish to get more comfortable with the command line before you try compiling source code? While it is possible to do so as steps in a recipe, there are many dangers, one of which has already been outlined above.
[*]I am unfamiliar with your card, but have you tried booting up without outside drivers? What happens when you do? In Linux, most drivers are either already part of the kernel or has the driver module precompiled as part of the distro. It is possible that your card already works and needs no special drivers. Then again, your card may be too obscure, and the reference to having to install firmware is not encouraging.
[/LIST]
You may wish to go through the links in my signature to familiarize yourself more with Ubuntu and Linux basics. If you wish a crash course that can lead to compiling ASAP, then especially: *A Great CLI Guide*

---

### Post by jbamford92 on 2016-12-29
Hi. Thanks for your reply. I tried doing it but I can't seem to use terminal very well. What would you suggest for driver wise? The card doesn't seem to be working with any TV software for Linux.

---

### Post by DuckHook on 2016-12-29
> **jbamford92 said:**
> &#8230;I tried doing it but I can't seem to use terminal very well.You are far from being alone. The Linux command line is intimidating to new users, myself included when I was first starting out. But everybody gets more comfortable with it through practice, and some pick it up quickly.> What would you suggest for driver wise?Unfortunately, in your case, there is no way around the necessity of the command line and compiling both the driver and the firmware if you want to get your TV card working. I don't want to be discouraging, but it may not work well (or at all) even if we manage to get it compiled. Sometimes, both code and instructions are not maintained and won't work on newer kernels.> The card doesn't seem to be working with any TV software for Linux.No app can use your card without the proper driver installed no matter how well coded the app is. However, if you are willing, the helpers on this forum are certainly prepared to help you through the compile process. You should expect a drawn out process of many days and postings, and taking one step back for every two steps forward.

The other options are to buy/use a card that is natively supported by Ubuntu (with drivers either built into the kernel or included as modules), or has precompiled binaries on its website for Ubuntu/Debian. I am unfamiliar with the function of your card, so haven't the faintest idea where to point you for such alternative hardware.

Why don't you take stock of your options and let us know how you would like to proceed? We aren't going anywhere and the forums are always available. No matter what you decide, I would encourage you to get more familiar with the command line through practice and with the help of the online book in my link. The command line will prove useful to you in many situations, and if you decide to proceed, it's much easier if you at least know how to change directories, list files, use sudo safely, type in commands, etc.

---

### Post by jbamford92 on 2017-01-01
Hi. Thought I'd report back. I've been doing a lot of experimenting. I installed the .fw file to /lib/firmware and updated the kernel. Got the card working in MythTV I'm a very happy chap after accomplishing this :D I've learnt a lot so far. All I can say is that I'm happy that I've ditched windows on my HTPC.

---

### Post by DuckHook on 2017-01-01
Marvellous! Congrats!

If you don't mind my asking&#8230; how did you do it? Compile from source? If you would provide a brief explanation, then mark this thread *solved*, it would help the rest of the community and anyone else with the same problem who comes across this thread.

---

