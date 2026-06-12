---
title: "Mounting A Failing Drive?"
date: 2014-03-23
forum: General Help
---

### Post by Blossomforth on 2014-03-23
Hello

I'm hoping you guys can help me. I have a Dell Mini 9 netbook with a 16gb solid state drive that currently has WinXP installed on it. Recently, the drive wouldn't boot and claimed the OS was missing. I loaded up my Ubuntu recovery disk to try and save my files from the drive, and Ubuntu listed the drive as "Disk failure imminent", with a single bad sector, according to the SMART test. I'm not sure how to go about rescuing my files, if its even possible. The drive appears in the Disk Utility, but not under the Places menu.

Right now, the comp is running Ubuntu 10.04 on a 4gb thumb drive. I'm not sure where to go from here since I'm still new to Ubuntu. Any help would be greatly appreciated. Thank you!

---

### Post by deadflowr on 2014-03-23
If in Places, you click on any of the entries to open the file manager do so and then when that opens look to the left pane and see if the drive/partition is listed there.
Also 10.04 on the desktop is dead and has reached end of life. Consider upgrading to a support release.

---

### Post by Blossomforth on 2014-03-23
The drive doesn't appear in the left side pane when I open the file browser. The OS definetly sees it though, since it shows up in the Disk Utility.

---

### Post by Mark Phelps on 2014-03-23
In the Disk Utility, there is generally an option to Mount the partition.  It doesn't mount it until you request it to.

You should try that.

---

### Post by Blossomforth on 2014-03-23
There's no option to mount it anywhere within the Utility menu.

---

### Post by kurja on 2014-03-24
Could be an mbr issue, I've had a couple of those and symptoms sound familiar. Try mounting it from terminal, check the partition's designation in disk utility (such as /dev/sda1) and mount that, if that returns an error message post it here.

If that's no help, try to _un_mount it, then check the disk with fsck.

I once had a problem with a drive that would neither mount nor unmount while fsck refused to run, returning that the drive was mounted.. Booting from a Slax liveCD enabled me to run fsck on that drive which rescued the situation.

---

### Post by deadflowr on 2014-03-24
> **Blossomforth said:**
> There's no option to mount it anywhere within the Utility menu.

What does the general content of the window say when you click on the hard drive name on the left side.
(When you select one of the devices on the left it will show the contents in the main window, in Disk Utility)

Also, there should be a smart check or something like that
(It's been a while since I ran 10.04, so it might be slightly different)

what does it say, regarding the failure and such.

---

### Post by Blossomforth on 2014-03-24
im not sure what im doing wrong when i try to mount the drive in the terminal. i made a folder in "/media" called "c" and when i try to mount it using the command "sudo mount /dev/sda /media/c" it says i have to specify a file system. 

Heres the content of the Disk Utility window. As i mentioned, its a failing SSD from a WinXP netbook. The netbook refused to load the OS, so im running 10.03 LTS installed on a 4GB thumbdrive in an attempt to try and recover some of the files on the bad drive. thanks again for any help you guys can offer me. I really appreciate it. 

[[IMG]http://i62.photobucket.com/albums/h100/poniesnstuffofficial/Screenshot_zpse1b7bf08.png[/IMG]]("http://s62.photobucket.com/user/poniesnstuffofficial/media/Screenshot_zpse1b7bf08.png.html")

---

### Post by deadflowr on 2014-03-24
No partition, makes sense why it won't mount.
You don't mount drives, but instead mount the partitions within those drives.

Since it says unknown, along with the RED BANNER disk failure imminent, I would conclude the disk is pretty much dead.
What does the smart status part tell you?

Edit: As a sidenote, there are professionals who specialize in recovering data from dead hard drives.
Do a local search for one in you area.
It's a process which require knowledge and the right environment to do(including special equipment)
So it's better to look at one of those recovery companies, than to try to do it yourself.

---

### Post by Mark Phelps on 2014-03-24
Sorry to say this but any partition that was there is gone -- which is why you can't mount it.

Since it was from a XP PC, it likely was formatted either NTFS or FAT32.  IF either of these was true, you would have better results using a Windows data recovery app, since they are very good at locating former folder names and file names.  But to do that, you would have to be able to connect this drive to a working Windows PC.

---

### Post by Blossomforth on 2014-03-24
Well, that's not good news, but its not the end of the world either. When I ran the SMART thing, everything was OK except for one bad sector. XP won't boot from the disk and it says "os not found". Is there anything else i can try or is it a dead end? I'm not trying to save the drive, just recover a few things off it before I send it out to pasture.

Maybe I'll replace the drive and install XP long enough to try and recover the files through a USB adapter. Thanks for the help guys, I really appreciate it.

---

### Post by bookrt on 2014-03-24
Have you run testdisk or ddrescue? I don't have any experience myself but these are the utilities I have seen mentioned when dealing with data recovery in Ubuntu. You should be able to install them to your USB stick at least temporarily if they are not already installed.

---

### Post by Blossomforth on 2014-03-25
I'll have to give those apps a go and see if it helps. Thank you for the suggestion!

---

