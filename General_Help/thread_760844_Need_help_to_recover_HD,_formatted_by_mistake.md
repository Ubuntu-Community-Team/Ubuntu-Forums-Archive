---
title: "Need help to recover HD, formatted by mistake"
date: 2008-04-20
forum: General Help
---

### Post by lucadp on 2008-04-20
Hi everybody, please help me in order to recovery my files.
I was running Ubuntu Live Cd, and today I wanted to format my usb key. Unfortunately I made a mistake and typed the wrong path in the shell. 
```
sudo mkfs.ext3 -b 4096 -L casper-rw /dev/sda1
```
sda1 is mi unique HD for Windows XP and now my laptop doesn't find the operating system any more. 
Anyway i know that the data is stil there, and probably this problem could be solved just forcing the partition back to ntfs. Otherwise if I've to format the HD back to ntfs, still there could be a chance for recovering my files.
Can anyone help me? I'd be grateful.

Thanks a lot, and sorry form my bad English

---

### Post by pytheas22 on 2008-04-20
I'm not an expert, but I'm pretty sure that since you've reformatted, everything is gone...you won't be able to get the files back simply by reformatting to NTFS.  That would only make it worse.  You could try booting to a Windows CD and seeing if you can fix the problem, but Windows won't read ext3, so I doubt you'll have much luck.  Unfortunately, since NTFS is proprietary, there's not much you can do from Ubuntu to save it.

If you want simply to rescue your files, there's a program called photorec that can search for them.  It won't repair the system--you will still probably need to reinstall Windows--but at least you can save your data.

Install photorec with:
```

sudo apt-get install testdisk
```

(photorec is part of the testdisk package)

and run it with:

```
sudo photorec
```

---

### Post by Lolicon on 2008-04-20
if you put data on the sectors already its gone. if its still unformatted you can probably use any recovery or partition program to try to fix it.

---

### Post by lucadp on 2008-04-20
Thanks guys, I appreciate your interest. I actually used the mkfs.ext only once, and then I didn't put any data on it, since I'm running on a live CD. I'va a question: If I install testdisk in this way
code]sudo apt-get install testdisk[/code]
does it install on the Hard Drive, or in the RAM? I don't want to install on my HD since it could erase more data.
Thanks!

---

### Post by pytheas22 on 2008-04-20
> does it install on the Hard Drive, or in the RAM?

So long as you are running the live CD, it will be installed in RAM; no worries about corrupting the drive any more.

---

### Post by pytheas22 on 2008-04-20
Also as another poster mentioned, beyond recovering the files themselves, you might be able to save the Windows system by repairing the partition.  testdisk will do that:
```

sudo testdisk
```

Also I recall using a program called gpart (not gparted) once that could also save partitions.

---

### Post by konungursvia on 2008-04-20
There are 2 ways to format: quick and complete. If you did a quick format, only some metadata is changed, and most of your data would likely survive.

---

### Post by lucadp on 2008-04-20
PhotoRec found a lot of file, thanks a lot! Unfortunately, since it's running from RAM, it has not enough memory to restore data.
I guess that the best solution is to create an image of the HD onto an external Hard Drive, even if I don't really know how to do it (I've heard about the dd command), and I'm not sure if it can be done from the live CD. Any help?

Thanks a lot, now I've got a new hope!

---

### Post by jlh68 on 2008-04-20
This may not be the exact problem by maybe this will work.

My Windoze HD will not boot Windoze.  It will display the startup screen but asks if I want to [Activate} and I check yes and then the screen goes to {It is already activated] and then proceeds to shut down.

Well I wanted my files off the HD.  I have a Vantec SATA/IDE to USB 2.0 Adapter ($24).  It has an interface connector (SATA, 5.25 IDE, 3.5 IDE, & 2.5 IDE)  and a power supply for the HD.  I hook it all up and power up the HD which is now plugged into my laptop USB port.  I now can access all the file on the HD.  I moved the ones I want to keep to my laptop.  Later I will move them to my PC as soon as I finish setting up Ubuntu 8,04 beta.  I guess I will upgrade to the final next week.

In any case often a Linux system can access NTFS and FAT drives without a problem.

In fact Law enforcement uses that same technique to forensically gather data from computers seized.

---

### Post by lucadp on 2008-04-21
Updates
I've created a disk image of my formatted HD with Gddrescue: even if it's ext3 and seams to be empty, i've managed to rip it to an external Hd. 
Now with another pc running vitsta I'm running Photo rec and it's going to backup most of my data, but it probably will take 24 hours to get done.
The files recovered were on an NTFS partition, and I guess that the names of them are all lost, but I'm fine.
After recovering my files I'm going to use test disk on my hd to see if I can recovery the full Windows installation.
Thanks a lot to all of you, and if you have any tip don't exitate to tell it to me.
Hope this 3D will help people with the same problem!

---

