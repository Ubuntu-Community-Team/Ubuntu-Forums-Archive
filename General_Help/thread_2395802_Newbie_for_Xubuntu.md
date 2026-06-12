---
title: "Newbie for Xubuntu"
date: 2018-07-07
forum: General Help
---

### Post by czgirb on 2018-07-07
Ubuntu 14.04, just migrate to Xubuntu 18.04
I found there is so much UI differ

* Now, I able to directly play MP3 file from my external. But after re-start the path is unknown ... why?
--- I used DeaDBeeF

* Is there any System Monitor (Ubuntu's like) for Xubuntu? How to get it?

* I heard someone said that Thunar has a split view? How to activate it?

* I've tried to do a download. For a file, with capacity over than 100-MB ... it will be ending by FAILED. why?

Please guide me ... thanx

---

### Post by Autodave on 2018-07-07
Did you upgrade or did you do a clean install?

As for system monitor:  There is one that you can get to by right-clicking on the header of your desktop and then choose Panle -> Add New Items -> (scroll down) System Load Monitor.

---

### Post by Dennis N on 2018-07-07
> **czgirb said:**
> Ubuntu 14.04, just migrate to Xubuntu 18.04
I found there is so much UI differ
* Now, I able to directly play MP3 file from my external. But after re-start the path is unknown ... why?
--- I used DeaDBeeF
* Is there any System Monitor (Ubuntu's like) for Xubuntu? How to get it?
* I heard someone said that Thunar has a split view? How to activate it?
* I've tried to do a download. For a file, with capacity over than 100-MB ... it will be ending by FAILED. why?
Please guide me ... thanx

There is the **task manager** already installed (in System category), but I suggest you install **gnome-system-monitor**. It's the same as in Ubuntu's and shows more than task manager.
Thunar does not come with split-view. Use tabs or two windows side-by-side (or perhaps install a second file manager that has it.)
Don't know DeadBeef. I use Audacious as my player. No problem with it playing from external drive.
No idea about your download. Size should not be a factor. I would try again.

---

### Post by Holger_Gehrke on 2018-07-07
> **czgirb said:**
> 
* Now, I able to directly play MP3 file from my external. But after re-start the path is unknown ... why?
--- I used DeaDBeeF

If you mean a reboot of the whole machine, then external media connected during boot are not mounted automatically. You can mount a drive by selecting an option on the context menu of its icon on the desktop or opening it in the file manager. 
> **czgirb said:**
> 
* Is there any System Monitor (Ubuntu's like) for Xubuntu? How to get it?

xfce4-taskmanager. It's in the menu as Taskmanager. It will give you the workload on the CPU and use of RAM and swap along with a list of currently running processes. If you need more information on your system you can install the gnome-system-monitor (that's the one mainline Ubuntu is using; 'sudo apt install gnome-system-monitor' in a terminal or use the 'Software'-app) or set up conky (not for the faint of heart ... it's not a system monitor, it's a way of life). There are also several panel-applets that can show you system and network load.
> **czgirb said:**
> 
* I heard someone said that Thunar has a split view? How to activate it?

I think you heard wrong. I've been using Thunar since Ubuntu 12.04 and I've never seen Thunar with a split view. It does have a tabbed view, but since you can't see two or more tabs at once that's not the same thing at all.
> **czgirb said:**
> 
* I've tried to do a download. For a file, with capacity over than 100-MB ... it will be ending by FAILED. why?

Using what protocol, what client, through what kind of network connection to what server ... Without knowing all of these and more, any attempt to diagnose the problem is pure guesswork.

Holger

---

### Post by #&amp;thj^% on 2018-07-07
If a split view file manger is needed I recommend Double Commander.
I do not use it as default, I still also have Thunar and as Holger_Gehrke has advised Thunar has Tabbed option>>> again not the same as Split View.
Also I feel strongly about telling you tabbed browsing in Thunar has shown me here that I need to keep an eye on the tabs as they revert to a unselected directory when using the back keyboard or mouse action at times.

---

### Post by oldos2er on 2018-07-07
> **czgirb said:**
> Ubuntu 14.04, just migrate to Xubuntu 18.04
I found there is so much UI differ

* Now, I able to directly play MP3 file from my external. But after re-start the path is unknown ... why?

Is the external mounted on reboot? If not you'll see the behavior you describe.

> **czgirb said:**
> * I heard someone said that Thunar has a split view? How to activate it?

To my knowledge it doesn't, but you can open two instances of the program side by side if needed. Or you can use something like sunflower or mc.

---

### Post by czgirb on 2018-07-07
> **Autodave said:**
> Did you upgrade or did you do a clean install?

As for system monitor:  There is one that you can get to by right-clicking on the header of your desktop and then choose Panle -> Add New Items -> (scroll down) System Load Monitor.

clean install

**System Load Monitor** ... installed. but it doesn't include **network, task manager,** and [B]each drive (storage) capacity
[/B]please help ...

---

### Post by czgirb on 2018-07-07
> **Dennis N said:**
> There is the **task manager** already installed (in System category), but I suggest you install **gnome-system-monitor**. It's the same as in Ubuntu's and shows more than task manager.
Thunar does not come with split-view. Use tabs or two windows side-by-side (or perhaps install a second file manager that has it.)
Don't know DeadBeef. I use Audacious as my player. No problem with it playing from external drive.
No idea about your download. Size should not be a factor. I would try again.


**gnome-system-monitor** is installed and provide info as desired ... thank you

---

### Post by oldos2er on 2018-07-07
Have you looked through the available panel applets? There's a network monitor, mount devices monitor, and more. If you're not seeing them you should install the package xfce4-goodies.

---

### Post by czgirb on 2018-07-07
> **Holger_Gehrke said:**
> 
If you mean a reboot of the whole machine, then external media connected during boot are not mounted automatically. You can mount a drive by selecting an option on the context menu of its icon on the desktop or opening it in the file manager.

would you mind to guide me how to mount a drive ... thank you


> **Holger_Gehrke said:**
> 
xfce4-taskmanager. It's in the menu as Taskmanager. It will give you the workload on the CPU and use of RAM and swap along with a list of currently running processes. If you need more information on your system you can install the gnome-system-monitor (that's the one mainline Ubuntu is using; 'sudo apt install gnome-system-monitor' in a terminal or use the 'Software'-app) or set up conky (not for the faint of heart ... it's not a system monitor, it's a way of life). There are also several panel-applets that can show you system and network load.

**gnome-system-monitor** is installed and works as wishes ... thank you


> **Holger_Gehrke said:**
> 
I think you heard wrong. I've been using Thunar since Ubuntu 12.04 and I've never seen Thunar with a split view. It does have a tabbed view, but since you can't see two or more tabs at once that's not the same thing at all.

ooo ... thank you for the information


> **Holger_Gehrke said:**
> 
... what protocol, what client, through what kind of network connection to what server ...

i'm using firefox to download a file from uploaded, my network is my local network and it via wi-fi ... i've tried it 3-times
*** i able to download the file completely via my windows computer ... at once

please help me ...


add ...
i followed the instructed provide by ... [https://tutorialforlinux.com/2018/04/03/how-to-install-latest-wine-xubuntu-18-04-bionic-lts/](https://tutorialforlinux.com/2018/04/03/how-to-install-latest-wine-xubuntu-18-04-bionic-lts/) ... to installed WINE.
but when i wish to run .exe ... i found no WINE
would you mind to tell me where is xubuntu placed my WINE?
when i run
> 
czgirb@czgirb-laptop:~$ wine --version
wine-3.0 (Ubuntu 3.0-1ubuntu1)
czgirb@czgirb-laptop:~$ 

please help me ...

---

### Post by Dennis N on 2018-07-07
> i followed the instructed provide by ... [https://tutorialforlinux.com/2018/04...04-bionic-lts/](https://tutorialforlinux.com/2018/04...04-bionic-lts/) ... to install WINE.
but when i wish to run .exe ... i found no WINE...where has xubuntu placed my WINE?

You need Windows installer for the program. Right click on windows installer and you should see option "Open with Wine Windows Program Loader". That should open the installer in wine and install the program itself. After install, you might get a launcher in the menu or maybe not. I can't say for sure as the wine I have runs in XFCE desktop. If not, you may want to make one. When wine installs your program, it informs you where it is to be installed. Pay attention. 

Wine has no GUI, except for **winecfg** which configures the wine environment. Run winecfg from terminal.

Look for tutorials on wine's web site or other places on internet.

---

### Post by czgirb on 2018-07-07
if my ... sudo fdisk -l ... is:
> 
Disk /dev/sda: 232,9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xe05e4f1e

Device     Boot    Start       End   Sectors  Size Id Type
/dev/sda1  *        2048  54687743  54685696 26,1G 83 Linux
/dev/sda2       54689790  58595327   3905538  1,9G  5 Extended
/dev/sda4       58595328 488396799 429801472  205G 83 Linux
/dev/sda5       54689792  58595327   3905536  1,9G 82 Linux swap / Solaris

Partition table entries are not in disk order.




Disk /dev/sdb: 465,8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x01bcefcf

Device     Boot Start       End   Sectors   Size Id Type
/dev/sdb1          63 976768127 976768065 465,8G 83 Linux
czgirb@czgirb-laptop:~$



if i wish to mount **sda4** permanently, i will use this
> 
sudo mount -t ext4 /dev/sda4 /mnt



if i wish to mount **sdb** permanently, i will use this
> 
sudo mount -t ext4 /dev/sdb /mnt


is that right? please correct me, if i'm wrong
thank you

---

### Post by Dennis N on 2018-07-07
mount will mount a file system until you un-mount or quit. People who want automatic mount at startup put an entry into /etc/fstab like this one I have to mount my data partition:
```
UUID=c3121154-ee33-418b-8c43-10377841e3c2 /mnt/Data ext4 defaults 0 2
```
A similar entry should work for you. Just change UUID and mount point to what you need.

Your 2nd display:
you can't mount /dev/sdb as that is not a partition. sdb1 would designate a partition.

BTW,
I also just answered your wine question in post #11.

---

### Post by czgirb on 2018-07-25
is there someone could tell me what is **extended**?
what is the differences between **extended** and **swap**?
as i remembered, i never create an **extended**, but ... how it was there???
please guide me ...

---

### Post by deadflowr on 2018-07-25
An extended partition is a partition that can hold multiple logical partitions.
The old standard partition scheme MBR could only create 4 primary partitions.
To get around this limitation it was given the ability to create one primary partition that could extend that by allowing many logical partitions within it.
So that's basically what the extended partition is.

This gives a somewhat better explanation I think:
[http://www.pcguide.com/ref/hdd/file/structPartitions-c.html]("http://www.pcguide.com/ref/hdd/file/structPartitions-c.html")

FTR, the newer GPT partitioning scheme can have many primary partition, thus making logical and extended partitions mostly moot.

---

