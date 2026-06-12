---
title: "Startup Disk Creator somehow formatted my 3tb drive. Is entire file structure gone?"
date: 2015-03-20
forum: General Help
---

### Post by jrarrmy2 on 2015-03-20
Hi there,

I was formatting a small thumbdrive with Startup Disk Creator and somehow it switched and formatted my external drive.
I've been searching everywhere and following many methods with about 10 different recover programs and none seem to be able to access the file structure. 

1. Is the structure definitely, entirely gone now?
    1. a) If it's not or even is, would it help if I had a specific section of the file structure still available to help find the rest? (I had a portion of the drive backed up on copy.com)

2. Not even a data recovery professional would be able to get filenames if it seems they're all overwritten with 00's?

Photorec has recovered 300k files but programming files are quite useless without names and folders.
Active's Disk Editor 5.0 shows pretty much all of offset 224-24560 is 00's.
Before and after that it has 'this is not a bootable disk. Please insert a bootable floppy...'
Then again from 24800- 1,080,000+ is 00's.

I'm assuming this likely means I have nothing and no backup log or startup disk log would've saved that kind of info? So I just need to actually reformat and start from scratch?

Thanks,
Jeremy

---

### Post by sudodus on 2015-03-20
Welcome to the Ubuntu Forums :-)

Tough luck! Editing partitions and installing operating systems are risky operations. They work most of the time, but not always.

I hope your copy.com backup contains the most important files.

Try Testdisk if you not tried it already. If still no go, I think PhotoRec is the best tool, because it works without a file system. But it cannot find the file names and directory structure. Some file types keep a copy of the file name in the beginning of the file, but most files don't give any clue to the file name.

Edit: Otherwise, when can't to recover more files, yes, you just need to actually reformat and start from scratch.

---

### Post by jrarrmy2 on 2015-03-20
Hi sudodus. thanks, just lost my old login info. Everything keeps changing here :)

Ya, I always have several backups, but everything hits at once and not every file is in each back-up :p 
It was actually during a final restructuring to make back-ups work better that it all went lol. (Reminds me of something... [COLOR=#545454][FONT=arial]**Oogway**[/FONT][/COLOR][COLOR=#545454][FONT=arial]:[/FONT][/COLOR][COLOR=#545454][FONT=arial] One often meets his destiny on the road he takes to avoid it) :p
[/FONT][/COLOR]
So ya, looks like all my attempts to make sure everything is backed up proper and organized just went backwards a few years.
Testdisk has been maybe too thoroughly attempted, analyzed it over and over again.


Moving forward outside of if any other options come.. is there a way to back up the structure regularly/automatically?

---

### Post by sudodus on 2015-03-20
There are many backup tools. Maybe you want an automatic backup system, that runs every night. Maybe you want a complete image of your system once in a great while.

You can start at the following link

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

and after reading it, you probably have some more specific questions.

---

### Post by jrarrmy2 on 2015-03-20
Ah thanks, that's a better list than what I've been finding.
I run my system on just a 30gb solid state, so what's most important is to back up specific folders cross-referencing on the other multiple internals and an external.

Can't wait to try 15.04, I can't run basic things on a fresh install of 14.04, utilities like this I probably won't be able to test, but I'll be trying. 

gshutdown doesn't shutdown, apps freeze grey when there's tons of resources, update won't load, can't unlock programs from launcher... having quite the time with all this these days.
A main problem is needing thumbnails of photos, but they seemingly must be stored on the system drive, yet I have 10gb of thumbnails(and growing) which doesn't help anything.

---

### Post by sudodus on 2015-03-20
Maybe you have a driver problem. What chips/cards are there for graphics and wifi?

---

### Post by jrarrmy2 on 2015-03-20
No wifi, PCI Express Gigabit Ehternet Controller
Graphics, Radeon HD 5400 (Gallium 0.4 on AMD Cedar)

32 bit with AMD FX 6300, 4gb ram

---

### Post by sudodus on 2015-03-20
I have only experience of Radeon with the free drivers. I hope someone else can help you with a proprietary driver.

---

### Post by jrarrmy2 on 2015-03-20
Thanks very much :)

---

