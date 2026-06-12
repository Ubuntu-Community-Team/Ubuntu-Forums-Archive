---
title: "How to automount SATA drives when boot"
date: 2015-11-10
forum: General Help
---

### Post by fkervin on 2015-11-10
Hi all,

I have a problem since years with Xubuntu, it is, I can't make hard drives automount on system boot, so I have to enter them at least once if I want torrent to access files stored on them.

And... yes, I know existence of /etc/fstab, and thanks to the people on this forum I know how to modify this file, add the UUID of the disk and make it mount on boot. You can say "you have it! done", but no, I don't have it. I want the drives to **automatically mount**, and when I say this I mean "like in Windows", it is, if I install a new disk on a computer I don't have to handle /etc/fstab file, the disk mounts really automatically.

Thanks to the great people on this forum, among them, **schragge**, I could make USB drives automount (I explain the method at the end of this post, perhaps can be usefull to anyone) but I'm still unable to make internal disks mount without the need of edit /etc/fstab.

In this point I've to say thanks to the people who want to answer me "*if you prefer windows use it*" or "*edit /etc/fstab file, it's easy and you know how to*". Those solutions are not ok to me.

The fact of modify /etc/fstab is easy for me, but lets say I give a computer to a third person and this person install by himself a new disk inside his computer. This people will break the system if he does it in the wrong way. Editing this file in the wrong way can even break the boot of the system.

All I want is simply that if this third person in the future needs to add a disk, he simply has to format the disk, not handle /etc/fstab. I know it is the usual way to do this with Ubuntu systems, but if I've make USB drives automount and also Kubuntu includes an option for "automount all units on start" (I've use this, works with SATA disks) I'm completely sure there has to be a way to do this on Xubuntu.

So, I hope someone can lend me a hand with this, In my opinion is something very interesting and could automate a process that I'm sure that has reasons to be manual, but as I explain, there are also reasons to make it automatic.

To end, I explain the method I learned here in this forum to automount USB disks, perhaps it could even be modified to affect also internal sata drives.

Regards and many thanks to anyone who has read this post.

**How to make USB drives automount**

```
sudo <your prefer text editor> /usr/local/bin/automount
```

paste this:

```

#!/bin/sh

udisksctl dump |
  awk -F':\n' -v'RS=\n\n' '/[ \t]*HintAuto:[ \t]*true/&&/\.Filesystem:/{
                             print $1
                           }' |
  while read dev
  do
    udisksctl mount --object-path "${dev##*/UDisks2/}"
  done

```

save and exit

modify permissions to the file:

```
sudo chmod +x /usr/local/bin/automount
```

Now we create a file in /etc/xdg/autostart:

```
sudo <your prefer text editor> /etc/xdg/autostart/massmount.desktop
```

we paste the content:

```
Encoding=UTF-8
Exec=automount
Name=Automount USB drives
Comment=Added thanks to gurus in ubuntuforums.org
Terminal=false
Type=Application
StartupNotify=false
OnlyShowIn=XFCE;
NoDisplay=true
```

Save and exit

---

### Post by TheFu on 2015-11-10
I'd just write a script that did this, but there are many difficulties.
* does the disk have any partitions?
* does the disk have any file systems?
* does the disk use LVM?
* what happens if the disk is part of a RAID set?
* what happens if there is a file system,  but the required tools to access it aren't on the machine?
* which userids should this work? The power to mount is the power to pwn a machine completely.

I realize you asked a simple question and if you can ignore all these likely options, fine. That can make the script easier.

OTOH, if this doesn't happen daily and I was responsible for systems management of these machines, I'd just create an ansible playbook to modify the /etc/fstab as needed for the specialized situations on these machines.

BTW, using sudo with most GUI text editors can make a gnome system refuse to launch many programs. 
Steps to reproduce:
* Install a fresh system
* login with the sudo-capable account
* sudo gedit /etc/hosts  ..... make an unimportant edit and save
* try to launch firefox or some other GUI programs and see them fail.

Use **sudoedit** instead. Much safer and then you can use any editor preferred, including GUI editors.

BTW, 
```
$ udisksctl
The program 'udisksctl' is currently not installed.
```
Not on my systems.

---

### Post by fkervin on 2015-11-12
> **TheFu said:**
> I'd just write a script that did this, but there are many difficulties.
* does the disk have any partitions?
* does the disk have any file systems?
* does the disk use LVM?
* what happens if the disk is part of a RAID set?
* what happens if there is a file system,  but the required tools to access it aren't on the machine?
* which userids should this work? The power to mount is the power to pwn a machine completely.

I realize you asked a simple question and if you can ignore all these likely options, fine. That can make the script easier.

OTOH, if this doesn't happen daily and I was responsible for systems management of these machines, I'd just create an ansible playbook to modify the /etc/fstab as needed for the specialized situations on these machines.

BTW, using sudo with most GUI text editors can make a gnome system refuse to launch many programs. 
Steps to reproduce:
* Install a fresh system
* login with the sudo-capable account
* sudo gedit /etc/hosts  ..... make an unimportant edit and save
* try to launch firefox or some other GUI programs and see them fail.

Use **sudoedit** instead. Much safer and then you can use any editor preferred, including GUI editors.

BTW, 
```
$ udisksctl
The program 'udisksctl' is currently not installed.
```
Not on my systems.

Many thanks for your answer, TheFu, and sorry for the late of my reply.

According to yout answers, the disks (appart from system disk) will have only one partition, no LVM and no RAID. Perhaps in some cases there could be a second disk with a Windows installation. I'm not sure about what you mean with two last answers.

To be clear, what I want is simply the same that happens when you enter Thunar and click on all the internal disks, then those disks are available for applications. When we do this, we have simply to click on the drives, no administrator rights are required, no pwn system and no problem, its simply click once on the disk and it's mounted. 

What I want its simply automate this, can this be done?

I undestand for your words it can imply problems, but I'd like to know how to do this and test by myself if those risks are bigger than profits.

Regards

---

### Post by TheFu on 2015-11-12
Have you already looked at the "Disks" tool included with a stock Ubuntu desktop install?
[https://apps.ubuntu.com/cat/applications/quantal/gnome-disk-utility/](https://apps.ubuntu.com/cat/applications/quantal/gnome-disk-utility/)
This application won't install on my system.  Don't know why that is.

---

