---
title: "Error mounting fstab"
date: 2014-07-14
forum: General Help
---

### Post by Leonardo_Pinheiro on 2014-07-14
I have read many questions and answers in this and other forums before asking. I watched videos on Youtube to learn how to deal with the fstab file too.
  So forgive me for bringing back this doubt again.
  When I start may computer, soon after I choose Linux in Grub, my  screen turns black and Ubuntu does not start. When I push the reset  button, I do the same thing again and, this time I receive this message:
  **An error occurred while mounting /etc/fstab**

  **Press S to skip mounting or M for manual recovery**
  It happens every time. I have to reboot to start Ubuntu 12.04.
  My /etc/fstab looks like this:
```

# /etc/fstab: static file system information.
#
# -----------------------------------------------------------------
# Partitions description:
#   /dev/sda1 -> Created by Windows7 with boot informations
#   /dev/sda2 -> Windows 7
#   /dev/sda3 -> Linux
#   /dev/sda4 -> Drivers and some programs
#
#   /dev/sdb2 -> External HD
#
# -----------------------------------------------------------------
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# nodev,noexec,nosuid
# ------------------------------------------------------------------
#
#Entry for /dev/sda3 :
UUID=2679ab6c-2da8-48eb-8b7b-5f11833934cc / ext4 relatime,errors=remount-ro 0 1  
# ------------------------------------------------------------------
#
#Entry for /dev/sda4 :
UUID=29811C914EAB7D93 /media/drivers ntfs-3g defaults,nosuid,nodev,locale=en_US.UTF-8 0 0  
# ------------------------------------------------------------------
#
#Entry for /dev/sda1 :
UUID=7A8A5F338A5EEAE1 /media/System\040Reserved ntfs-3g defaults,nosuid,nodev,locale=en_US.UTF-8 0 0  
# ------------------------------------------------------------------
#
#Entry for /dev/sda2 :
UUID=749CCF049CCEBFBA /windows ntfs-3g defaults,locale=en_US.UTF-8 0 0  
# ------------------------------------------------------------------
#
#Entry for /dev/sdb2          
UUID=01CF9881FC472D80 /media/externalHD ntfs-3g defaults,locale=en_US.UTF-8 0 0  
#
# ------------------------------------------------------------------
#
UUID=12aed398-6f8b-44e6-abe4-c47fef0b751d none swap sw 0 0  
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0


```

---

### Post by steeldriver on 2014-07-14
Are you sure your /etc/fstab has the # at the start of the first line? the error message kind of suggests it's trying to mount a device called '/etc/fstab'

---

### Post by Leonardo_Pinheiro on 2014-07-14
Unfortunatelly I am sure the # is there. But you are in the right track. When I type
```

sudo mount -a

```
I receive the message that the first line is bad.

---

### Post by Bashing-om on 2014-07-14
Leonardo_Pinheiro; Hello;

What release are you running ?
In my 14.04 release the proc line is no longer used ..........
However in my 12.04:
```

proc            /proc           proc    nodev,noexec,nosuid 0       0

```
As the 'proc' line is the 1st line parsed.
Note that a 'default' is not used here.
Might try and change the line and see what results.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by steeldriver on 2014-07-14
Maybe there are some non-printing characters that we're not seeing - what does

```

sed '1!d' /etc/fstab | xxd

```

show?

---

### Post by Leonardo_Pinheiro on 2014-07-14
Hey,

I have just notice something!

I was in Windows when I replyed your message, [**[COLOR=#C61919][B]steeldriver**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1627500"). Then I rebooted the machine and chose Linux inside GRUB, just like I was doing e failing.

But this time it worked without any problems. I logged as administrator, opened a Terminal and typed:
```

sudo gedit /etc/fstab

```

And I see this:
```

proc /proc proc defaults 0 0
UUID=2679ab6c-2da8-48eb-8b7b-5f11833934cc / ext4 defaults,errors=remount-ro,relatime 0 1  
UUID=29811C914EAB7D93 /media/drivers ntfs-3g defaults,nosuid,nodev,locale=en_US.UTF-8 0 0  
UUID=7A8A5F338A5EEAE1 /media/System\040Reserved ntfs-3g defaults,nosuid,nodev,locale=en_US.UTF-8 0 0  
UUID=749CCF049CCEBFBA /windows ntfs-3g defaults,locale=en_US.UTF-8 0 0  
UUID=01CF9881FC472D80 /media/externalHD ntfs-3g defaults,locale=en_US.UTF-8 0 0  
UUID=12aed398-6f8b-44e6-abe4-c47fef0b751d none swap sw 0 0  
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0

```

As you can see, **this has none of my comments!!!** And **there are other differences!!!**

The word **[COLOR=#0000cd]defaults[/COLOR]** was not in the second line and **[COLOR=#0000cd]relatime was the first option,[/COLOR]** not the last.

Does Ubuntu have any way of re-writing that file?

I remember I installed *MoutManager,* but I did not change (I think) anything.

I also tryed to install the program *Boot Rapair* (I saw a video on Youtube), but the installation failed. I typed the following in this order:
```

sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install boot-repair-ubuntu

```

As I said, the installation failed. But now Ubuntu launches.

[**[COLOR=#DD4814][B]Bashing-om**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1111508"), thank you man. Every help is welcome.:D

---

### Post by yancek on 2014-07-14
> **Press S to skip mounting or M for manual recovery**

I sometimes see that warning message.  Usually it is a non-filesystem data partition or a partition on another drive which has an entry in fstab.  I hit the "S" key and it continues booting.  What happens when you hit the "S" key?

---

### Post by Leonardo_Pinheiro on 2014-07-14
> **yancek said:**
> I sometimes see that warning message.  Usually it is a non-filesystem data partition or a partition on another drive which has an entry in fstab.  I hit the "S" key and it continues booting.  What happens when you hit the "S" key?

Yancek, the second time I rebooted (the first was failing) I was being forced to press the "S" key and then I used to receive the message that the UUID=12aed398-6f8b-44e6-abe4-c47fef0b751d was missing (or something) or not ready yet. That is (I believe) the swap partition that I refused to create during installation.

---

### Post by linuxrev2 on 2015-01-11
I too had Leonardo_Pinheiro's error message: **An error occurred while mounting /etc/fstab**. I am using Kubuntu 14.04LTS.

Obviously the system tried to mount [FONT=courier new]/etc/fstab[/FONT] as a fille system. The error occurred after I had [FONT=courier new]fstab[/FONT] edited using KWrite. I could not trace any irregularity in the file, but perhaps KWrite did something invisible to the first line, triggering the system to consider it as a line to be executed. In the end I opened [FONT=courier new]fstab[/FONT] in a terminal and used [FONT=courier new]nano[/FONT] as an editor. I added a blank first line beginning with '#' and that did the trick. No more error message.

I also noted that the line 'proc /proc proc defaults 0 0', which I have had in my [FONT=courier new]fstab[/FONT] in many distros and over many years, apparently has been dropped in Kubuntu 14.04, as someone mentioned above. It is not what I learned on my Linux sysadmin course, so I added it again as 'proc  /proc  proc  nodev,noexec,nosuid  0  0'. Does anyone have a pressing argument *not* to add this line to [FONT=courier new]fstab[/FONT]?

---

