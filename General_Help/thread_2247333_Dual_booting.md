---
title: "Dual booting"
date: 2014-10-07
forum: General Help
---

### Post by UncleMonty on 2014-10-07
I am currently dual booting ubuntu and linux mint, how do I go about changing the boot order so that ubuntu is the default option?

---

### Post by slickymaster on 2014-10-07
There’s a GUI tool for editing Grub 2 boot loader, it's called Grub-Customizer.

You can install it in Ubuntu using the PPA repository. Open a terminal window and run these commands one by one:```
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer
```With Grub-Customizer, highlight the OS entry and click the up/down arrow button to change its order. Or set the default OS in General Settings tab.

---

### Post by Impavidus on 2014-10-07
You can modify /etc/default/grub to make Ubuntu the default option. The system that is in control of grub (the last one installed or the last one to install an update to grub) usually puts itself on top of the list, so if Ubuntu is in control of grub it should be on top too.

---

### Post by UncleMonty on 2014-10-07
How can it be loaded please? The only instructions I can find are from 2011.

---

### Post by slickymaster on 2014-10-07
Once installed you can open it from the Unity Dash. Search for it in Dash, and then click on the icon, and it will open.

Alternatively you can start it from the terminal:```
gksu grub-customizer
```

---

### Post by yancek on 2014-10-07
Apparently you installed Mint after Ubuntu and you are using the Grub bootloader from Mint.  As suggested above, when booted to Mint, go to the /boot/grub/grub.cfg file and count down to the Ubuntu menuentry and put that number in the /etc/default/grub file as shown below.  In this instance, Grub counts from zero, so if Ubuntu is the third entry, you would replace the zero below with the number 2.

> GRUB_DEFAULT=0

Alternatively, boot into Ubuntu and open a terminal and run:  sudo grub-install /dev/sda

That will work if you have only one hard drive.  If you have more than one you need to indicate that.

---

### Post by grahammechanical on 2014-10-07
What I would do and I do it regularly because I have several installs of Ubuntu is load into Ubuntu and run

```
sudo update-grub
sudo grub-install /dev/sda
```

Assuming that you only have one hard disk and that both OS are on the same hard disk.

The last Linux we install puts its own Grub into the MBR and the Grub menu is then controlled by the Grub configuration files of the last installed OS. If you had installed Ubuntu after Linux Mint then Ubuntu would be in control of the Grub mennu and Ubuntu would be at the top of the list. Running those commands from whatever install of Linux we want in control of the Grub menu will change things.

Regards.

---

### Post by oldfred on 2014-10-07
Grub Customizer modifies grub scripts and adds its own scripts. Often better to just manage it yourself.

If you just want to change order but have Ubuntu first just follow yancek's suggestion. Easier than adding grub customizer.

But if you want Ubuntu's grub in MBR so it controls booting and is first in boot order follow grahammechnical's suggestion.

But Mint may have its grub remembering where to reinstall on a major grub update. 

I know this works in Ubuntu, and would expect it to work in Mint. If you do not want Mints grub overwriting Ubuntu's grub uncheck all options.

If one drive both installs should show they reinstall to same drive's MBR.
       #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
It will show drive model & serial number
to see drive info
sudo lshw -C Disk -short 

      
 #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc or dpkg-reconfigure grub-efi-amd64
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

---

### Post by Dennis N on 2014-10-07
The simplest solution to the original question (change boot order) with just two OS installed is to change the value of GRUB_DEFAULT as yancek suggests. I'm sure he just forgot to mention it, but it needs to be added that after doing this, **sudo update-grub** needs to be run in the terminal, otherwise your grub menu will remain unchanged.

---

### Post by UncleMonty on 2014-10-28
> **grahammechanical said:**
> What I would do and I do it regularly because I have several installs of Ubuntu is load into Ubuntu and run

```
sudo update-grub
sudo grub-install /dev/sda
```

Assuming that you only have one hard disk and that both OS are on the same hard disk.

The last Linux we install puts its own Grub into the MBR and the Grub menu is then controlled by the Grub configuration files of the last installed OS. If you had installed Ubuntu after Linux Mint then Ubuntu would be in control of the Grub mennu and Ubuntu would be at the top of the list. Running those commands from whatever install of Linux we want in control of the Grub menu will change things.

Regards.

This worked! Thanks

---

