---
title: "Installing Ubuntu from an ipod to my computer"
date: 2008-06-11
forum: General Help
---

### Post by Killaspike on 2008-06-11
Can I just extract all the files from my ubuntu iso onto my ipod or any external hard drive and install ubuntu from that?

I want to install ubuntu but I have no cd-rw/dvd-rw to write it to.

And I want to get rid of windows and not have a dual boot.

---

### Post by cszikszoy on 2008-06-11
This is a guide from the eeeuser.com wiki.  This guide uses windows.  There was a guide somewhere to do this in linux, for 7.10, but I think I remember reading that it didn't work for 8.04.  Anyways, if you're using windows, this should work for you:

1. Prepare the Flash Drive with a Bootable Ubuntu Distribution 
    We will be installing Ubuntu on our flash drive, so first remember to back up all the information you have stored there as it will be erased. 
    In order to install Ubuntu correctly, it is necessary to make the device Ubuntu is being stalled from &#8220;bootable&#8221;. This means that when the device is plugged into the computer during the computer's boot process, the computer will boot from the device rather than the computer's internal memory. 

    -On your Windows computer, download the UB8Convert utility from Pendrivelinux.com and run UB8convert.exe. A folder called &#8220;Ubuntu8&#8221; will be created on your Desktop. Place your .iso file containing Ubuntu i 1. Prepare the Flash Drive with a Bootable Ubuntu Distribution 
    We will be installing Ubuntu on our flash drive, so first remember to back up all the information you have stored there as it will be erased. 
    In order to install Ubuntu correctly, it is necessary to make the device Ubuntu is being stalled from &#8220;bootable&#8221;. This means that when the device is plugged into the computer during the computer's boot process, the computer will boot from the device rather than the computer's internal memory. 
    
-On your Windows computer, download the UB8Convert utility from Pendrivelinux.com and run UB8convert.exe. A folder called &#8220;Ubuntu8&#8221; will be created on your Desktop. Place your .iso file containing Ubuntu inside the &#8220;Ubuntu8&#8221; folder. 
    
-Run the &#8220;fixu.bat&#8221; script inside the &#8220;Ubuntu8&#8221; folder. Read through the prompts and wait until the script has successfully terminated. After the script finishes, a new folder called &#8220;USB-Ubuntu&#8221; will be created in the &#8220;Ubuntu8&#8221; folder. 
    
-Insert your USB flash drive into the USB port on your Windows computer. Copy all the files in the &#8220;USB-Ubuntu&#8221; file onto your flash drive. All files copied must be copied to the root directory of the flash drive, not another folder. 
    
-Once the files are copied to the flash drive, open the flash drive in Windows Explorer and run the &#8220;makeboot.bat&#8221; script. Follow the script prompts and wait until the script finishes. Once the script has finished, eject your USB flash drive. 
    Your USB flash drive is now a bootable Ubuntu 8.04 LTS install disk! 
nside the &#8220;Ubuntu8&#8221; folder. 
    
-Run the &#8220;fixu.bat&#8221; script inside the &#8220;Ubuntu8&#8221; folder. Read through the prompts and wait until the script has successfully terminated. After the script finishes, a new folder called &#8220;USB-Ubuntu&#8221; will be created in the &#8220;Ubuntu8&#8221; folder. 
    
-Insert your USB flash drive into the USB port on your Windows computer. Copy all the files in the &#8220;USB-Ubuntu&#8221; file onto your flash drive. All files copied must be copied to the root directory of the flash drive, not another folder. 
    
-Once the files are copied to the flash drive, open the flash drive in Windows Explorer and run the &#8220;makeboot.bat&#8221; script. Follow the script prompts and wait until the script finishes. Once the script has finished, eject your USB flash drive. 

Your USB flash drive is now a bootable Ubuntu 8.04 LTS install disk!

---

### Post by Killaspike on 2008-06-11
> **cszikszoy said:**
> This is a guide from the eeeuser.com wiki.  This guide uses windows.  There was a guide somewhere to do this in linux, for 7.10, but I think I remember reading that it didn't work for 8.04.  Anyways, if you're using windows, this should work for you:

1. Prepare the Flash Drive with a Bootable Ubuntu Distribution 
    We will be installing Ubuntu on our flash drive, so first remember to back up all the information you have stored there as it will be erased. 
    In order to install Ubuntu correctly, it is necessary to make the device Ubuntu is being stalled from “bootable”. This means that when the device is plugged into the computer during the computer's boot process, the computer will boot from the device rather than the computer's internal memory. 

    -On your Windows computer, download the UB8Convert utility from Pendrivelinux.com and run UB8convert.exe. A folder called “Ubuntu8” will be created on your Desktop. Place your .iso file containing Ubuntu i 1. Prepare the Flash Drive with a Bootable Ubuntu Distribution 
    We will be installing Ubuntu on our flash drive, so first remember to back up all the information you have stored there as it will be erased. 
    In order to install Ubuntu correctly, it is necessary to make the device Ubuntu is being stalled from “bootable”. This means that when the device is plugged into the computer during the computer's boot process, the computer will boot from the device rather than the computer's internal memory. 
    
-On your Windows computer, download the UB8Convert utility from Pendrivelinux.com and run UB8convert.exe. A folder called “Ubuntu8” will be created on your Desktop. Place your .iso file containing Ubuntu inside the “Ubuntu8” folder. 
    
-Run the “fixu.bat” script inside the “Ubuntu8” folder. Read through the prompts and wait until the script has successfully terminated. After the script finishes, a new folder called “USB-Ubuntu” will be created in the “Ubuntu8” folder. 
    
-Insert your USB flash drive into the USB port on your Windows computer. Copy all the files in the “USB-Ubuntu” file onto your flash drive. All files copied must be copied to the root directory of the flash drive, not another folder. 
    
-Once the files are copied to the flash drive, open the flash drive in Windows Explorer and run the “makeboot.bat” script. Follow the script prompts and wait until the script finishes. Once the script has finished, eject your USB flash drive. 
    Your USB flash drive is now a bootable Ubuntu 8.04 LTS install disk! 
nside the “Ubuntu8” folder. 
    
-Run the “fixu.bat” script inside the “Ubuntu8” folder. Read through the prompts and wait until the script has successfully terminated. After the script finishes, a new folder called “USB-Ubuntu” will be created in the “Ubuntu8” folder. 
    
-Insert your USB flash drive into the USB port on your Windows computer. Copy all the files in the “USB-Ubuntu” file onto your flash drive. All files copied must be copied to the root directory of the flash drive, not another folder. 
    
-Once the files are copied to the flash drive, open the flash drive in Windows Explorer and run the “makeboot.bat” script. Follow the script prompts and wait until the script finishes. Once the script has finished, eject your USB flash drive. 

Your USB flash drive is now a bootable Ubuntu 8.04 LTS install disk!


I did all this and my computer just goes into an endless reboot cycle before getting to windows when I have my ipod plugged in, when I take it out windows boots

---

### Post by cszikszoy on 2008-06-12
Pretty sure you can't do this with an IPOD.  You need to do it with a flash drive, or some type of media that you can completely format.  Pretty sure you can't completely format the IPOD.

Try this with a flash drive (2gb min) and it should work.  It worked fine for me with a 2gb with ubuntu 7.10

---

### Post by WeEatVista on 2008-06-12
I don't think there is a way for you to completely format an iPod, so don't try using an iPod to install Linux. Just go to your local computer store and pick up a 2GB USB flash drive, it will work a lot better. If you search google, there are multiple ways of installing Linux to USB drives. For more ways on how to do this you might want to check out [http://www.pendrivelinux.com]("http://www.pendrivelinux.com")

Hope this helps,

-We Eat Vista

P.S. I found somewhere where you could actually buy USB drives with Ubuntu 8.04 all ready to use, but they were about 10 dollars more than a regular USB drive and I don't remember the sight name.

---

