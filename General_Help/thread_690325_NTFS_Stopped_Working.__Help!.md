---
title: "NTFS Stopped Working.  Help!"
date: 2008-02-07
forum: General Help
---

### Post by ezm on 2008-02-07
Hello -- 
So I have an irritating problem.  I have a partioned hard drive on which I am running a both ubuntu (gutsy gibbon) and Windows Vista, dual-booted.

I wanted to have read/write access to the data which is in the Windows NTFS partition of my hard drive and so I worked out that I can use the NTFS Configuration Tool (NTFS3g) to mount the windows partition so that I can both read and write from it.

I installed this package using the Synaptic package manager and configured the drive succesfully.  It ran succesfully for quite a long time.  I restarted the system several times.  One day, however, it stopped working.  When I booted the drive was not mounted.  I think, though I am not sure, this occured after, while running the computer in Vista, the compute ran out of battery and shut down without properly closing.  

I tried to re-run the NTFS configuration tool and received the following message after checking the windows partition and clicking apply: "An error occured when trying to configure /media/SW_Preload, please retry. Thanks."  

I have looked online for people experiencing similar problems and found a common recommendation to restart in Vista and run chkdsk /f.  I did this and it seemed  to find no problems.  I rebooted in Ubuntu and tried to run the NTFS Config. Tool again, but got the same error message.  

Since then I have reinstalled the NTFS3g tool using the S. Package Manager and restarted the computer.  Still getting the same message.  

Any help would be much much appreciated.  This is a very frustrating problem as I was very happy working in Ubuntu and accessing my data in the windows partition.  Vista is such a horrible work environment at the moment.  

ezm

---

### Post by ezm on 2008-02-07
An additional detail is that I just tried to manually mount the drive using a simple mount command:

  sudo mount /dev/sda2 /media/SW_Preload

The command worked succesfully...  (Though I guess the drive in this case is not read/write?)

ezm

---

### Post by merike on 2008-02-07
According to manual page for mount the default is mounting read/write.

---

### Post by ezm on 2008-02-07
Ok, yes I tested this and it is indeed read/write.  But I remember reading on several pages
that the read/write methods in this case may not be safe/stable?  

What in fact is the difference between using NTFS Config tool to mount a drive automatically
and doing it manually?

And if were to want to automate the mounting of the drive at boot time without using the NTFS Config. tool, how would I do that?

(I'm revealing my lack of knowledge about linux at this point.)

ezm

---

### Post by merike on 2008-02-07
I have lines for ntfs partitions in fstab file. I also have ntfs-3g driver installed, I assume that this is used both by mount command and mounting at boot. Since ntfs-config uses the same driver there shouldn't be a difference.
About safety: it could be that some of the articles saying it isn't safe may be old. Support for ntfs has got a lot better in recent years.
If you'd do it manually then you'd add a corresponding line to /etc/fstab. A quick search in the forum should give you exact line.
I currently have:
```
UUID=B4B0BDEFB0BDB7E6 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
```
Your UUID would be different but you can use /dev/sda2 instead.
I have never fully explored what exactly options after ntfs mean and if I have I soon forget. I go by: "if it's working don't repair it". In any case the exact meaning of those can be found using some fstab tutorial.

---

