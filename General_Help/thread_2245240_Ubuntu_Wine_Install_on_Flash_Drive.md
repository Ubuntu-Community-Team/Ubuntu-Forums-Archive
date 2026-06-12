---
title: "Ubuntu Wine Install on Flash Drive?"
date: 2014-09-22
forum: General Help
---

### Post by harry28 on 2014-09-22
I recently installed Linux Ubuntu on my Acer C720 Chromebook and it runs really good. However since the internal SSD is only 16GB and I have Chromeos and Ubuntu installed on the SSD plus programs for Chromeos, I have very limited space on the internal left. I want to install some Windows based programs since I need them for college work and I was wondering if it would be possible to install Wine and Windows programs on a Flash Drive (32GB)?. Or would it be better to get an SD card and use the internal SD card slot to install programs onto?

---

### Post by Mark Phelps on 2014-09-22
> I want to install some Windows based programs

BEFORE you attempt that, use the linked page to search for the apps and versions you want to run.  Not everything works well in Wine; some stuff doesn't work at all.  Anything not found, or rated less than Gold, is going to be a waste of your time installing: [http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true]("http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true")

---

### Post by grahammechanical on 2014-09-22
Whenever I have installed an application whether through the software centre or the terminal, I have never been asked to set a location for where the application is installed to. As far as I know the working parts of an application go in / and the folders inside /, and the user configuration file goes into /home.

I know that it is possible to install Linux in such a way that the folders in / are on their own partitions. But doing that with a removable drive will break the OS if it is loaded without the removable drive being plugged in.

Where is your data, the documents and such? Is it also on the internal SSD? You will better off, in my opinion, storing your data on an external USB flash drive as a way of creating space on the internal SSD. You could also remove any applications that you do not use. There must be some duplication of the kind of applications between the two OS. Do you need an email application in both OS? As an example.

Wine will install into the / folder but when wine installs a Windows application it will let you assign a folder into which the application is installed. Such as C:\programs. It may be possible to install the Windows programs on the Flash Drive.

Regards.

---

### Post by tom140 on 2014-10-12
Just curious if the OP was able to get this working by installing Wine programs only to the SD card/USB drive. I'm in the same boat with my chromebook.

---

### Post by sudodus on 2014-10-12
You can install a whole and separate operating system on a USB pendrive or flash card, and boot from it. If it has fast flash hardware, it can work quite well. See these links

[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)
[Link to USB 2 and USB 3 speed tests for installers]("http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085")
[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

---

### Post by tom140 on 2014-10-13
> **sudodus said:**
> You can install a whole and separate operating system on a USB pendrive or flash card, and boot from it. If it has fast flash hardware, it can work quite well. See these links

[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)
[Link to USB 2 and USB 3 speed tests for installers]("http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085")
[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")


Oops I already went with the 'whole install' on my chromebook. I'll attempt this once my 32gb sd card comes later this week. ;)

---

### Post by Mike_Walsh on 2014-10-13
> **sudodus said:**
> You can install a whole and separate operating system on a USB pendrive or flash card, and boot from it. If it has fast flash hardware, it can work quite well.

A big +1 to sudodus on this one. I have recently (last week in fact) done JUST this with Kubuntu. I'm writing this in Chromium, in Kubuntu, on a 64 GB SanDisk CruzerBlade flash drive at this very moment. I have /, /home, and swap partitions in place; it works very well indeed. And because it's the entire OS, I also have Wine installed, specifically to run ONE graphics application that I cannot find an exact equivalent for in the repositories... *sigh* :D

Graham's quite right, too. You would do better to move your data to the external flash drive, thereby freeing up space on the internal SSD; this would, I feel, work rather better for you.

Regards,

Mike.

---

### Post by Mike_Walsh on 2014-10-13
> **tom140 said:**
> Oops I already went with the 'whole install' on my chromebook. I'll attempt this once my 32gb sd card comes later this week. ;)

You should find this works just as well on an SdCard as it does on a flash drive... :p

And, as with a flash drive, you can take it with you, and use it on any machine you can plug it into. You can, of course, purchase an SD cardreader quite cheaply, which will allow you run it from a USB port if you don't have a card slot to plug into.

Regards,

Mike.

---

### Post by tom140 on 2014-10-13
> **Mike_Walsh said:**
> You should find this works just as well on an SdCard as it does on a flash drive... :p

And, as with a flash drive, you can take it with you, and use it on any machine you can plug it into. You can, of course, purchase an SD cardreader quite cheaply, which will allow you run it from a USB port if you don't have a card slot to plug into.

Regards,

Mike.


Sounds good. I wasn't sure which class speed to purchase so I just went with class 10 assuming it's the fastest for the SD card.

---

### Post by Mike_Walsh on 2014-10-14
Hi, Tom.

I don't think the class speed rating for SD cards is quite as critical in this instance as it is in the SD card's natively intended setting (i.e. photography and video recording), as these both require the card to be able to write huge chunks of data at high speed; more so with the issue of recording video.

However, it certainly won't hurt to purchase one or two with the highest speed rating you can reasonably afford. SD cards are dirt cheap nowadays; there's no reason at all why you couldn't do more than one OS install, so that you've a choice of what to use each time! ;)

Regards,

Mike.

---

