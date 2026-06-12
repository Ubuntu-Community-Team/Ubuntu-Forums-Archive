---
title: "[SOLVED] Removing Ubuntu"
date: 2008-02-06
forum: General Help
---

### Post by Tyler495 on 2008-02-06
Hello, first post and i need help uninstalling Ubuntu I used it for about 2 months.Thought it was great but... I'm a gamer so it didn't really work perfect and is much faster under windows. Anyway I need to remove and I dont have an XP disk because it came factory installed.(i did read other posts but they all needed xp disk_


Tyler

---

### Post by pointone on 2008-02-06
If you don't have Windows XP still installed somewhere on your hard drive, you cannot reinstall it without a Windows XP installation disc. Contact your system manufacturer for one if this is the case.

---

### Post by hellion0 on 2008-02-06
Well, if you don't have an XP disc, you'll need to get one. Preferably through legal channels.

Try getting in touch with your machine's manufacturer, there's a slim chance of getting ahold of an OEM disc for your machine. Normally, though, if it's a factory install, the computer should come with an OEM disc for whatever OS it came with.

---

### Post by erfahren on 2008-02-06
> **hellion0 said:**
> Well, if you don't have an XP disc, you'll need to get one. Preferably through legal channels.

Try getting in touch with your machine's manufacturer, there's a slim chance of getting ahold of an OEM disc for your machine. Normally, though, if it's a factory install, the computer should come with an OEM disc for whatever OS it came with.
usually the manufacturers intend the purchaser to burn off their own set these days and provide a way to do that. It would be covered in the manual that usually will be off the "All Programs" menu somewhere.

(why doesn't anyone ever do that?)

---

### Post by bodhi.zazen on 2008-02-06
See this thread : [http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

No disk = contact manufacturer

---

### Post by confused57 on 2008-02-06
Super Grub Disk might be your best option:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by Tyler495 on 2008-02-06
Wow, thanks for the fast response umm i just found my recovery disks will these do any good also im emailing HP to see about a windows disk.

---

### Post by ryanVickers on 2008-02-06
If XP is still on your hard drive, which it should be... I would find it hard to believe that anyone would just blindly totally switch to a new OS cold turkey... then you simply need to delete the Ubuntu partition and resize XP to fill the drive.

---

### Post by Tyler495 on 2008-02-06
No it was a dual boot system i didnt jump in cold turky probably should have mentioned earlier.

---

### Post by ryanVickers on 2008-02-06
ok, good, then you should be able to resize XP to fill the drive, and then somehow set the MBR back... (not my specialty ;))

---

### Post by Tyler495 on 2008-02-06
Not sure what you mean by that im kinda of a noob with this stuff.

---

### Post by ryanVickers on 2008-02-06
well, you split your hard drive (not physically, just with data ;)) into a XP piece and an Ubuntu piece.  You need to remove the Ubuntu piece, then expand the XP piece to fill the whole thing again.

Then, the thing that allowed you to pick XP or Ubuntu on boot, called GRUB (GRand Unified Bootloader), that will be removed along with Ubuntu, so you need to somehow get the C:\boot.ini file on XP working as the MBR (Master Boot Record, the thing that boots your OS('s))

---

### Post by Tyler495 on 2008-02-06
I posted a screenshot i hope im in the right place.

---

### Post by pointone on 2008-02-06
You will need to boot to a recovery console using the recovery disks and run the command:

```
fdisk /mbr
```

This will restore the Windows bootloader.

Those two partitions you circled are indeed the ones containing Ubuntu. You should be able to safely delete them once you restore your MBR.

---

### Post by Tyler495 on 2008-02-06
Wow, thanks for all the help but a how do i get into my recovery console?

---

### Post by erfahren on 2008-02-06
its much easier to fix the MBR before removing the Ubuntu partition - while you can still boot into Windows

someone posted a link ealier with instructions how to do that (using MBRfix.exe)

---

### Post by Tyler495 on 2008-02-06
Alight. I went to the site but i couldn't find the file there?

[http://www.sysint.no/en/Download.aspx:guitar:](http://www.sysint.no/en/Download.aspx:guitar:)

---

### Post by Tyler495 on 2008-02-06
[http://www.sysint.no/en/Download.aspx](http://www.sysint.no/en/Download.aspx)

Ignore othere post accendtly added amotin:lolflag:

Windows works fine I just want to remove Ubuntu(sorry liked it but.._

---

### Post by pointone on 2008-02-06
You can get to the recovery console by booting from your recovery disk. It should start loading some things then ask whether you want to repair or start a recovery console, or something along those lines. Choose the recovery console option and it will load a command prompt. Then you simply type "fdisk /mbr".

---

### Post by Tyler495 on 2008-02-06
Ty will report back tomoro and let you know if i had any luck.

---

### Post by erfahren on 2008-02-06
**see Hermanzone's "Uninstall" page** - [**MBRfix.exe section**](http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe)

---

### Post by erfahren on 2008-02-06
> **Tyler495 said:**
> [http://www.sysint.no/en/Download.aspx](http://www.sysint.no/en/Download.aspx)

Ignore othere post accendtly added amotin:lolflag:

Windows works fine I just want to remove Ubuntu(sorry liked it but.._
[b]if you go and delete the Ubuntu partition before restoring the MBR, Windows will no longer work "fine" - you'd be removing GRUB along with Linux. 

It is much easier to restore the MBR using that little utility while Windows is still able to boot - you don't need a recovery disk - you wouldn't need to boot into the recovery console. Just download that little utility and use it as per [these instructions](http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe).[/b]

---

### Post by ryanVickers on 2008-02-06
**is there a particular reason we have to talk in bold!!! ? :p**

---

### Post by erfahren on 2008-02-06
> **ryanVickers said:**
> **is there a particular reason we have to talk in bold!!! ? :p**
I was talking in bold because it seemed that no one was paying attention

restoring the WinXP MBR (which is different than WinXP's boot.ini) is *much* easier if it is done *before* removing the Linux partition. Just the little utility that was mentioned is all that is needed, and it's used through Windows. No need for the SuperGrub disk, WinXP or recovery disk, etc. if it's done that way.

---

### Post by Tyler495 on 2008-02-07
Well i pasted in C drive is this the right spot?                     Sorry about being so late had School

---

### Post by erfahren on 2008-02-07
> **Tyler495 said:**
> Well i pasted in C drive is this the right spot?                     Sorry about being so late had School yes - that's correct

---

### Post by Tyler495 on 2008-02-07
Umm it this what i should be left with.

---

### Post by erfahren on 2008-02-07
first change directory to the C:\ 

> 
Change it to just a C: prompt by typing: cd \ , then press 'Enter'.
After that you should just have a plain C:\>_ prompt.

then do
```

MbrFix /drive 0 fixmbr /yes

```

---

### Post by Tyler495 on 2008-02-07
Now were getting somewhere the GRUB boot list doesn't show up. Now do I just right click and delete the two circled partions?

---

### Post by erfahren on 2008-02-07
> **Tyler495 said:**
> Now were getting somewhere the GRUB boot list doesn't show up. Now do I just right click and delete the two circled partions?
yay! - yep, it worked then!

yep, what would probably be easiest is to delete those two partitions and then make one new partition out of the free space. Format it to NTFS and then it should just show up in Windows as "D:\" - use it to store your data and large files.

You *could* use GParted from the Ubuntu LiveCD to "grow" your Windows partition into the free space - but it's really handy to have a seperate partition to back stuff up to if you ever want to reinstall Windows.

---

### Post by Tyler495 on 2008-02-07
Thanks very much you all have been a big help.

---

### Post by erfahren on 2008-02-07
> **Tyler495 said:**
> Thanks very much you all have been a big help.
you're quite welcome :) glad you got it worked out!

hope you'll give Ubuntu (or Linux) another try in the future! 

-- note: if everything is working well and you consider this as "solved" you can go to the Thread Tools above the top post and mark it "Solved".

good luck!

---

### Post by ryanVickers on 2008-02-07
> **Tyler495 said:**
> Well i pasted in C drive is this the right spot?                     Sorry about being so late had School
[B]
WHAT? You put PASTE in the hard drive!???[/B]

---

### Post by Tyler495 on 2008-02-07
Haha No, thanks for your help though

---

### Post by ryanVickers on 2008-02-07
oh, ok then, good... copy and paste should not be done on a hardware level :p

---

