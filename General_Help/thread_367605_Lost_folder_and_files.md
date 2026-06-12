---
title: "Lost folder and files"
date: 2007-02-22
forum: General Help
---

### Post by lanchongzi on 2007-02-22
hi there

I just encountered a weird problem

I had my PC running - downloading some torrents using Ktorrent ( KDE app) on my Gnome desktop  
I went for a coffee  nearby ( nice place btw :)  )  when I returned home my PC was all weired.
my music folder was gone  - AAAARGH!!! - and I just got 'the eagles of death metal" !!
my torrent folder was gone as well
Ktorrent kept saying he couldn't find the files - no wonder since it was gone 'n all
so I closed it, opened it up again - wanted to set the folder to store .temp data to - but it wouldnt let me change it, 
Now my 97.8% completed torrents are gone - shame shame
oh, right i forgot.  everything in the taskbar was gone too.
and in the lost& found folder is not even the stinky fart of an indian elephant :(


what could have caused this and how can I prevent it from happening again?


thanks in advance


edit:  i just found out that even firefox couldn't remember what he is supposed to remember ( meaning bookmarks or like when i type in 'y' so that 'yahoo' pops up automatically - sorry i don't know the term for this function :)  )
and when i changed into my supposedly faster Xubuntu session it was all sluggish with a response time from more then 30 seconds

---

### Post by nereid on 2007-02-22
This doesn't sound at all like a software problem. This seems to me like a harddisk crash or something like that. Any other occurrences of this problem, beside Firefox and KTorrent?

---

### Post by lanchongzi on 2007-02-22
no, not that i noticed

but why is it just one folder and not just parts of it or sth like it?
is there a way to find out what exactly happened?

---

### Post by nereid on 2007-02-23
Ok, but you also said that KTorrent wouldn't let you change the temp folder. As long as the system isn't critically damaged does this seem to me like a hardware problem. Have you fsck'ed your partition lately? If not it would be a good idea to run fsck on the partition (just be sure you only do this on an unmouted partition. This means, if it is your root partition you have to boot from a boot CD).

---

### Post by lanchongzi on 2007-02-23
fsck ?
unmounted ?

i know i must sound really stupid but i thought un/mount is an option for external devices like an USB stick or the like.
well I will look exactly how  to do it
back up my data
try and let you know how it went



thanks for the advice  :)

---

### Post by nereid on 2007-02-23
No, nobody has to know everything. Every partition on your harddisk has to be mounted so that you can access it. You only know that it is for external devices because your root partition will be automatically mounted at boot. This means to get access to your unmounted root partition you have to boot your PC with the Ubuntu CD. From the CD you can run the command fsck (file system check). This program will check your file system for inconsistencies and bad blocks (you need to enable the bad block checking with a command line option as it takes a little bit longer). To prevent any damage to your file system you should only use fsck on an unmounted partition, just to be safe.

fsck will run every 30 mounts or every 30 days automatically which ever comes first. Be sure to read the fsck man page and do make back ups.

Hope I could help.

---

### Post by lanchongzi on 2007-02-23
you did help - a lot

thank you for the advice I will try it out tommorow in the morning then I will let you know
 - have to make the Backups first  :)
like you said " just to be safe"
hihi  learned that now

again thank you very much for the fast and helpful reply

---

### Post by lanchongzi on 2007-02-23
I nearly forgot
when i tried to use my PSP ( with my USB Stick inside :) )
to copy files to it I couldn't unmount or eject it after i was done

I installed Ubuntu first , then updated , then installed Xubuntu - which I am using now since I find it a bit faster and I kinda like the overall simplistic style it has

so I just stopped it using the command in my PSP.
so now the files are corrupted and I can't use them.

I will search for a solution for this problem now, but maybe you heard of it.
that made me use the other partition, in which Windows XP is installed.
but also there I couldnt delete the corrupted data  :(
 and that when I am trying to not use Windows 
never really liked the new Windows - I liked the old one though  what was is called 3.5 or something?  that was a nice version  ( well, that was off topic but anyways)
wish you a nice day


lanchongzi

---

### Post by nereid on 2007-02-23
Do you have a NTFS file system on your Windows partition? Linux ain't very good with it. It can read NTFS but as far as I know can't write to it reliable.

The point with mount is to make sure, that the OS has a correct access to it and the unmount commando will verify that all data has been correctly written to the medium. So it ain't a good idea to draw something out if it ain't unmounted.

The unmount process can take some time and you can't really see how long it will take. Ubuntu is configured to write only the index of a file at the copy procedure and the real stuff will start at least when you unmount the medium. So don't pull your USB stick out too fast. Unmount your stick and wait around five minutes or so if you're not in a hurry.

---

### Post by tgalati4 on 2007-02-23
What was the uptime of the machine before you started experiencing problems?  It could be a power problem.  Do you have an UPS?  Any clock radios flashing in the house that would indicate a short power loss?

Downloading torrents can cause continuous write sessions on the disk.  If the disk is old (greater than 3 years) or cheap (consumer grade vs server grade) then it is possible that one of the heads went bad.  Linux will still run, but any new activity will be crippled and it will continue to get worse as the data corruption continues.  Sounds like what you are experiencing.

Windows is nice in that you get a blue screen of death that hides all of that nastiness.  And we are so conditioned to reboot, we never get to see the operating system die a progressive death.

When you have a strong OS, you need to pay more attention to the hardware.

---

