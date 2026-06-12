---
title: "I want my XP back"
date: 2008-05-09
forum: General Help
---

### Post by the.weavster on 2008-05-09
How do I uninstall Ubuntu and Grub so I can go back to single booting my (sorry to say it, but it's true) much more robust, reliable XP SP2 system.

---

### Post by Th3Professor on 2008-05-09
> **the.weavster said:**
> How do I uninstall Ubuntu and Grub so I can go back to single booting my (sorry to say it, but it's true) much more robust, reliable XP SP2 system.

Putting OS opinions aside so as to avoid any wars...

1. Simply put in your XP install CD
2. Boot into it (might need to select F2, F8, or F12, etc. while it's booting)
3. Install it.

It takes you through the partition and format processes.


The subject line reminds me of "I want my MTV"... okay, nevermind.

---

### Post by vdawg on 2008-05-09
Bascially I think he already had XP on there, all you need to do is fix your mbr

Check out this thread : [http://www.techzonez.com/forums/showthread.php?t=3975](http://www.techzonez.com/forums/showthread.php?t=3975)

Remember you will need your administrator password if you are using the boot cd. The best option is using a floppy, or I guess if you can boot into your windows partition you can run the command directly from a terminal in there.

Sorry to hear about your problems with ubuntu, maybe you could try a fresh reinstall and see if things work out for you.

good luck!

---

### Post by Monicker on 2008-05-09
You can boot XP into the Recovery Console from the CD, and then use fixmbr to put back the standard Windows mbr.  After that you can delete the linux partition  from Windows, and reformat it as a Windows ntfs one.

---

### Post by zvacet on 2008-05-09
Use your Ubuntu live Cd and whan you come to partition stage delete Ubuntu partition.After that you will not be able to boot in WInXP so follow [this]("http://ubuntuforums.org/showthread.php?t=740221") to recover your Win bootloader.

---

### Post by chrisccoulson on 2008-05-09
I'm sorry that you haven't had such a good experience with Ubuntu, but what particular problems are you having? I tried searching through all your posts, and I only see 5 requests for help, and people tried to help in 3 of these but you never responded to the people that tried to help (these people can't help you unless you respond):

[LIST]
[*][administrative tasks]("http://ubuntuforums.org/showthread.php?t=711462") (Feb 2008), which people responded and tried to help you with but you never continued communication with those people.
[*][LMMS "You probably have no rights to read this file."]("http://ubuntuforums.org/showthread.php?t=781873") (4 days ago), again which someone tried to start helping you with, but you haven't responded.
[*][Package manager stuck in a loop]("http://ubuntuforums.org/showthread.php?t=787974") (only 2 hours ago), which someone has tried to help you with, but you haven't responded with requested information.
[*][speedtouch usb broadband modem]("http://ubuntuforums.org/showthread.php?t=711223") (Feb 2008) - I'm not sure if this one was answered satisfactorily or not
[*][Where do I find my USB drives?]("http://ubuntuforums.org/showthread.php?t=784201") (3 days ago) - noone has responded to this yet, but please bare in mind that not everyone reading it will have the knowledge to respond
[/LIST]

It seems like you aren't that interested in solving your problems

---

### Post by ugm6hr on 2008-05-09
> **the.weavster said:**
> How do I uninstall Ubuntu and Grub so I can go back to single booting my (sorry to say it, but it's true) much more robust, reliable XP SP2 system.

This is the easiest way: [http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe](http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe)

Step 2: http://www.users.bigpond.net.au/hermanzone/p18.htm#STEP_TWO

---

### Post by the.weavster on 2008-05-09
> **chrisccoulson said:**
> It seems like you aren't that interested in solving your problemsActually, I'm not interested in having problems - I just want the OS detect and set up my hardware and to obediently launch the applications I wish to run.

I dabbled with Ubuntu because I got a virus on XP and it took me a whole day to sort it out. That pales to insignificance compared to the hours and aggravation trying to upgrade from Ubuntu 7.10 to 8.04 has caused me and even reformatting the partition and trying to reinstall 7.10 from CD wont work now (3 failed attempts). I'm not trying to start a war about which OS is the best (or least bad) I just don't want to compound my misery by having two lots of trouble.

[QUOTE=ugm6hr]This is the easiest way: [http://www.users.bigpond.net.au/herm...htm#MbrFix.exe](http://www.users.bigpond.net.au/herm...htm#MbrFix.exe)[/quote]Thank you, that worked a treat! Now I just have to try to delete the Linux partitions and get that space back.

Thanks also to everyone else for their suggestions too.

---

### Post by the.weavster on 2008-05-09
> **Th3Professor said:**
> The subject line reminds me of "I want my MTV"... okay, nevermind.That was what was in my head as I typed it :)

---

### Post by RJARRRPCGP on 2008-05-09
> **vdawg said:**
> The best option is using a floppy, or I guess if you can boot into your windows partition you can run the command directly from a terminal in there.



Sorry, usually, floppy=DOS. DOS don't support NTFS, thus unless your partition has the obsolete FAT32, you cannot access the partition!

---

### Post by drthompson on 2008-05-10
Try Paragon's Partition Manager, there's a trial version but to do what you want you'll need to purchase it.  I've gone through the same problem and this solved it in about 10 minutes.  It might be as easy as running the boot manager wizard, of course you'll have to do this in Windows.

---

### Post by bigken on 2008-05-10
boot with your windows xp cd 
press R for recovery console 
select your windows partition usually 1
type fixmbr press enter then type fixboot enter again then type exit 
your pc will reboot into windows in windows just use admin tools to delete and format your linux partitions

---

### Post by ugm6hr on 2008-05-10
> **the.weavster said:**
> Thank you, that worked a treat! Now I just have to try to delete the Linux partitions and get that space back.

Boot with any LiveCD that includes GParted (e.g. Ubuntu), and start the Partition Editor (GParted) in the System->Administration menu.

Select the Ubuntu partition (make sure you pick the right one!) and delete or format to something Windows will recognise (e.g. VFAT).

You could then reformat in Windows to reclaim the space.

---

### Post by Tomatz on 2008-05-10
Happy scanning ;)

---

