---
title: "2 Hard Drives"
date: 2007-11-26
forum: General Help
---

### Post by melisandre on 2007-11-26
Someone mentioned when I had earlier problems the way to get Ubuntu 7.10 to recognize 2 hard drives... I can't remember where I saw that. Could someone give me a quick overview on how to do that?

---

### Post by smartboyathome on 2007-11-26
What do you mean? You want to connect them while Ubuntu is on and have them come up? Or maybe do you want to make them 'part of' the current HD? The former is easier to do (in fact it is done automatically) than the latter (which you have to do manually).

---

### Post by Therion on 2007-11-26
Ubuntu automatically recognizes my slave-drive, but i do have to use the "Mount" command before I can *access* it.  I just right-click and choose the Mount command from the context-menu, but you can set things up so that the drive will automatically mount on startup; I've just never bothered.

Does that help?

---

### Post by santana on 2007-11-26
you have to add an entry to /etc/fstab

---

### Post by melisandre on 2007-11-26
> **Therion said:**
> Ubuntu automatically recognizes my slave-drive, but i do have to use the "Mount" command before I can *access* it.  I just right-click and choose the Mount command from the context-menu, but you can set things up so that the drive will automatically mount on startup; I've just never bothered.

Does that help?

Something like that... it said it had a problem mounting it. I'm rather new at this, so I'm not sure I know what you mean though...

---

### Post by Therion on 2007-11-26
> **melisandre said:**
> Something like that... it said it had a problem mounting it. I'm rather new at this, so I'm not sure I know what you mean though...
Hmmm... So you can see the slave drive listed in the panel on the left when you open your Home folder.  You right-click on it (the slave-drive icon on the left) then click on "Mount", and you get an error, saying it can't be mounted, correct?

Assuming that's the case, let's try this:  Open a Terminal from: Applications->Accessories->Terminal and type (or cut and paste):

```
sudo apt-get update
sudo apt-get install ntfs-config
```

Enter your user password, then Enter.

This should install the NTFS Configuration Tool if it's not already installed.  

Now go to Applications-> System tools-> NTFS Configuration Tool

Try using that Config Tool to get your slave-drive to mount up, and if that doesn't do it, you might need to edit fstab.  But let's not go there if we don't need do.  :)

---

### Post by melisandre on 2007-11-26
Great thanks! I'll try that later tonight.

---

### Post by melisandre on 2007-11-27
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

?????????????? What happened here????????????

Edit: Never mind, the installation worked...

---

### Post by melisandre on 2007-11-27
> **melisandre said:**
> E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

?????????????? What happened here????????????

Edit: Never mind, the installation worked...

Ok, so I used it, and this is the message it gave me:
> Mounting /media/Local Disk 2 failed.

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/Local Disk 2 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/Local Disk 2 ntfs-3g defaults,force 0 0



So I went to terminal and attempted to do mount it there with

```
mount -t ntfs-3g /dev/sdb1 /media/Local Disk 2 -o force
```

This is what I got:

> mount: mount point 2 does not exist

:cry:

PS. My second harddrive is called Local Disk 2.

---

### Post by geirha on 2007-11-27
You'll need to escape those spaces in the mount-point, or enclose it in quotes
```
mount -t ntfs-3g /dev/sdb1 /media/Local\ Disk\ 2
#or
mount -t ntfs-3g /dev/sdb1 "/media/Local Disk 2"
```

Make sure the mountpoint exist and is a directory
```
sudo mkdir "/media/Local Disk 2"
```

---

### Post by Therion on 2007-11-27
> $LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
clicking on the 'Safely Remove Hardware' icon in the Windows
taskbar then shutdown Windows cleanly.
I once got that error myself.  What solved it for me, and this assumes you are dual-booting Windows, was booting into Windows, accessing the slave-drive (open and close a file for instance, anything that will actually *access* the slave drive).  Opening another file on the C: drive, closing it, and then shutting down Windows and the PC cleanly.  I then did a cold-start, booted right into Ubuntu, and used the Mount command for the slave-drive.  Access problem solved.  It was just that simple in my case.

---

### Post by melisandre on 2007-11-27
> $LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/Local Disk 2 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/Local Disk 2 ntfs-3g defaults,force 0 0

Oh, and Therion - I don't have Windows =)

---

### Post by melisandre on 2007-11-29
I hate to *bump* this, but I have very important files for a deadline on the other harddrive...:(

---

### Post by geirha on 2007-11-29
Well, did you try with "-o force"?
```
sudo mkdir /media/Local\ Disk\ 2
sudo mount -t ntfs-3g -o force /dev/sdb /media/Local\ Disk\ 2
```
Not safe, but seems to be your only option.

---

### Post by melisandre on 2007-12-04
> **geirha said:**
> Well, did you try with "-o force"?
```
sudo mkdir /media/Local\ Disk\ 2
sudo mount -t ntfs-3g -o force /dev/sdb /media/Local\ Disk\ 2
```
Not safe, but seems to be your only option.

I did everything it said, and still got errors... should I get a LiveBoot Windows CD and do chkdisk?

---

### Post by geirha on 2007-12-05
oops, "/dev/sdb" should've been "/dev/sdb1" :/

Booting windows and doing a chkdsk is probably a good idea, and you'll probably be able to mount it without -o force afterwards.

---

### Post by melisandre on 2007-12-11
> **geirha said:**
> oops, "/dev/sdb" should've been "/dev/sdb1" :/

Booting windows and doing a chkdsk is probably a good idea, and you'll probably be able to mount it without -o force afterwards.

Thanks for all your help! I'll get back to you when I am able to do that (as the CD has been stolen by another computer-problem-riddled member of the family... =P)

---

### Post by melisandre on 2007-12-30
Alright, after much procrastination and ado I ran chkdsk (windows, blah) only to find it couldn't do it due to the disk being RAW data. However, when I booted up Ubuntu again... everything was set! Guess Windows set out to bother me once more. Thanks so much for all your help everyone! It was really appreciated.

---

