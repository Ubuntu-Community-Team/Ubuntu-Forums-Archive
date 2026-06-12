---
title: "How to Install Windows on Ubuntu with a USB Drive?"
date: 2013-04-21
forum: General Help
---

### Post by Jason Kuzhively on 2013-04-21
I have a 4 GB Pen Drive on which I used UNetBootin to copy the .iso file into it. I tried to boot from the Pen Drive but I get this error:
```
BOOTMGR is Missing
Press CTRL+Alt+Del to Restart
```

I formatted my Pen Drive to NTFS and flagged it as bootable with GParted but this is the result I get when I try to boot from Ubuntu. I need help fast...

UPDATE: I found the solution, it's in post #19.

:guitar:

---

### Post by mikewhatever on 2013-04-21
We don't really support such requests here. Had you wanted to install Ubuntu, that would have been a different story, but for what you want, contact Microsoft.

---

### Post by Cheesemill on 2013-04-21
You could try using WinUSB.

[http://www.webupd8.org/2012/01/tool-to-create-windows-usb-install.html](http://www.webupd8.org/2012/01/tool-to-create-windows-usb-install.html)

---

### Post by Mark Phelps on 2013-04-21
> **Jason Kuzhively said:**
> I have a 4 GB Pen Drive on which I used UNetBootin to copy the .iso file into it. 
You don't copy the ISO file to the pen drive; you expand the ISO file onto the pen drive.  IF it's an ISO of a Windows bootable image, the drive will then be bootable as a result.

If you continue to have problems, you should post to the Windows 7 forums: sevenforums.com.

---

### Post by Jason Kuzhively on 2013-04-21
> **Mark Phelps said:**
> You don't copy the ISO file to the pen drive; you expand the ISO file onto the pen drive.  IF it's an ISO of a Windows bootable image, the drive will then be bootable as a result.

If you continue to have problems, you should post to the Windows 7 forums: sevenforums.com.

I didn't simply *copy *the ISO into the pen drive but I used Unetbootin to *expand *it on to the pen drive, I also tried WinUSB. Unetbootin didn't work at all for me and WinUSB just took me into some GRUB thingy.

---

### Post by Jason Kuzhively on 2013-04-21
> [COLOR=#000000]We don't really support such requests here. Had you wanted to Ubuntu, that would have been a different story, but for what you want, contact Microsoft.[/COLOR]

Thank you *very *much, but I have had enough of this "Ubuntu" thing...

---

### Post by C.S.Cameron on 2013-04-21
This tutorial is the only method of installing XP to USB that has ever worked for me.

[http://tdoui.webs.com/Install%20And%20Run%20Windwos%20XP%20From%20USB.pdf](http://tdoui.webs.com/Install%20And%20Run%20Windwos%20XP%20From%20USB.pdf)

It is much slower than running Ubuntu from USB.

---

### Post by Jason Kuzhively on 2013-04-21
> [COLOR=#000000]This tutorial is the only method of installing XP to USB that has ever worked for me.[/COLOR]

[http://tdoui.webs.com/Install%20And%...From%20USB.pdf]("http://tdoui.webs.com/Install%20And%20Run%20Windwos%20XP%20From%20USB.pdf")

[COLOR=#000000]It is much slower than running Ubuntu from USB.[/COLOR]

THANK YOU!!! But do you know how to extract these .IN_ Files???

---

### Post by C.S.Cameron on 2013-04-21
Edit:

Link removed.

---

### Post by Jason Kuzhively on 2013-04-22
Okay, That got rid of the BOOTMGR is missing error but now it takes me to some GNU GRUB thingy where Ubuntu and some other stuff is listed.

---

### Post by C.S.Cameron on 2013-04-22
Did you format the flash drive before installing XP?
You should only see the win boot loader.
Is the flash set as first hard drive in BIOS?

---

### Post by Slim Odds on 2013-04-22
You need to boot from that USB

You might want to try YUMI [http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/)

---

### Post by C.S.Cameron on 2013-04-23
> **Jason Kuzhively said:**
> Okay, That got rid of the BOOTMGR is missing error but now it takes me to some GNU GRUB thingy where Ubuntu and some other stuff is listed.

I have only managed to get SP1 & SP2 working, not SP3.

---

### Post by Jason Kuzhively on 2013-04-23
> **C.S.Cameron said:**
> Did you format the flash drive before installing XP?
You should only see the win boot loader.
Is the flash set as first hard drive in BIOS?

Yes, I did all that...

---

### Post by Jason Kuzhively on 2013-04-23
> [COLOR=#000000]I have only managed to get SP1 & SP2 working, not SP3.[/COLOR]

Please don't tell me that I have to get another Windows .iso file... :'(

---

### Post by C.S.Cameron on 2013-04-23
Sorry.

---

### Post by Jason Kuzhively on 2013-04-23
I FIGURED IT OUT!!!!!!!!!!!!!

First of all, I wanna thank @C.S.Cameron for helping me. The way I did it was ridiculously long but... It worked. I will probably post a new thread and post the instructions there. Again I wanna thank @C.S.Cameron, May you find peace O Brave Warrior from Lynn Valley... ;) :)

---

### Post by C.S.Cameron on 2013-04-23
If you got SP3 working I'm interested.

---

### Post by Jason Kuzhively on 2013-04-27
OK, Here is how I installed XP from my USB while Running Ubuntu. I haven't tested it with other Versions of Windows so try, there's no reason it *shouldn't *work. 
[CENTER][B]
Part I: Installing VirtualBox and Other Stuff.

[/B][/CENTER]


[LIST]
[*]Install VirtualBox on your Ubuntu, it's there in the Software Centre.
[*]Get your hands on a Windows ISO Image. If you have a Windows XP CD, then rip it with IMGBurn which you can find in the Software Centre.
[*]Open VirtualBox and Click the "New" Button.
[*]Use the Wizard to create a Virtual Partition for XP. In Operating System Drop-down select Microsoft Windows and in the Version Drop-down select Windows XP or whatever Version you are planning to use.
[*]Choose the amount of RAM to be allocated to this OS (when it's in use). Don't allocate too much because there will be less RAM for your host system to run, which will crash your entire system. Win-XP requires at-least 512 MB-Ram, but I would gived it atleast 800 MB.
[*]Create a new hard disk since you probably don't have one already. Click Next to Continue. You will be taken through the Create New Virtual Disk wizard, which will allow you to choose hard disk size, dynamically expanding/fixed size, etc.
[*]Review the summary it provides at the end and verify the information is correct. After that, the new Virtual Machine will be created.
[*]Mount the ISO image by clicking on the Settings button. Click the Storage section on the left hand side of the window. Click on the Empty CD medium in the Storage Tree.
[/LIST]

[LIST]
[*]Open the Virtual Media Manager, depicted with an icon like a folder with an up arrow, next to CD/DVD Device under "Attributes".
[*]Add the disk image file by clicking Add, then choosing the location of the Windows XP ISO image. Select it with "Select", then press OK in the Settings Window. Launch the VirtualBox by pressing "Start".
[*]Add the disk image file by clicking Add, then choosing the location of the Windows XP ISO image. Select it with "Select", then 
press OK in the Settings Window. Launch the VirtualBox by pressing "Start".
[/LIST]


[LIST]
[*]Install Windows. You should have the Windows installer running now. Remember that since you have not yet install the Guest
[/LIST]
        Additions, you will have to press your Host key (normally Right-Ctrl)

[LIST]
[*]Install Guest Additions. While the machine is running, under the "Devices" menu, click "Install Guest Additions", which will 
launch a setup wizard inside Windows XP. Now you will have OS mouse integration, so you won't have to press the host key to switch 
between your host and guest. You also can copy and paste between the two operating systems.
[/LIST]

[CENTER]
[B]Part II: Getting USB Devices to Work on your Virtual Machine. 
[/B][/CENTER]

Now go to About VirtualBox and find out which Version of VirtualBox you have. Go to this link --- [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads) and download the VirtualBox Extension Pack for the Version of VB you have. After downloading the Extension Pack for your version of VirtualBox, install it by opening it.
Now here are the steps for getting USBs to work on your Virtual Machine:




[LIST]
[*]After installing the extension pack, go to "Settings" and click on "USB," there are two check boxes, check 'em both.
[*]In Ubuntu, Go to *Systems > Administration > Users and Groups*, "Users and groups" is not installed by default in Ubuntu 11.10, 12.04 and newer, so you'll have to install it firstly:
[/LIST]
```
sudo apt-get install gnome-system-tools
```
[LIST]
[*]In *Users and Groups, *click on "Manage groups", scroll down to the "vboxusers" group and click "Propreties", then check the box next to your username and click OK.
[/LIST]

Then log out and log back in, plug in an USB stick (or whatever you may need), start a VirtualBox machine and select the USB device in the lower right.
[CENTER][B]
Part III: Preparing
[/B][/CENTER]


[LIST]
[*]In Ubuntu, Download Novicorp WinToFlash from [http://www.wintoflash.com/home/en/](http://www.wintoflash.com/home/en/). Make a new folder in /home/ and name it "WinUSB." Put the Windows ISO and WinToFlash in there.
[*]Open the VM Settings and go to Shared Folders. You can define them there. Click on the Add button, find and select the folder "WinUSB" in which we put the ISO and WinToFlash.
[*]Click "Start," Right Click on "My Computer" and choose "Map Network Drive." Choose any letter in the Drive Dropdown and in Folder, type in "\\vboxsvr\WinUSB" and click Finish. In My Computer, The Shared Folder will show up in Network Places with whatever Drive Letter you assigned to it. In this How-To, I will be using the "Z:"
[*]Get Virtual Clone Drive and use it to mount the ISO as a Virtual Drive by right clicking it and choosing Mount ----
[/LIST]
[CENTER][B]
Part IV: Finishing Up

[/B][/CENTER]

[LIST]
[*]Plug in an USB stick (or whatever you may need), start a VirtualBox machine and select the USB device in the lower right (The small USB icon.) The USB Drive should show up in your Virtual Machine.
[*]Open "Z:" and run WinToFlash after extracting it. Click the Big Tick Mark and the Wizard should start, in the Windows Files path, choose the Virtual Drive you set up using Virtual Clone Drive and in USB Drive, choose your USB Drive, it should be there in My Computer.
[/LIST]
[B]
Wait, this process will take at least half an hour.[/B] After it is done, set up your BIOS to boot from USB and it should boot from it now.

**Note:** I haven't tested this on any other version of Ubuntu, you can try, there is no reason it shouldn't work.:P

[I][B]Thanks To: C.S.Cameron from UbuntuForums.org, Elizabeth23 from XPForums.com, WikiHow, WebUPD8, Oracle and Novicorp.
[/B][/I]
This guide might have some mistakes, if you find one, the mail me --- [EMAIL="jackey.jaison@gmail.com"]jackey.jaison@gmail.com[/EMAIL].

---

### Post by Jason Kuzhively on 2013-04-27
The Reason I switched from Ubuntu to Windows is *not *because I simply wanna throw hate at Ubuntu, it's because my PC simply doesn't agree with Ubuntu. After I switched to Windows, I tried Linux Mint and I'm Loving It. I would have stuck with Ubuntu if it didn't throw tons of errors at me, I think my PC and Ubuntu don't... uh, go together or something :confused:

---

