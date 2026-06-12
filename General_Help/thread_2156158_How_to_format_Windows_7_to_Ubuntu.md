---
title: "How to format Windows 7 to Ubuntu"
date: 2013-06-20
forum: General Help
---

### Post by LiakosGR on 2013-06-20
Hello i want to format my laptop from W7 to ubuntu. how can i do this???

---

### Post by Vormeph on 2013-06-20
There's no need to format Windows 7 or your laptop. You need to get the .iso file for Ubuntu (or its variants) and burn them to a CD/USB. If you're going to burn the .iso file to a USB, use Unetbootin. Also, depending on which bit-format of Windows you are using (32-bit or 64-bit) you'd want to install Ubuntu as either 32-bit or 64-bit, respectively. Generally the amount of RAM you have is a good indication as to which bit-version you should be using. 

If you have two hard-drives, take note that you can only install Ubuntu on ONE of the hard drives. 

One more thing, you need to understand that once you click the 'Install' button, there's no going back; you enter the Linux world, and thus I welcome you! :-D

P.S. Change the BIOS settings on boot-up to make sure your USB boots first, rather than your hard drive. F2 usually is the key to use, but it should tell you on the BIOS screen when you first turn on your machine.

---

### Post by LiakosGR on 2013-06-20
so you tell me if i boot from the usb and i install ubuntu i will have only ubuntu or i will have both of them??

---

### Post by CharlesA on 2013-06-20
The installer lets you either install side-by-side or replace Windows with Ubuntu.

I always clone the drive before making modifications.

---

### Post by LiakosGR on 2013-06-20
so i have the option to choose what i want to do??

---

### Post by CharlesA on 2013-06-20
Yes.

---

### Post by oldfred on 2013-06-20
Several of these show the install process with screen shots so you have an idea of what will happen.

 Install options, Do not use erase entire drive unless that is really what you want.
[http://www.ubuntu.com/download/help/install-desktop-long-term-support](http://www.ubuntu.com/download/help/install-desktop-long-term-support)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)
Install 12.04- side by side auto install with screen shots
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) 

Best to do a full backup of Windows.
      
 The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by Vormeph on 2013-06-20
I suggest practicing the installation of Ubuntu through a Virtual Machine. That way, you'll get an idea as to what will come up on your actual screen once your mind is made up.

---

### Post by CharlesA on 2013-06-20
> **Vormeph said:**
> I suggest practicing the installation of Ubuntu through a Virtual Machine. That way, you'll get an idea as to what will come up on your actual screen once your mind is made up.

That is a good way to do it if your machine can handle virtualzation.

---

### Post by LiakosGR on 2013-06-21
my laptop i thing it will burn if i do this :P

i want to do this in my desktop later!!

---

### Post by LiakosGR on 2013-07-08
i was going to do it with my usb stick and i have ERROR 8000!! what is this??

---

### Post by oldfred on 2013-07-08
Not familiar with error 8000, at what point or where in boot process do you get this?

You should see BIOS, and with one time boot key choose USB as boot device. That will only work if you have correctly configured USB flash drive with bootable files.
Then you should get screens as shown in examples above.

If a video issue:
       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by LiakosGR on 2013-07-09
i have this error before start  format! both of usb and CD

---

### Post by LiakosGR on 2013-07-09
i solved the problem with error 8000 so i find new :P

[B]Failed to idle channel 2
Failed to idle channel 3[/B]

---

### Post by oldfred on 2013-07-09
These all seem to be system errors, not related to any software?? BIOS or hardware issues??

---

### Post by LiakosGR on 2013-07-10
i don't have any issues with w7 in my laptop!! and when i did format in my laptop i didn't have any problem!!!

---

### Post by oldfred on 2013-07-10
So what are the errors, without more info we cannot help. What system is this and what processor, RAM & video card/chip do you have?

---

### Post by leosubhadeep on 2013-07-11
_**[SIZE=3]It is always better to have both Windows and Linux (read Ubuntu) as dual-boot to get every type of applications[/SIZE]**_.

To use Ubuntu dedicatedly, **backup your important data** and run wubi.exe from Windows which is inside the Ubuntu package; after restart, you will be prompted to "Erase Windows and install Ubuntu"- you can do this if you want to. :)

---

### Post by Dale61 on 2013-07-11
Go [here]("http://www.ubuntu.com/download/desktop/windows-installer"), choose what best suits your hardware, then just follow the prompts.  I have a laptop with W7, so I had to go with a 12.04 LTS install, but at least it's better than the alternative.

---

### Post by LiakosGR on 2013-08-21
i have the same errors!! i have this laptop -> fujitsu siemens esprimo mobile v6555 [http://prntscr.com/1mmmk7](http://prntscr.com/1mmmk7)

---

### Post by oldfred on 2013-08-21
With nVidia you need nomodeset. Do you get the initial purple screen with tiny icons at bottom of a keyboard & person. Then press any key, then at f button choices chose f6 and select nomodeset.
You will also need nomodeset after install but have to edit the grub menu as you boot. 

This shows screens of both installer and after first boot only use the temporary settings.
       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

---

