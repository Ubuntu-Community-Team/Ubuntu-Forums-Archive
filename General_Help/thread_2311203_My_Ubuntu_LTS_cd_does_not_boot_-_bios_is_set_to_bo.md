---
title: "My Ubuntu LTS cd does not boot - bios is set to boot cd/dvd"
date: 2016-01-25
forum: General Help
---

### Post by patrikmellq on 2016-01-25
Hello - i want to make a new fresh install of Ubuntu LTS - because i will install Tripwire.
But my computer start up very quick so the Ubuntu cd/dvd does not have time to load.
I have a gaming computer Acer with 64 bit.

I enter bios when pressing the key "delete".
Is there any other key i can press to get the cd/dvd up running.

Cheers

---

### Post by QDR06VV9 on 2016-01-25
Is there no key combo for boot option by F2 or F12?

---

### Post by patrikmellq on 2016-01-25
I will test clicking on F2 and if not working i will try F12.
I have to get my Ubuntu dvd up running so i can install from scratch with Tripwire.
Maybe i have to take picture of my bios setup, but is was working to run the Ubuntu dvd when i had windows 10 and i also use the same dvd to install Ubuntu on a IMAC ... so there nothing wrong with the dvd ...

---

### Post by yancek on 2016-01-25
> I enter bios when pressing the key "delete".

You should have a 'boot' tab when you get into the BIOS to change boot priority to the CD/DVD drive.

---

### Post by patrikmellq on 2016-01-25
Yes i have priority 1 for cd/dvd in bios and Ubuntu is on priority 2 - still Ubuntu start - but i can hear the dvd strart spinning.
When i test to press ESC it just say i should press DELETE to enter bios.

Press F2 and F12 is not working.

Cheers

---

### Post by Nuno_Abreu on 2016-01-25
Sometimes F8 or F9 are the keys to press.

---

### Post by patrikmellq on 2016-01-25
I will test to press F8 and F9 - here is one image of the boos setup - at the end of the configuration is say boot meny is disabled - but when i made it enabled is just add a text at the start up to press F12 and nothing happens - Ubuntu start. 

[IMG]http://i64.tinypic.com/ddnsw4.jpg[/IMG]

---

### Post by Nuno_Abreu on 2016-01-25
What about turning on that "Boot menu" option in your BIOS? It's disabled and that can be the problem - it seems it is directly booting to your hard drive, typical from manufacturers.

Also, disable "Quiet Boot" to see if it can also be the problem.

---

### Post by deadflowr on 2016-01-25
More likely a bad burn.
try again.

---

### Post by patrikmellq on 2016-01-25
Ok thanks - will try both options - first i will try to change bios settings again - if not working i will burn new image with new dvd ...

Cheers

---

### Post by Nuno_Abreu on 2016-01-25
> **deadflowr said:**
> More likely a bad burn.
try again.

Or this. But what's strange is the lack or inexistence of errors.

---

### Post by patrikmellq on 2016-01-25
I burn a new dvd on a new dvd and it was not working, i try again, this start to make me angry, maybe i should clean my hard-drive with g-parterd and force my dvd to run when i reboot my computer.
But then i might end up with no Ubuntu system and no starting dvd, i hate this situation.

---

### Post by ajgreeny on 2016-01-25
Have you considered trying to install with a USB install medium?
It has two main advantages; firstly it will run the live system faster than a DVD, and secondly, of course, it is reusable/rewritable.

Can we also know if this is a UEFI system, or are you using legacy BIOS/CSM?

---

### Post by QDR06VV9 on 2016-01-25
> **ajgreeny said:**
> Have you considered trying to install with a USB install medium?
It has two main advantages; firstly it will run the live system faster than a DVD, and secondly, of course, it is reusable/rewritable.

Can we also know if this is a UEFI system, or are you using legacy BIOS/CSM?
+1;)
It would also be good to know what model of acer he is using.:D

---

### Post by patrikmellq on 2016-01-25
I have Acer Predator G3-605
 I install a USB and change setting in bios, still not working.
All i know that i have rapid hard-drive that start up quick.
Don't know if i have UEFI or CSM but bios say never with setting of CSM, see picture at page 1 on this topic of my bios window.

 This is crazy.

---

### Post by patrikmellq on 2016-01-25
Guess what - i put my windows 10 cd into the computer and it say - press any key to boot from cd/dvd - so is working with windows 10 dvd.
 How or where can i read how to check hash or secure download key - when downloading Ubuntu LTS iso i should check the it has not been temporize.

---

### Post by JOHN_ELLIS on 2016-01-25
Just looking again at your boot menu at the bottom it says "boot menu [Disabled]" maybe that is why your drive is just booting into the operating system.

Hope this helps

John

---

### Post by patrikmellq on 2016-01-25
I change that to enable - but it only put a text in the left down corner and say press F12 to boot and its next to press DEL to acces bios.
When i click on F12 nothing happens - but i will try again - but i find it strange that my windows 10 dvd starts/booting - then it comes a line that say press any key to boot from cd/dvd ....

---

### Post by QDR06VV9 on 2016-01-25
> **patrikmellq said:**
> I change that to enable - but it only put a text in the left down corner and say press F12 to boot and its next to press DEL to acces bios.
When i click on F12 nothing happens - but i will try again - but i find it strange that my windows 10 dvd starts/booting - then it comes a line that say press any key to boot from cd/dvd ....
See if this helps it is about windows but the same applies for linux
[https://techanywhere.com/cant-boot-to-windows-7-dvd-only-to-windows-8-on-acer-predator-g3-605-ur20-bios-change-no-uefi-option-to-legacy-solved/](https://techanywhere.com/cant-boot-to-windows-7-dvd-only-to-windows-8-on-acer-predator-g3-605-ur20-bios-change-no-uefi-option-to-legacy-solved/)

---

### Post by patrikmellq on 2016-01-25
YES!!!! THANK YOU!!!

 The guide is working.
 Now i will install Ubuntu LTS from scratch and install Tripwire.
 I will install Tripwire database on a floppy and make it read only and configuration Tripwire to send me one email report each day.
 Super.

---

