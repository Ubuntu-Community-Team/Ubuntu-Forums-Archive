---
title: "Problem installing Ubuntu on new build"
date: 2017-12-15
forum: General Help
---

### Post by resiak1 on 2017-12-15
I just finished building my new PC and am having issues installing Ubuntu. 


  I'm not exactly sure what information would be useful for you guys but here are the specs of the build.

  

[LIST]
[*]Asrock OC Formula mobo 
[*]Intel i7-7820x 
[*]3 NVIDIA GTX 1080 FE's 
[*]4x16gb Corsair Dominator Platinum 
[*]Samsung 960 EVO M.2 500gb 
[*]EVGA Supernova 1600 T2 
[/LIST]

Not sure if it matters but after failing to install Ubuntu I tried to install Windows 10 and was successful. 


  Thank you in advanced!

Edit: Oops, forgot to include photo of error. Uploading now.

Here's the photo of the error.


.[IMG]https://lh3.googleusercontent.com/s1TYzDpyqO4wkB8f96E4_rTvkUBnrk_pMJGntWVibgyez55syZx5SABfFURa7D1W0ZXwa2sX6hcUaipuao0UljwxZ0JHu_TmPW7vzYPgKIKYV8rPoKWiFyh3Frkn6Hw6RinHYYXM=w664-h374-no[/IMG]

---

### Post by oldfred on 2017-12-15
Older Asrock had extra SATA port as ASmedia which do not work with Linux, not sure if yours still uses that configuration or not.
 Asrock Z170 ASmedia port issue
[https://ubuntuforums.org/showthread.php?t=2345564](https://ubuntuforums.org/showthread.php?t=2345564) 

Not sure about 3 nVidia cards.
But you may need nomodeset and will need to use ppa to get very newest nVidia driver. Do not download from nVidia.
Some have installed Ubuntu using Intel driver, then installed nVidia driver.
But even newest Intel may need a boot parameter.

This is for Intel.

 [https://www.phoronix.com/scan.php?page=article&item=coffee-uhd-graphics&num=1](https://www.phoronix.com/scan.php?page=article&item=coffee-uhd-graphics&num=1)
Now new Intel chips need this boot parameter:
 i915.alpha_support=1 

For nVidia you need nomodeset until you install the nVidia driver.
      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) 
    
      
 [https://askubuntu.com/questions/61396/how-do-i-install-the-nvidia-drivers](https://askubuntu.com/questions/61396/how-do-i-install-the-nvidia-drivers)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa 
   # should show newest versions available in addition
ubuntu-drivers devices 
    
If you attempt to change video drivers, you must totally purge old one first or they conflict and cause issues.


 ASUS PRIME Z370-A Running Great On Linux, needs i915.alpha_support=1 or Linux 4.15 kernel
[https://www.phoronix.com/scan.php?page=article&item=asus-prime-z370a&num=1](https://www.phoronix.com/scan.php?page=article&item=asus-prime-z370a&num=1)
ASRock Z370M-ITX/ac: Mini-ITX Motherboard With Dual NICs, WiFi, Triple Display For ~$130 USD Oct 2017
[https://www.phoronix.com/scan.php?page=article&item=asrock-z370m-itx&num=1](https://www.phoronix.com/scan.php?page=article&item=asrock-z370m-itx&num=1)

---

### Post by resiak1 on 2017-12-16
Thanks for all the info! Using nomodeset I managed to live boot Ubuntu from USB, however, when I go to install Ubuntu the option to install Ubuntu along side windows is missing. Do you have any idea why this would be and how I can fix it?

Thanks again, your help is much appreciated.



> **oldfred said:**
> Older Asrock had extra SATA port as ASmedia which do not work with Linux, not sure if yours still uses that configuration or not.
 Asrock Z170 ASmedia port issue
[https://ubuntuforums.org/showthread.php?t=2345564](https://ubuntuforums.org/showthread.php?t=2345564) 

Not sure about 3 nVidia cards.
But you may need nomodeset and will need to use ppa to get very newest nVidia driver. Do not download from nVidia.
Some have installed Ubuntu using Intel driver, then installed nVidia driver.
But even newest Intel may need a boot parameter.

This is for Intel.

 [https://www.phoronix.com/scan.php?page=article&item=coffee-uhd-graphics&num=1](https://www.phoronix.com/scan.php?page=article&item=coffee-uhd-graphics&num=1)
Now new Intel chips need this boot parameter:
 i915.alpha_support=1 

For nVidia you need nomodeset until you install the nVidia driver.
      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) 
    
      
 [https://askubuntu.com/questions/61396/how-do-i-install-the-nvidia-drivers](https://askubuntu.com/questions/61396/how-do-i-install-the-nvidia-drivers)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa 
   # should show newest versions available in addition
ubuntu-drivers devices 
    
If you attempt to change video drivers, you must totally purge old one first or they conflict and cause issues.


 ASUS PRIME Z370-A Running Great On Linux, needs i915.alpha_support=1 or Linux 4.15 kernel
[https://www.phoronix.com/scan.php?page=article&item=asus-prime-z370a&num=1](https://www.phoronix.com/scan.php?page=article&item=asus-prime-z370a&num=1)
ASRock Z370M-ITX/ac: Mini-ITX Motherboard With Dual NICs, WiFi, Triple Display For ~$130 USD Oct 2017
[https://www.phoronix.com/scan.php?page=article&item=asrock-z370m-itx&num=1](https://www.phoronix.com/scan.php?page=article&item=asrock-z370m-itx&num=1)

Never mind, I fixed it.

---

### Post by oldfred on 2017-12-16
Please post what settings you had to change, so others with similar systems can find solutions.

And you can then change to [Solved].

---

### Post by resiak1 on 2017-12-16
Will do. I'm still working on getting it all setup ATM. I was able to get the option to install along side windows by shrinking the windows partition. Now I'm working on installing the nvidia drivers.

I am having an issue updating the drivers. 

This is what I did,

sudo apt-get purge nvidia*

sudo add-apt-repository ppa:graphics-drivers

sudo apt-get update

sudo apt-get install nvidia-384.98 

[I]I also tried 384 instead of 384.98 and got the same results...

[/I]$ sudo apt-get install nvidia-384
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package nvidia-384

Any idea what I'm doing wrong?

Thank you!

I see that this person had a similar issue as I'm having. I tried all that was suggested but I continue to get the same results.

[https://ubuntuforums.org/showthread.php?t=2370033](https://ubuntuforums.org/showthread.php?t=2370033)

---

### Post by yancek on 2017-12-16
You might try another method of opening System Settings from the left panel (wrench/gear icon) and then clicking on  Software and Updates.  When the new window opens, you will see several tabs at the top including one for Additional Drivers so click that and wait for it to finish and see if it finds the drivers.

---

### Post by oldfred on 2017-12-16
Did you do a full purge between attempting installs of nVidia driver?

The ppa should give newest driver as options.
       #What is installed
dpkg -l | grep -i nvidia
dkms status
lsmod | grep nvidia 
   # Shows standard repository versions, which is the same as
System Settings, Software & Updates icon, Additional drivers tab
ubuntu-drivers devices 

 Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa 
   # should show newest versions available in addition
sudo ubuntu-drivers devices
If you just want default version - recommended one
sudo ubuntu-drivers autoinstall
Or you can manually choose any in list.
sudo apt-get install nvidia-XXX  

If installed and need to purge.
      
 If you have installed any version, you must purge first, old will conflict with new as new install does not overwrite old version.
sudo apt-get remove --purge nvidia-*
sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms
This xorg file may not exist, so if error that would be ok
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

---

### Post by resiak1 on 2017-12-17
> **yancek said:**
> You might try another method of opening System Settings from the left panel (wrench/gear icon) and then clicking on  Software and Updates.  When the new window opens, you will see several tabs at the top including one for Additional Drivers so click that and wait for it to finish and see if it finds the drivers.

I followed your instructions and it found NVidia-375. I applied the drivers and it is working now. The thing is, 375 is not the newest NVidia drivers. 

Thank you

I just now saw this post. I'll try out what you suggested. Thanks!


> **oldfred said:**
> Did you do a full purge between attempting installs of nVidia driver?

The ppa should give newest driver as options.
       #What is installed
dpkg -l | grep -i nvidia
dkms status
lsmod | grep nvidia 
   # Shows standard repository versions, which is the same as
System Settings, Software & Updates icon, Additional drivers tab
ubuntu-drivers devices 

 Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa 
   # should show newest versions available in addition
sudo ubuntu-drivers devices
If you just want default version - recommended one
sudo ubuntu-drivers autoinstall
Or you can manually choose any in list.
sudo apt-get install nvidia-XXX  

If installed and need to purge.
      
 If you have installed any version, you must purge first, old will conflict with new as new install does not overwrite old version.
sudo apt-get remove --purge nvidia-*
sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms
This xorg file may not exist, so if error that would be ok
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

Does this look right or do I need to purge some of these?

```
dpkg -l | grep -i nvidia
ii  bbswitch-dkms                               0.8-3ubuntu1                                 amd64        Interface for toggling the power on NVIDIA Optimus video cards
ii  libcuda1-387                                387.34-0ubuntu0~gpu16.04.2                   amd64        NVIDIA CUDA runtime library
rc  nvidia-381                                  381.22-0ubuntu0~gpu16.04.2                   amd64        NVIDIA binary driver - version 381.22
ii  nvidia-387                                  387.34-0ubuntu0~gpu16.04.2                   amd64        NVIDIA binary driver - version 387.34
rc  nvidia-opencl-icd-381                       381.22-0ubuntu0~gpu16.04.2                   amd64        NVIDIA OpenCL ICD
ii  nvidia-opencl-icd-387                       387.34-0ubuntu0~gpu16.04.2                   amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                0.8.2                                        amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                             387.22-0ubuntu0~gpu16.04.1                   amd64        Tool for configuring the NVIDIA graphics driver
jack@jack-desktop:~$ dkms status

```
```
dkms status
bbswitch, 0.8, 4.10.0-42-generic, x86_64: installed
bbswitch, 0.8, 4.4.0-104-generic, x86_64: installed
nvidia-387, 387.34, 4.10.0-42-generic, x86_64: installed


```
```
lsmod | grep nvidia 
nvidia_uvm            688128  0
nvidia_drm             45056  3
nvidia_modeset        897024  5 nvidia_drm
nvidia              13967360  328 nvidia_modeset,nvidia_uvm
drm_kms_helper        151552  1 nvidia_drm
drm                   352256  6 nvidia_drm,drm_kms_helper


```


Also, I can't seem to get my second display to work. I looked in display settings and it's not detecting the second display.

---

