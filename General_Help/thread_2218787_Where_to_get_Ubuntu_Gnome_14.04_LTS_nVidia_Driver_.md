---
title: "Where to get Ubuntu Gnome 14.04 LTS nVidia Driver GTX 750ti"
date: 2014-04-22
forum: General Help
---

### Post by macsociety on 2014-04-22
Have a PC with nice nVidia GTX 750ti video card.  Right now it does not boot with video the new Ubuntu Gnome 14.04 LTS so I have had to boot from my motherboards built in Intel 4000 video to at least install and run.  I would like to download a driver that will allow me to switch to the nicer GTX 750ti if at all possible.

Where do I download the driver and which version should I get offering best chance of allowing me to run properly.

Thanks

TJ

---

### Post by nuttzo31 on 2014-04-22
Are you able to boot up the livecd?

Maybe your card is too new for the open source drivers to support properly?

If you can boot to the recovery menu from grub you should be able to enable networking,drop to root and then type sudo apt-get install nvidia-331-updates to install nvidia proprietary.

---

### Post by nuttzo31 on 2014-04-22
Actually it looks like you might need the nvidia 334 or ever 337 drivers for that card, you will have to use the xswat ppa.

---

### Post by nuttzo31 on 2014-04-22
Ok i looked up some more and you should be able to do it like this.

Boot recovery kernel from grub menu, enable networking and then drop to root shell.

For latest beta run
[HTML]sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-337[/HTML]
 
OR

For latest stable run
[HTML]sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-334[/HTML]
  

reboot and you should be good to go.

---

### Post by oldfred on 2014-04-22
Does not have details on installing, but does show it works.

 Maxwell 750 
[http://www.phoronix.com/scan.php?page=article&item=evga_geforce_gtx750&num=1](http://www.phoronix.com/scan.php?page=article&item=evga_geforce_gtx750&num=1)
[http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell_750linux&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell_750linux&num=1)

---

### Post by macsociety on 2014-04-22
> **nuttzo31 said:**
> Are you able to boot up the livecd?

Maybe your card is too new for the open source drivers to support properly?

If you can boot to the recovery menu from grub you should be able to enable networking,drop to root and then type sudo apt-get install nvidia-331-updates to install nvidia proprietary.

Hi, no I get a black screen with blinking cursor booting from the LiveCD if I try to use the nVidia card.

Therefore I switched in Bios to the motherboard video card and booted from CD fine.  Then installed Ubuntu Gnome 14.04 LTS.

Can I now just boot like I do now and run the commands you mention below in Terminal.... have the drivers install... then reboot into Bios switching boot to nVidia card instead, and it run fine that way.

I have no idea on how to boot into GRUB as you mention.

What I can say is I run Ubuntu Gnome 14.04 LTS fine now but form my motherboards video card and want to switch to nVidia card once I get the correct drivers installed.

I take it both stock drivers running on my motherboards video right now and the new nVidia version can co-exist? and just depending on what video card I enable in BIOS is how it chooses what video driver to use?

So hopefully I can just boot and use terminal to type in these commands you told me to:
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-337
Let me know please.

TJ

---

### Post by nuttzo31 on 2014-04-22
> **macsociety said:**
> Hi, no I get a black screen with blinking cursor booting from the LiveCD if I try to use the nVidia card.

Therefore I switched in Bios to the motherboard video card and booted from CD fine.  Then installed Ubuntu Gnome 14.04 LTS.

Can I now just boot like I do now and run the commands you mention below in Terminal.... have the drivers install... then reboot into Bios switching boot to nVidia card instead, and it run fine that way.

I have no idea on how to boot into GRUB as you mention.

What I can say is I run Ubuntu Gnome 14.04 LTS fine now but form my motherboards video card and want to switch to nVidia card once I get the correct drivers installed.

I take it both stock drivers running on my motherboards video right now and the new nVidia version can co-exist? and just depending on what video card I enable in BIOS is how it chooses what video driver to use?

So hopefully I can just boot and use terminal to type in these commands you told me to:
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-337
Let me know please.

TJ

I am not sure if you can install the nvidia drivers while using the onboard graphics, try and see what happens.

If not you should be able to do a reinstall with a live cd, you might have to append nomodeset when booting the live cd to get basic graphics and then install. 

After install to get to the grub menu is a matter of pressing shift just as grub boots to bring up the grub menu.Then just select advanced options and choose the kernel that has recovery on it.Look at this page here 

[http://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu](http://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu)

Also use the nvidia-334 package don't use the nvidia-337 as i have found it to be too buggy.

---

### Post by macsociety on 2014-05-15
Update.... had the time to try this and it failed.  Had to boot from LiveCD and re-install the OS.  :(

I tried the apt-get install nvidia-334 and although all installed, reboot of system froze me out.

I am no Linux expert and don't know much.

Maybe I need to exlain a tad more.

My Maingear has onboard video port that works fine with Ubuntu Gnome 14.04LTS.  Running that now via HDMI cable from PC to LED Display.  Boots to CD or HD fine in this motherboard on-board video port that is Intel 4000 I believe graphics.

Now booting to CD or HDD switching BIOS to turn off on-board ram and instead using nVidia 750 DVI port, I can't boot in either.  Screen goes black very early on booting just to CD and I have blinking cursor up top.  So some video issue obviously.

Now running from HDD and installing the nVidia driver I thought would install this driver but LEAVE ALONE the driver I am already using now so both can be accessed.  I guess that is not how it goes.

Install of the nVidia driver seems to go fine, I reboot system and it fails to boot from on-board video now.  Get a frozen Gnome logo screen and never gets past that.  So I adjust BIOS to turn off on-board and switch to PCI port the nVidia is on.  Tried to boot but then black screen like before, blinking cursor, nothing else.

So appears I must somehoe try to get a bootable CD or something that will allow me to boot while nVidia card is selected in BIOS and then install driver and maybe it will work?

I just not sure how to make a CD to make that happen.

I am a bit clueless in that.

TJ
> **nuttzo31 said:**
> Ok i looked up some more and you should be able to do it like this.

Boot recovery kernel from grub menu, enable networking and then drop to root shell.

For latest beta run
[HTML]sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-337[/HTML]
 
OR

For latest stable run
[HTML]sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-334[/HTML]
  

reboot and you should be good to go.

---

### Post by oldfred on 2014-05-15
You may need to add a ppa for the newer kernel, not yet in Ubuntu.
[http://ubuntuforums.org/showthread.php?t=2214805](http://ubuntuforums.org/showthread.php?t=2214805)

If you do not have nVidia installed yet, and it is booting with nVidia you need nomodeset.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
If not nVidia then you may need these:
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

