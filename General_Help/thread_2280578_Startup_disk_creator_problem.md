---
title: "Startup disk creator problem"
date: 2015-05-31
forum: General Help
---

### Post by iiwasen on 2015-05-31
I have a Ubuntu 14.04. I accidentally used the command "usb-creator-gtk --allow-system-internal" while I was in the home folder. After that it locked all my folders there and I restarted the computer. Then it went to a fix screen and tried to fix itself. I pressed the manual fix buttons and now it's on the terminal saying "Filesystem check or mount failed. A  maintenance shell will now be started. Control-D will terminate this  shell and continue booting after re-trying filesystems. Any further  errors will be ignored.".

I have considered two options: 1. Letting it fix itself. 2. Running the command "sudo mount -o remount,rw /".

The problem is that I do not know what it would do on those points and if neither of those is going to save the data on the linux, what would?

---

### Post by sudodus on 2015-06-01
Welcome to the Ubuntu Forums :-)

I have spent a lot of time with tools to create USB pendrives. The option **--allow-system-internal** is not in the manual ```
man usb-creator-gtk
``` but I find it in the output from ```
usb-creator-gtk -h
```

I guess that is where you found it. I'm not sure what it does, but it seems risky to use the option --allow-system-internal.

There are many alternatives to ***usb-creator-gtk***. See this link [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[I][B]Backup
[/B][/I]
If you have important data stored in your system (in your internal hard disk drive), I recommend that you backup your data before trying to save your system. Boot a live session - boot from your Ubuntu install drive (DVD disk or USB pendrive), identify the important data in your internal hard disk drive and save it to an external drive or to an internet cloud service. Or use a special tool for backup or cloning/imaging. Please ask for details, if you need help to backup your important data!
[I][B]
Repair[/B][/I]

With your important data backed up, you dare let the system try to fix itself. If that does not work, please come back for more help!

Good luck :-)

---

### Post by iiwasen on 2015-06-07
It seems that letting Linux fix the problem itself was enough, yet it still checks the disk when I start it.

---

### Post by sudodus on 2015-06-07
I suggest that you check the SMART information of your internal disk drive. You can do that with 'Disks' alias ***gnome-disks***. It will show the status of the physical device. 

After that you can check the file system in the root partition '/'.

Boot from another drive, for example your Ubuntu install DVD/USB drive. Start a terminal window and run

```
df
```

```
sudo e2fsck -f /dev/sdxy
```

where x is the drive letter and y is the partition number (that you identified earlier). It is often /dev/sda1 or /dev/sda5 if you boot from the first disk.

File system errors can be repaired. Come back here if there are read/write errors while you are running ***e2fsck***.

But there is always a risk that something bad happens, so I remind you of ***backup***. All valuable personal data should be backed up.

---

### Post by iiwasen on 2015-06-07
It stopped checking the disk after a few restarts even though I didn't do the file system error repair. In other words, it seems that the problem is solved.

---

### Post by sudodus on 2015-06-07
That good :-) If you feel that your problem is solved, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

