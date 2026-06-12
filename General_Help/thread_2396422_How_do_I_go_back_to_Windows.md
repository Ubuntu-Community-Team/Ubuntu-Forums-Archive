---
title: "How do I go back to Windows?"
date: 2018-07-15
forum: General Help
---

### Post by whobiggs on 2018-07-15
how do I get rid of ubuntu and return to windows? Ubuntu has even more problems than win 10 did but I don't know how to go back. I cannot understand any of the tutorials, does anyone speak plain English for idiots? I copied  WIn 10 to USB stick but have no idea how to run it. I don't understand the commands and simply cannot find anything I'm referred to.

---

### Post by deadflowr on 2018-07-15
No one can help until we know what the current state of the setup is.
We can speculate on what you have in regards to Windows, but that is all we can do.
Please provide a breakdown of the current situation in full.
Information such as, 
Is this from a dual-boot setup?
Or did you originally have Win10 installed and wiped it to install Ubuntu?
What exactly was copied to the usb stick?
(did you copy some files, or copy the installation media?)
Little things like that go a long way.

---

### Post by yancek on 2018-07-15
What did you copy to the usb stick/  Was it the extracted windows iso?  If you had windows 10 installed when you bought the computer, it was probably UEFI install and in that case, you should see an otion o boot of whatever machine you have to boot from UEFI or enter the BIOS setup and have an option to boot windows.  Of course, if you installed Ubuntu over windows, that won't work so did you?  Do you still have a windows recovery partition on the drive?  Did you create a windows recovery CD when prompted on first boot of windows?  If so, you should be able to do that and recover the windows partition setting it to factory defaults.

If you have windows on a usb and can still boot Ubuntu, you should be able to boot it from the Ubuntu Grub.  You need to provide more information on the hardware such as the manufacturer of the computer (HP, Dell, Toshiba, etc.) and answer the above questions.

---

### Post by sgage on 2018-07-15
Unless you made something like a Macrium image of your Windows installation prior to installing Ubuntu, you can't simply roll back to Windows. You will need Windows installation media, and then you will need to reinstall Windows from scratch. You might have better luck at a Windows forum, like [https://www.tenforums.com/general-support/](https://www.tenforums.com/general-support/)

Your post is rather vague about what you copied to USB - as others have mentioned, please clarify so that we can better help you.

---

### Post by HermanAB on 2018-07-16
One problem that you may run into, is that Windows may not recognize your HDD as something that it can format again.  The Windows utilities are not the brightest.  The solution for that problem is to zero the first bit of the disk using something like "dd if=/dev/zero of=/dev/sda bs=1000 count=1000".  After that, the Windows installer should work.

---

### Post by dragonfly41 on 2018-07-16
> [COLOR=#000000]*I copied WIn 10 to USB stick but have no idea how to run it.*[/COLOR]

Refer to tutorials ... here is one ..

[http://uk.pcmag.com/operating-systems-and-platforms/88253/feature/how-to-run-windows-10-from-a-usb-drive](http://uk.pcmag.com/operating-systems-and-platforms/88253/feature/how-to-run-windows-10-from-a-usb-drive)

---

### Post by missmoondog on 2018-07-16
as others have said there's not nearly enough info to help you and if you didn't create an image of your windows install, you are simply screwed, no matter what you put on usb. only choice will be a clean install of windows now, probably.

as far as saying ubuntu has more problems than windows, especially windows 10, makes me wonder about a whole lot of things!

---

### Post by Mark Phelps on 2018-07-16
The OP clearly said "return to widows" -- the implication being that their PC came with Windows preinstalled,in their case, Win10.

If they simply overwrote Windows with Linux, and did not do the Live Media stuff first, then there's no telling what kind of driver issues they encountered after that.

So yeah -- they COULD have encountered lots of problems if their install did not load all the drivers they needed for their hardware.  And, I know from personal experience, such problems can range from easy to impossible to solve, especially with a PC that has newer hardware for which Linux drivers are not available.

To the OP -- you can't simply "copy Win10" to a USB stick and expect it to work.  Instead, you need to use this link to download and create Win10 install media:  [https://www.microsoft.com/en-us/software-download/windows10](https://www.microsoft.com/en-us/software-download/windows10)

Good Luck

---

### Post by whobiggs on 2018-07-17
Thanks to everyone for their replies, this is a HP Pavilion netbook and I've been told it does not have enough RAM. Win10 worked really quickly to begin with but now is dreadfull hence trying Ubuntu. However I clearly don't understand it sufficiently eg commands etc. The first time I boot it shows 3 red dots out of 5 and freezes so I have to restart and it goes ok although one of the first things I see is rows of "failed to alloc to mem" then it goes on to show boot options. I constantly have the cursor jumping to the top left and sometimes the activities view. I cannot play video's and have no sound. When writing it often jumps back to the start or further down the page meaning I keep writing but in the wrong place. It also freezes regularly and I have to click top right to try and get back to life again. With Windows I did know how to use the task manager to see what is unresponsive and to close it down but here I don't have a clue. It is not running dual boot, Win10 was wiped, It does not have a DVD slot but I backed up on USB. I have copied a Win installer to USB but there I'm stuck. Is this enough info to help?


I am not a computer expert and was around long before they were invented presumably unlike many of you.

So to those that are offended that I dare to criticize Ubuntu please don't be because not everyone knows what you do! Remember you were (I assume) ignorant once. [-X

---

### Post by Topsiho on 2018-07-17
Hello whobiggs,

From what you tell us it's not fair that you say Ubuntu creates more problems than Windows10. It is an other OS, and that is something quite different, in more than one way.
I guess that when booting it only shows 3 red dots instead of 5 means that it is searching for information that it can not find, or has information  which it can not store on the disk for further use. In the first case something went wrong when creating a bootable USB-disk, from the downloaded .iso (you downloaded it from Ubuntu, did you), and in the second case your computer has not enough RAM probably, which also explains it having become slow using Windows. Solution: putting in more RAM.

Using a new OS (an other OS) requires that you just learn to how use it, which is NOT difficult (even if you are already around for a long time, as you put it. Being myself around a long time too, I feel free to say so :) ).

So my best guess is that you persevere and start discovering Ubuntu (or other Linuxes), and discover what you have missed far too long by now.

Topsiho

---

### Post by yancek on 2018-07-17
> HP Pavilion netbook and I've been told it does not have enough RAM

HP has been making and selling the Pavilion for decades, how old is and how much RAM do you have?  This would be the bare minimum information needed to get started.  The problems you are reporting might be the result of your computer not having enough resources so that information will be useful.  If you are able to successfully boot Ubuntu, open a terminal and enter this command (hit the Enter key) and post the output here.

```
inxi -F
```

If you downloaded the windows installer and properly put it on a usb, you need to enter the BIOS/Setup when the computer first boots.  Watch the screen, usually in the lower left of the screen you will see a message telling you which key to use.  When you access the BIOS, look for Boot and Boot Options and set the usb first.

---

### Post by Mark Phelps on 2018-07-18
To repeat my comment, you can't simply "copy the Win installer to USB" and expect it to work. You need to use the Microsoft Media Creation Tool to create a working USB installation stick.

As to the RAM, I have Win10 running on 2GB very old laptop, so unless your PC has 1GB or less, you should have enough RAM to run Win10.

You should really check with the HP Support Forums for help in installing Windows on your laptop:  [https://h30434.www3.hp.com/](https://h30434.www3.hp.com/)

Good Luck

---

### Post by deepakdeshp on 2018-07-18
> **yancek said:**
> HP has been making and selling the Pavilion for decades, how old is and how much RAM do you have?  This would be the bare minimum information needed to get started.  The problems you are reporting might be the result of your computer not having enough resources so that information will be useful.  If you are able to successfully boot Ubuntu, open a terminal and enter this command (hit the Enter key) and post the output here.

```
inxi -F
```

If you downloaded the windows installer and properly put it on a usb, you need to enter the BIOS/Setup when the computer first boots.  Watch the screen, usually in the lower left of the screen you will see a message telling you which key to use.  When you access the BIOS, look for Boot and Boot Options and set the usb first.
The OP was running windows 10 successfully before installing Ubuntu. Definitely Ubuntu will require less resources than Windows 10

---

### Post by whobiggs on 2018-07-22
It is clearly corrupted I am having great difficulty even starting the computer. I've downloaded the win install media creation thing but then what do I do? I cannot click on it to run.

---

### Post by yancek on 2018-07-22
> [COLOR=#000000]The OP was running windows 10 successfully before installing Ubuntu. [/COLOR]

Running it, but how successfull quoting from the OP post below.  Posting the amount of RAM would be useful.

> [COLOR=#000000] I've been told it does not have enough RAM. Win10 worked really quickly to begin with but now is dreadfull[/COLOR]

If you can boot Ubuntu, you can boot the windows installer from Grub in Ubuntu if you are able to follow the simple instructions at the link below.

[http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)

---

