---
title: "Can't shut down Ubuntu 9.4"
date: 2016-01-15
forum: General Help
---

### Post by nipplewise on 2016-01-15
>>> [http://i.imgur.com/izbUkfO.jpg](http://i.imgur.com/izbUkfO.jpg)

This is the only CD I have with linux on; any other usb key installation does not work.
Updates are not an option as well because of disk space.
_Is there any quick fix for this?_
The only way to shut down the PC is to select Restart and then us the On/Off button on the case.
Shut down itself and then Off don't work; the machine keeps restarting with this combo.

```
---[ end trace 18fce2fe5d9bb322 ]---
```

This is where the screen halts at first.
Then the after that, the loop goes on periodically with the successive lines.

---

### Post by Bucky Ball on 2016-01-15
*Thread moved to **General Help**.*

Welcome. 9.04 it is woefully out of date and you will be extremely lucky to get any help with it. It is no longer supported by Canonical or the forums. Things have changed so much since 9.04 most of us wouldn't, and don't, remember much about it.

Why not download a supported version and try that? If it is an old machine then Ubuntu probably won't run now, but Lubuntu or Xubuntu probably will, and they will look a lot more like 9.04 (which the supported Ubuntu doesn't).

If you are talking about having no room for updates for 9.04, there aren't any. They finished five and a half years ago. That release hasn't had security updates in that time either so I would avoid going online with it.

If you need help with trying a recent version, just ask.

---

### Post by nipplewise on 2016-01-15
Firefox is not running properly and I cannot even install Chrome (*Go back on page* is not working) because of low disk space:
```
There is not enough room on the disk to save /tmp/2rPWsL3o.deb.part.
Remove unnecessary files from the disk and try again, or try saving in a different location.
```
The command **df -H** gives me:
```
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda5              2.5G   2.4G      0 100% /
tmpfs                  387M      0   387M   0% /lib/init/rw
varrun                 387M   111k   386M   1% /var/run
varlock                387M      0   387M   0% /var/lock
udev                   387M   156k   386M   1% /dev
tmpfs                  387M   541k   386M   1% /dev/shm
lrm                    387M   2.9M   384M   1% /lib/modules/2.6.28-11-generic/volatile
overflow               1.1M   1.1M      0 100% /tmp
```
I have plenty of space on the disk though.
What would be the best solution? 
I'll stick to Restart for the moment.
**I want to be able to run updates and save files.**

---

### Post by Bucky Ball on 2016-01-15
Read post #2. Read reply posts before posting. Thanks.

There are NO updates to run on that ancient, unsupported release. What you have is what it is. Done, finished, kaput. You will not be able to install anything from the repositories or update as the repos no longer exist. :|

---

### Post by nipplewise on 2016-01-15
Sorry, I only saw your reply when I already had posted mine.
I guess I'll try and install Lubuntu.
**What would be the best way to burn the Lubuntu iso from Windows 8.1?**
Would the Windows burning utility do it without issues?

---

### Post by Bucky Ball on 2016-01-15
Not sure about that. I don't use Windows to create disks and only use USB installs nowadays. You can use either of these in Win to create a Ubuntu USB installer:

UNetbootin:
[www.unetbootin.sourceforge.net](www.unetbootin.sourceforge.net)

Universal USB Installer:
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

How much RAM does the machine have? [Ubuntu Gnome]("http://ubuntugnome.org/") is another option which is apparently fairly lightweight and would be similar to 9.04 in appearance I would think (it uses the gnome desktop environment which was used in 9.04, but 'modernised').

And there's [Xubuntu]("http://xubuntu.org/"). Lightweight and my choice as easy to customise.

PS: For burning an install disk on Win, [see here]("https://duckduckgo.com/?q=create+ubuntu+dvd+windows"). You burn a disk image. Do NOT create a data disk (drag and drop the ISO file). Common mistake. ;)

---

### Post by nipplewise on 2016-01-15
Thank you. 
Unfortunately I have attempted several times without success to install another version using a USB stick.
Even choosing the stick from the boot list won't work.
I used the program from pendrivelinux.com and tried with another one too.
I think the problem stems from the motherboard: it's old.
**There's only one DIMM of RAM, 1 GB total**, but plenty of space on the partition I used for Ubuntu 9.4.
**I'll burn an up to date distro to disk and see what happens**.

---

### Post by grahammechanical on 2016-01-15
Instructions on how to burn a DVD in Windows

[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)

Regards.

---

### Post by leunam12 on 2016-01-15
Try Rufus, It is very good, but maybe your USB stick is defective.

---

### Post by SeijiSensei on 2016-01-15
You only have 2.5G available in that partition.  That's not nearly enough for any new version of Ubuntu.  Usually you need at least 10G free, especially if /home is included in the same partition.  If you indeed have "plenty of space on the disk" you'll need to repartition at installation.

---

### Post by kurt18947 on 2016-01-16
> **There's only one DIMM of RAM, 1 GB total**, 

I think you'd want a 32 bit version as well, rather than 64 bit. Lubuntu does seem quite usable these days. LXLE, an Lubuntu spin would be another consideration.  Don't forget MATE, an update of classic gnome2 which is also pretty lightweight.  I find it not unusual for machines older than a few years to have issues with USB boot. Not all but some - it appears to depend on the BIOS writer.

---

### Post by mörgæs on 2016-01-16
The partitioning does indeed look strange. Please run ```
sudo lshw -short -C disk
``` and post the results in CODE tags.

---

### Post by nipplewise on 2016-01-16
[FONT=lucida console][FONT=arial]The installation of Lubuntu 15.10 crashed. Could this be a problem of space as well? **df -h**:[/FONT]

```
lubuntu@lubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            360M     0  360M   0% /dev
tmpfs            75M  5.2M   70M   7% /run
/dev/sr0        747M  747M     0 100% /cdrom
/dev/loop0      681M  681M     0 100% /rofs
/cow            372M  224M  148M  61% /
tmpfs           372M     0  372M   0% /dev/shm
tmpfs           5.0M  8.0K  5.0M   1% /run/lock
tmpfs           372M     0  372M   0% /sys/fs/cgroup
tmpfs           372M  3.9M  368M   2% /tmp
tmpfs            75M  4.0K   75M   1% /run/user/999
/dev/sda6       2.3G  2.3G     0 100% /target
```
[FONT=arial]I choose the *install Lubuntu over Ubuntu* option.
I think I'm going to wipe all these partitions using a Windows disc (which I'm familiar with) and then do a "clean" install on the main 100 GB partition. [/FONT][/FONT]

---

### Post by Bucky Ball on 2016-01-16
> **nipplewise said:**
> 
I think I'm going to wipe all these partitions using a Windows disc (which I'm familiar with) and then do a "clean" install on the main 100 GB partition. [/FONT][/FONT]

Good idea. You can also boot from Ubuntu install media, choose the option 'Try Ubuntu', launch Gparted and wipe the partitions, then install Ubuntu directly by clicking the 'Install' icon on the desktop.

If you do it in Windows, just leave blank space. Don't create partitions. Win can't create anything Ubuntu can be installed on.

---

### Post by nipplewise on 2016-01-16
>>> [http://i.imgur.com/MSwU0Iq.jpg](http://i.imgur.com/MSwU0Iq.jpg)

I erased the partitions created by the previous installation.
Now I'm trying to install Lubuntu 15.10 again.
Unfortunately _there is no option for an automated installation, excluding the one that erases all the data_. [B]
sda3[/B] has data on it therefore I need to create partitions manually.
**sda2** is the target partition for the installation of Lubuntu.
Is this [http://goo.gl/6vxQD5](http://goo.gl/6vxQD5) a reliable guide?

---

### Post by nipplewise on 2016-01-16
I successfully installed Lubuntu.
Thank you all.

---

### Post by mörgæs on 2016-01-16
Good, please mark the thread 'solved'.

---

### Post by nipplewise on 2016-01-16
Done.

---

### Post by Bucky Ball on 2016-01-16
Great news! :) You're in the 21st century! 

I was going to throw in that if you chosse 'Something Else' when you get to the partitioning section of the install you can partition manually, which means you can retain the existing partitions and install Lubuntu in the free space. 

Maybe something for next time. Enjoy. :)

---

