---
title: "How do I run Ubuntu from a flash drive?"
date: 2021-07-22
forum: General Help
---

### Post by z-q on 2021-07-22
I want to run Ubuntu from a flash drive. When I search for how to do that, I end up at this page: [https://ubuntu.com/tutorials/create-a-usb-stick-on-windows](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows)

However, I tried that, and it is not what I want at all. The procedure there creates a flash drive that will boot, then give you the option to either "try" Ubuntu or install Ubuntu on the computer's drive. If you "try" Ubuntu, you seem to be in a temporary environment. Changes you make, to the startup applications for instance, don't sustain.

I just want to run Ubuntu from the flash drive, plain and simple. I don't want the user to choose "try" vs. "install" at startup, and I don't want configuration changes to be rolled-back at the end of the session. I want to run Ubuntu normally, but from a flash drive. How do I do that?

---

### Post by monkeybrain20122 on 2021-07-22
You can create the flash drive with persistence. How to do it depends on the software you use to create the live usb. The option should be pretty visible.

---

### Post by grahammechanical on 2021-07-22
To create a USB drive having Ubuntu 20.04 with persistence you might try using this software.

[https://www.linuxuprising.com/2019/08/rufus-creating-persistent-storage-live.html](https://www.linuxuprising.com/2019/08/rufus-creating-persistent-storage-live.html)

Regards

---

### Post by z-q on 2021-07-22
Thanks. I will try that.

I seem to be missing something here. Why isn't "persistence" the default? Why would anyone ever want not-persistent?

---

### Post by monkeybrain20122 on 2021-07-22
> **z-q said:**
> Thanks. I will try that.

I seem to be missing something here. Why isn't "persistence" the default? Why would anyone ever want not-persistent?

Because most people only use the live usb to try out and install Ubuntu, not as a 'real' system. You can even do a real installation on a usb drive (not as a liveusb) but in my experience the performance is no good, if you install on an external hard disk then it has the same performance as an installation to internal hard disk except it may take longer to boot. I used to have a portable ubuntu installation that I can boot up different computers but now with secure boot and what not probably would only work on the computer on which it is created.

---

### Post by C.S.Cameron on 2021-07-22
**Persistent Install vs Full install**


Ubuntu can be installed to a USB in different ways. A Live install does not save between sessions. A Persistent install extracts the OS from a compressed file and saves data to an overlay file or partition each session, and a Full install installs the complete OS to the USB just like an install to internal disk.

**Comparison between Persistent and Full install USB**

[B]Advantages of a persistent install:
[/B]
1) You can use the persistent pendrive to install Ubuntu to another computer.

2) A persistent install takes up less space on the pendrive.

3) You can reset the pendrive by overwriting the old casper-rw file with a new one.

4) The install to pendrive takes less time.

5) Slightly less wear on the drive.

**Advantages of a Full install:**

1) You can update and upgrade.

2) If you have problems or wish to modify, the solution is the same as with an internal install, (You can ask for help in the forums).

3) No ugly startup / install screen.

4) Better security, you can use full encryption 

5) You can use proprietary drivers.

6)  Swapfiles and partitions work and Hibernation can be enabled.

7) Many persistent installs are limited to a 4GB casper-rw and a 4GB home-rw persistence file, to get more persistence requires persistence partitions. Once casper-rw is full, the drive will not boot.

8) More efficient usage of disk space. Does not require reserved space for persistence.

9) Faster boot, **no automatic disk checking** or Try Ubuntu/Install Ubuntu screen.

10) You can run VBox and use virtual machines.

11) Generally faster boot than Live or Persistent USB's.

12) More stable, better for day to day use. I have run Ubuntu off a flash drive for 5 years making only LTS upgrades.

Note that once booted, both methods run at about the same speed. If the computer has lots of RAM Ubuntu should run mainly in RAM and there will not be a big difference between running off internal HDD and USB3 flash drive f.

**Full Install Method**

A quick and easy method to flash a Full install to USB can be found here: [https://askubuntu.com/questions/1300454/easy-full-install-usb-that-boots-both-bios-and-uefi](https://askubuntu.com/questions/1300454/easy-full-install-usb-that-boots-both-bios-and-uefi)

A more traditional methods for creating a Full install USB from scratch can be found here: [https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-st](https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-st)

---

### Post by z-q on 2021-07-23
Thanks to everyone for the replies. I understand much better now. I see that the thing I wanted to do, which I thought was simple and common, is actually complicated and uncommon. I will try to work through the step-by-step guide.

---

### Post by ActionParsnip on 2021-07-23
Just install to the USB stick using a different USB stick. The fact that it is USB doesn't make any difference to Ubuntu in any way. A disk is a disk

---

### Post by yancek on 2021-07-23
It may not be that common but if you do a search here at the forums or online for 'create persistent ubuntu usb', you will find many hits.  There are also a number of tools you can use but it depends upon what OS you are currently using.  Doing an online search or searching these forums should give a lot of results.  Some of the tools make it very simple, others are not so easy but I would hardly call it complicated

Some tools are:  Universal USB Installer, Unetboootin, Etcher, mkusb,

---

### Post by HermanAB on 2021-07-23
Just install Ubuntu the usual way and select the flash device as the target drive.  There is no need for the ‘persistance’ complication.   I’ve run machines that way for years.

---

### Post by z-q on 2021-07-23
I am following the step-by-step instructions at the post C.S.Cameron  linked to here:  [https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-st](https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-st)

I am stuck at this step: "Copy the boot and the EFI  folders from the Ubuntu ISO file to the boot,esp partition sdx3." If I  understand correctly, it is telling me to extract two folders from an  ISO file and copy them onto a partition. How do I extract folders from  an ISO file? And what is the syntax to specify a partition as the  destination for a copy command?

---

### Post by z-q on 2021-07-23
I think maybe I figured it out. For extracting the folders from the ISO, I found boot and EFI folders in the /cdrom folder, so I'm going to assume that's what the instructions were referring to. To use the partition as the destination for a copy command, I could find no solution except to mount the partition. I ended up with this:
> cd /mnt
sudo mkdir sdc3
sudo mount /dev/sdc3 /mnt/sdc3
sudo cp -r /cdrom/boot /mnt/sdc3
sudo cp -r /cdrom/EFI /mnt/sdc3
sudo unmount /dev/sdc3
sudo rmdir sdc3
Hopefully, that worked. I'll find out when I get to the end of the procedure.

---

### Post by z-q on 2021-07-23
Update: Everything worked. Thank you, C.S.Cameron, for the excellent instructions.

Unfortunately, the resulting OS is unusably slow. I don't know why. When I created a bootable Ubuntu install USB and chose "Try Ubuntu", the performance was good. This full install performs much, much worse. It takes about 15 minutes to boot. Launching an application takes several minutes. And sometimes, everything just freezes for 5 minutes or more.

I am going to give up on this project for now and see if I can find another approach to what I want to do.

---

### Post by ajgreeny on 2021-07-23
Your experience is not a great surprise to me.

If using a USB2 flash drive in a USB2 port everything will be severely limited by the read/write and transfer speeds of USB2 which are simply too slow for an OS.
USB3 will be much better but still relatively slow.

A live system, even with persistence is running mainly if not totally in RAM so runs very much faster.

---

### Post by z-q on 2021-07-23
Ajgreeny, Thanks for the feedback.

I must be a dunce here because I'm just not getting it. I understand that RAM is faster than flash memory, but why is my full install using RAM less efficiently than the "Try Ubuntu" version? Functionally, the two versions look substantially the same, so why can't my full install use RAM the same way and be just as fast?

Admittedly, my version is saving changes to the flash drive that the "Try Ubuntu" version isn't saving, but the performance difference is far more than can be explained by the few configuration changes I've made. My version is at least 10x slower. Does my operating system really need 90% of its time to read and write a pittance of user data?

---

### Post by C.S.Cameron on 2021-07-23
How much RAM does the computer have? Perhaps try the drive on a different computer.

---

### Post by z-q on 2021-07-24
> **C.S.Cameron said:**
> How much RAM does the computer have?
I don't know, but if the amount of RAM matters this much, then I'm pursuing the wrong solution.

I don't require Ubuntu for my application. I can probably get the functionality I need from one of the minimalist Linux distributions, so I'm researching that option now.

---

### Post by sudodus on 2021-07-24
It can work well to run Ubuntu from a USB drive, as installed system as well as persistent live. But if not, there are several alternatives within the Ubuntu family of flavours. The flavours are developed and maintained by volunteers. And you might be able to find a faster USB drive.

Please tell us the specification of your computer, if you want help that can focus on the bottlenecks of your computer.

- Brand name and model of the computer (or motherboard if you put it together yourself).
- Brand name and model of the CPU
- Brand name and model of the graphics chip or card
- Amount of RAM.

These details can be found via the command

```

sudo lshw | less

```

I suggest that you try an Ubuntu 20.04.x LTS flavour with a light foot-print, **Lubuntu, Ubuntu MATE or Xubuntu**, as a **persistent live** system.

It is rather easy to create a persistent live system if you have an Ubuntu system - install and use [mkusb](https://help.ubuntu.com/community/mkusb).

In Windows you can use [Rufus](https://help.ubuntu.com/community/Installation/FromUSBStick/fromWindows#preview). With the correct settings you will find the slider and you 'drag it to the right' to get as much drive space as possible for persistence.

These links (and links from them) can be helpful:

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[Installation/FromUSBStick/pre#Notes_about_speed](https://help.ubuntu.com/community/Installation/FromUSBStick/pre#Notes_about_speed)

---

### Post by z-q on 2021-07-24
This community is great. I appreciate that you guys are trying to engage with my problem, even though I haven't given you many details. Let me explain what I'm doing, and maybe that will put things in a different perspective.

I volunteer for a search and rescue agency. We have a couple of vehicles with computers mounted on the dashboard. This week, the drive in one of the computers failed. We will fix the problem by replacing the drive or the computer (not sure which yet). Red tape being what it is, that will take a couple of weeks. In the meantime, this vehicle is out of service for ops assignments. Most of the applications we run from the vehicles are browser-based, so I figured maybe I could eliminate the downtime by making a bootable flash drive that launches a browser and remembers the passwords needed to log-in to various websites. As you can see from my comments in this thread, I have tried, but so far failed, to do so.

With apologies to my teammates, it is important that the boot procedure be idiot-proof. A Grub screen of boot options won't be understood. Thus, my goal is to make a bootable flash drive that launches a browser on startup, remembers data generated during the session, and shows no prompts during startup. The no-prompts-during-startup requirement seems to be a significant sticking point. That's why I can't use what everyone is calling the "persistent" approach.

I appreciate the questions about the computer specs, but I really won't know what they are until the next time I go to the station. The computers are fairly recent modern PC laptops (and good ones too – we don't buy cheap stuff). Any solution which will work on a typical PC should work on these computers. Any solution which requires high performance hardware, I'm not interested in.

Anyway, I never intended to pour a lot of time into this project. Giving up won't be a failure. But if anyone knows a quick way to create a bootable USB drive like I am describing, now that you know the full story of what I'm doing, please let me know.

---

### Post by sudodus on 2021-07-25
Thanks for these details, z-q,

Now I understand that what you need is an installed system, that you can configure to be very easy to use. Since you had problems with the USB pendrive, *probably* caused by slow performance, maybe also by some other bottleneck, I suggest that you get an SSD drive connected via USB3 or a standard [SATA-]SSD and a box that will connect it to USB3 (the box should be a physical container plus a USB3 to SATA adapter). Your organization should get that for less than 100 &#8364; or US $100, and my experience is that it will perform well.

You install from a standard live Lubuntu, Ubuntu-MATE or Xubuntu iso file to this SSD drive just like it were an internal drive. This will be easy when there is no internal drive connected (or when the internal drive is dead).

If you have only and need only open source Linux drivers and no proprietary drivers (for graphics and wifi), such an installed system in a USB3-connected SSD will perform almost as well as an installed system.

---

### Post by z-q on 2021-07-25
Thank you for the suggestion. I will have time to pursue the SSD box idea later this week. I'll let you know how it goes.

---

### Post by HermanAB on 2021-07-25
Note that flash devices come with different speed ratings.  A 10x device will definitely result in a much faster system than an old and tired widget from your junk box…

---

