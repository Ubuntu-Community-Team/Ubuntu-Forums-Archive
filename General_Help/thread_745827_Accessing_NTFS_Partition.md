---
title: "Accessing NTFS Partition"
date: 2008-04-04
forum: General Help
---

### Post by Zecromancer on 2008-04-04
Hey everyone. I'm new here. I'm also new to Ubuntu, which should seem pretty obvious.

 I used to use windows and had 2 partitions, one for general stuff, and one solely for music and games (because I reformat a lot and hate re-installing games and ripping music).

Anyway, I can't access my music and games now that I have Ubuntu. The folder is blank. It's on /media/hda5, if that helps any. I checked the paritions, and it recognizes that the partition has 48 GB used up, so I'm pretty confident that my stuff is still there. I just can't get to it, and I'm guessing it's because it's an NTFS partition. 

Any help? Please remember that I'm a COMPLETE beginner, so sorry for such a dumb question.

EDIT: Oh by the way, I DO NOT dual-boot, so i can't just access it from windows.

---

### Post by zeronothing on 2008-04-04
hey there,

to help you out, try installing ntfs-3g. this will allow you to access your windows partitions. if you open up terminal and execute this command:

sudo apt-get install ntfs-3g ntfs-config

this will install the ntfs-3g module and then it will install the gui mount program to mount the windows partitions. hope this helps.

oh, also you can install the same stuff using synaptic as well. this is accessed by going to 
system->administration->synaptic

here you can search and install the program using a gui interface

have fun

---

### Post by Zecromancer on 2008-04-04
Ok I got the NTFS-3g thing, and i ran a new program. Not sure if it's the right one, but it's new, it's called 'NTFS configuration tool'.  Was that the right program? anyway, I ran it and apparently the drive is in use, but it's unmounted.

 It gave me a code to force it to mount, 'mount -t ntfs-3g /dev/hda5 /media/hda5 -o force'
And when i entered that, i got a message that said 'mount: only root can do that'

First of all, was that the right thing? Secondly, what am I doing wrong?

---

### Post by zeronothing on 2008-04-04
that is right, you have installed everything nessessary to mount the partitions but I forgot one last thing. in order to mount those partitions you have to do it with root privileges. to do that try doing this:

at your desktop press this shortcut key alt+f2


this will bring up the "run applications" windows 


in the text box enter this command: gksu ntfs-config

hopefully it will ask you for you password an then allow you to mount the partitions because the command gksu allows you to execute a gui programs with root privileges

give it a whirl

---

### Post by Zecromancer on 2008-04-04
Ok, I did that and checked both boxes but I still got the same message. Is it a problem with my computer or something?

---

### Post by zeronothing on 2008-04-04
try opening up terminal and executing this command to see what you get after you get it copy and paste it into a post here:


command: sudo fdisk -l


paste whatever you get in terminal here in a post so I can examine your disks available

thanks

---

### Post by Zecromancer on 2008-04-05
Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x32933292

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1732    13912258+  83  Linux
/dev/hda2           17320       30401   105081165    f  W95 Ext'd (LBA)
/dev/hda3            1733        1856      996030   82  Linux swap / Solaris
/dev/hda4            1857       14014    97659135   83  Linux
/dev/hda5           17320       30401   105076408+   7  HPFS/NTFS

Partition table entries are not in disk order
joe@Zecromancer:~$

---

### Post by zeronothing on 2008-04-05
ok, good try this:

open up terminal and execute this command:

sudo mkdir /media/windows

this will create a directory for the mount point to mount the windows partition: next

execute this command in terminal:

sudo ntfs-3g /dev/hda5 /media/windows

hopefully you will be able to mount it successfully. in order to view the partition go to: places->computer->filesystem->media->windows


try that

---

### Post by Zecromancer on 2008-04-05
joe@Zecromancer:~$ sudo mkdir /media/windows
joe@Zecromancer:~$ sudo ntfs-3g /dev/hda5 /media/windows
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/hda5': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/hda5 /media/windows -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/hda5 /media/windows ntfs-3g defaults,force 0 0
joe@Zecromancer:~$

---

### Post by zeronothing on 2008-04-05
ok, I have heard people having problems like this but don't give up. try executing the command like it says to see if it will mount. in terminal execute this command:

mount -t ntfs-3g /dev/hda5 /media/windows -o force

if that doesn't work we will try the fstab option

---

### Post by zeronothing on 2008-04-05
wait, forgot to add sudo before the command. should be like this:

sudo mount -t ntfs-3g /dev/hda5 /media/windows -o force

---

### Post by Zecromancer on 2008-04-05
Ok I got this:


joe@Zecromancer:~$ mount -t ntfs-3g /dev/hda5 /media/windows -o force
mount: only root can do that
joe@Zecromancer:~$ /dev/hda5 /media/windows ntfs-3g defaults,force 0 0
bash: /dev/hda5: Permission denied
joe@Zecromancer:~$

EDIT: Used the wrong code, With the one you last told me, I got

joe@Zecromancer:~$ sudo mount -t ntfs-3g /dev/hda5 /media/windows -o force
$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.
joe@Zecromancer:~$

---

### Post by zeronothing on 2008-04-05
read my post above yours, I forgot to added sudo to the command

---

### Post by Zecromancer on 2008-04-05
Yea, just noticed that, I tried your last one and got

joe@Zecromancer:~$ sudo mount -t ntfs-3g /dev/hda5 /media/windows -o force
$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.
joe@Zecromancer:~$

---

### Post by zeronothing on 2008-04-05
try seeing if the partition did mount by going to:

places->computer->filesystem->media->windows

see if you can see your files on the windows partition

---

### Post by Zecromancer on 2008-04-05
Whoa, thanks man! It's there, I owe you a million for that, THANKS! :guitar:

---

### Post by zeronothing on 2008-04-05
just to help you out even more try enter editing the fstab file so you dont have to remember to enter all the crap in to terminal to access the windows partition.

open up terminal and execute this:

sudo gedit /etc/fstab

what will happen is the config file for fstab will open up in a text editor so you can edit the mount points for your system. at the end of the config file add this to it:

/dev/hda5	/media/windows	ntfs-3g defaults 0 0

save the file in the text editor by clicking the save button

hopefully from now on when you restart your computer, during the reboot it will mount the windows partition automatically. 

have fun.. if you need even more help i have a ICQ account you can message me at to get more help. you can click on the green flower to the left on my post to message me on ICQ 

later

---

