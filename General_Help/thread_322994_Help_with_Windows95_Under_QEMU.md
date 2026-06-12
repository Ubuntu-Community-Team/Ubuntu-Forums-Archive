---
title: "Help with Windows95 Under QEMU"
date: 2006-12-21
forum: General Help
---

### Post by Darkfrost101 on 2006-12-21
Hey guys!

I was hoping you lot could help me out, i'm completly stuck :) 

What i'm trying to do is run windows 95 inside dapper with QEMU.

Now, i have a Windows 95 cdrom from a old computer, and i'm hoping i can use that.

I've look at various guides, and made a win.iso for the hd, but then i get to the problem.

I put the Win95 cd in, and use qemu -localtime -hda win.img -cdrom /dev/hdc -m 128 -boot d
I get a message saying:
CDROM boot failure code : 0004
Boot from CD-Rom failed
FATAL: Could not read the boot disk

Now, from what i understand, i have to use a dos floppy and install dos, and install windows 95 from there.

NOTE: I have no floppy drive :)

I've looked around and found FreeDos, so after a bit of looking around i work out a new command, which is
qemu -localtime -hda win.img -cdrom /dev/hdc -fda fdboot.img -m 128 -boot d
the fdboot.img is there downloaded from [http://www.ibiblio.org/pub/micro/pc-stuff/freedos/files/distributions/1.0/](http://www.ibiblio.org/pub/micro/pc-stuff/freedos/files/distributions/1.0/)

but when i run the command, the same thing happens,
Boot from CD-Rom failed
FATAL: Could not read the boot disk

Then i changed the -boot d to -boot a

FreeDos starts, and i go onto LiveCD
i type x:setup.exe and then it preforms a check on my sytem...

I get the message:

This version of Microsoft ScanDisk will work only with MS-DOS versions 5.0 and later.
Setup found a compressed volume or a disk-cache utility on your computer. Quit Setup and check your compressed volume with your disck compression software or remove the disk-cache utility.
Then run Setup again.

Sorry, but what do i do now? Hoping someone could help :)

Thanks!

---

### Post by budgie9 on 2006-12-21
I can't help you with the commands, but I think you will find Win95 actually wants MSDOS and therefore the FreeDos will not work.  Could it be perhaps the disk is seeing the Linux disk and thinks it is a compressed disk?
I would be most interested to see how you get on with this project so could you post your finding please.

---

### Post by Darkfrost101 on 2006-12-21
Hmm... Ok

Is there anywhere i can get MSDOS for free? (Legally) 
I'm guessing I can't, but hey, i might be lucky!

---

### Post by Darkfrost101 on 2006-12-22
Ok, i installed Freedos properly (Set the cd drive to fdbasecd.iso and installed from there)

Now the windows 95 installer starts! Yay! Progress!

Problem. New error :)

After a load of next next next stuff, it says

PANIC: more than two near fnodes requested at the same time!

System halted

Any help with this? :D

Thanks again!

---

