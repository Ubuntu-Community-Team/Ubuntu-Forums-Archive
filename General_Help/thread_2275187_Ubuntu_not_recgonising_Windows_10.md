---
title: "Ubuntu not recgonising Windows 10"
date: 2015-04-24
forum: General Help
---

### Post by Nuno_Faria on 2015-04-24
Ubuntu is not seeing Windows 10, Im getting mad. All i want is to dual-boot ubuntu or other variant of ubuntu with my windows 10. I have tried Ubuntu, Xubuntu, Lubuntu and Kubuntu and they have the same damn result.
In the other option to manage partitions i cant get it to do the damn thing. In ubuntu and other variants (except kubuntu) i can create partitions and stuff and it works except i get some error about the ROOT or / folder and i cant do things to it dualboot, In kubuntu the only difference is the buttons to do the partitions and stuff dont work and boot files are acting kinda weird...

---

### Post by yancek on 2015-04-24
It might help if you indicated what some error about ROOT was.  You're extremely short on facts, details and usefull information on your problem.  No information on the hardware you are using, the option to install you selected, the number of drives/partitions you have, whether you are using UEFI/GPT or MBR to boot.  Without at least this information, there is not much anyone can do to help except guess.

---

### Post by QIII on 2015-04-24
It might also be helpful if you would describe the process you are using to install.

You could also snap a few images with a cell phone so we can have a look at what you are seeing.

---

### Post by sotiris2 on 2015-04-24
Is windows 10 properly shutdown with fast boot disabled? If fast boot is enabled windows doesn't exactly 'close' its filesystem, ubuntu does not access them and therefore doesn't find windows. It will cause you a problem with getting the bootloader to recognize windows so can have the option to boot windows if you install while ubuntu installer does not see the window installation. 

The error that you get is because after you create the partition yourself you have to select it to be mounted at / (root). Select the partition you want in the installer, double click it and in use as dialog pick "use as ext4 filesystem" and in Mount point pick /. 

But make sure you shutdown windows properly first after disabling fast boot.

---

### Post by Mark Phelps on 2015-04-24
> Is windows 10 properly shutdown with fast boot disabled?Sorry, wrong parameter.

Fast Boot is a BIOS/UEFI option and is unrelated to hibernation.

The correct parameter is FastStartup.  You need to disable that in Win10, because otherwise, even when you ShutDown Win10, it goes into a new form of hibernation which keeps all open filesystems still mounted -- thus preventing you from mounting them again in Ubuntu.

Also, after you do this, make sure you use ShutDown to close Win10, not Restart.  Why? Because Restart causes Win10 to ignore the FastStartup disable option and automatically puts Win10 into hibernation.

---

### Post by Nuno_Faria on 2015-04-25
Where i disable FastStartup in windows...

---

### Post by yancek on 2015-04-25
> Where i disable FastStartup in windows... 

You need to enter the BIOS setup immediately upon booting the computer.  There will be a specific key you need to use to do this.  This key varies widely with different manufacturers and we don't know what you have so can't tell you anything other than to watch the screen as soon as you boot for a message:  Press ?? key to enter setup.  There will be a specific key such as F2, F10 or other in place of the ?? above.  If you posted some info on your hardware, someone else who uses it would probably be able to tell you which key.

---

### Post by Mark Phelps on 2015-04-25
Once again ... FastStartup is NOT a BIOS/UEFI option -- it is a hibernation option INSIDE Windows.

The link is to the tutorial on the Windos 8 forums -- where you need to go if you have Windows 8 questions: [http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html")

---

