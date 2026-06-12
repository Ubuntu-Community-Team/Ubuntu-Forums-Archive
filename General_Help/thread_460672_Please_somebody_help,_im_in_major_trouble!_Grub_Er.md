---
title: "Please somebody help, im in major trouble! Grub Error 17"
date: 2007-05-31
forum: General Help
---

### Post by wvcaudill2 on 2007-05-31
Heres the deal, im going to be grounded for life. Seriously, im at the point of tears. I just gave my dad my old computer which I originally had Windows XP on, and then i made a partition and installed Ubuntu. Well, my Dad said he wanted Ubuntu off, so I went into the Windows Disk Manager, and deleted the Ubuntu partition. I then restarted the computer and got a "Grub Error 17" message! My dad is going to be so mad at me! Please help me! I cant re-install Windows because it came pre-installed on the computer! My God, someone help me!

---

### Post by confused57 on 2007-05-31
> **wvcaudill2 said:**
> Heres the deal, im going to be grounded for life. Seriously, im at the point of tears. I just gave my dad my old computer which I originally had Windows XP on, and then i made a partition and installed Ubuntu. Well, my Dad said he wanted Ubuntu off, so I went into the Windows Disk Manager, and deleted the Ubuntu partition. I then restarted the computer and got a "Grub Error 17" message! My dad is going to be so mad at me! Please help me! I cant re-install Windows because it came pre-installed on the computer! My God, someone help me!

First thing you should probably do is reinstall Ubuntu...once you're able to boot into Windows or Ubuntu, make a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

The SGD can restore your Window's IPL code to the mbr...then you can delete the Ubuntu partition, once you can boot Windows.

OR

If you have access to another pc, burn the SGD on it, then use it to restore your Window's IPL code.

---

### Post by wvcaudill2 on 2007-05-31
Ok, do I just burn the iso staright onto a CD, or do I get the files out of it? MY DAD IS HOME! RESPOND QUICKLY PLEASE!

---

### Post by wvcaudill2 on 2007-05-31
And if this works will it restore my computer to exactly how Windows was before???

---

### Post by wvcaudill2 on 2007-05-31
Well, i downloaded the file and put it on a cd, then extracted it to that same CD, and then I went and put it into the computer, and it still loaded with Grub Error 17! Please, somebody help!

---

### Post by confused57 on 2007-05-31
> **wvcaudill2 said:**
> And if this works will it restore my computer to exactly how Windows was before???

To burn an iso correctly, it must be burned "as an image", not as a data or bootable cd, burn it at a low speed(8x or less)...then set your bios to boot your cd drive before your hard drive.  Just look for an option in your cd burning program to burn an "image".

Yes, SGD "should" be able to get your Windows booting just as before.

Added:  Don't extract the iso before burning it.

Another way would be to make a Win98SE oem boot floppy(if you have a floppy drive):
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by wvcaudill2 on 2007-05-31
Ok, im not sure how to make it an image or whatever, but I used MagicISO, and im going to go try what you said. My Dad went to bed so I can sneak downstairs. I hope to God it works.

---

### Post by wvcaudill2 on 2007-05-31
I tried to do what you say. I inserted the CD, when my computer started to load a pressed the f1 key for system setup, but I couldnt find the BIOS thing. There were sections at the top though that i could go to. There was Main, Advanced, Power, Boot, and Exit. And under Main was a thing called BIOS Revision, but it was grey so I couldnt go to it. Please help!

---

### Post by confused57 on 2007-05-31
> **wvcaudill2 said:**
> I tried to do what you say. I inserted the CD, when my computer started to load a pressed the f1 key for system setup, but I couldnt find the BIOS thing. There were sections at the top though that i could go to. There was Main, Advanced, Power, Boot, and Exit. And under Main was a thing called BIOS Revision, but it was grey so I couldnt go to it. Please help!
I would think the "Boot" section would be what you want.  How did you boot the Ubuntu live cd when you first installed Ubuntu to your computer?  You would do the same thing to boot SGD.

---

### Post by wvcaudill2 on 2007-05-31
I cant remember how I installed Ubuntu. But, on the boot screen, there is:
>Boot-Time Diagnostiic Screen [Disabled]
>Boot Device Priority
   >>1St Boot device [Floppy]
   >>2ND Boot Device [Cd]
   >>3RD Boot Device [Hard Drive]
    >>4TH Boot Device [Disabled]
>Hard Drive Boot Priority
>Floppy Device Priority
>CD-ROM Device Priority



Please note that all the items with >means they can be expaned, and all the ones marked with a >> belong to the one above them. Such as all the 1st through 4th boot device things belong under the Boot Priority

---

### Post by handydan918 on 2007-05-31
Ya know, if none of the rest of it works, you could edit the /boot/grub/menu.lst file and make windows the default O/S for booting. That would be almost as good as not having Linux installed at all, because you can just push the idiot button on the front, walk away, and windows will boot automatically.
Just a thot...:rolleyes:

---

### Post by confused57 on 2007-05-31
> **wvcaudill2 said:**
> I cant remember how I installed Ubuntu. But, on the boot screen, there is:
>Boot-Time Diagnostiic Screen [Disabled]
>Boot Device Priority
   >>1St Boot device [Floppy]
   >>2ND Boot Device [Cd]
   >>3RD Boot Device [Hard Drive]
    >>4TH Boot Device [Disabled]
>Hard Drive Boot Priority
>Floppy Device Priority
>CD-ROM Device Priority



Please note that all the items with >means they can be expaned, and all the ones marked with a >> belong to the one above them. Such as all the 1st through 4th boot device things belong under the Boot Priority
I believe your bios is set up correctly, but I'm not sure if the SGD iso is burned correctly.
Check the name of the SGD file that you downloaded, is it an iso file or a bzip file?
In your working pc, with Windows running,  place the SGD cd that you burned in the cd drive...does it show 1 big file or several files & folders?

Look for options in your cd burning program for "image",  most cd writing programs have this.

---

### Post by wvcaudill2 on 2007-05-31
Anyone there?

---

### Post by confused57 on 2007-05-31
> **wvcaudill2 said:**
> Anyone there?
I'm back,  can you answer the questions I asked in my last reply?  That'll help determine what  the problem might be.  Also, you might try booting up the Ubuntu live cd, just to make sure that your pc is indeed booting first from the cd drive...just a test.

---

### Post by wvcaudill2 on 2007-05-31
Oh, sorry, I didnt see your post. Okay. the name of the file I downloaded was "sgd_source_code_0.9590". My computer, the one that is running, says it is a MagicISO Document, so I assume its an ISO file. When I expllore the CD, there are 3 file/folders, Boot, rr_moved, and boot.catalog. In MagicISO, the program I use for iso files, I see no image options. But then, im not very experienced with MagicISO. As a test, I inserted my Ubuntu 6.10 CD, and it booted from that! And, it gave me all the normal options. I left it at that though. So, maybe there is a way to re-install Ubuntu and it will fix everthing???

---

### Post by confused57 on 2007-05-31
> **wvcaudill2 said:**
> Oh, sorry, I didnt see your post. Okay. the name of the file I downloaded was "sgd_source_code_0.9590". My computer, the one that is running, says it is a MagicISO Document, so I assume its an ISO file. When I expllore the CD, there are 3 file/folders, Boot, rr_moved, and boot.catalog. In MagicISO, the program I use for iso files, I see no image options. But then, im not very experienced with MagicISO. As a test, I inserted my Ubuntu 6.10 CD, and it booted from that! And, it gave me all the normal options. I left it at that though. So, maybe there is a way to re-install Ubuntu and it will fix everthing???

Yes, I agree...for now, I think the best idea would be to reinstall Ubuntu...you'd then be able to boot Windows & Ubuntu.  Also, there's an excellent iso burning program(Gnomebaker) in Ubuntu, that you can use to burn the SGD iso as an image.   Once you get your SGD correctly burned & you're able to boot the cd...then read the first link I gave you in my first reply, there's some excellent instructions for what you need to do to restore your Window's IPL code to the mbr.

---

### Post by wvcaudill2 on 2007-05-31
So if I install Ubunu I will be able to boot Windows, but it wont be like it was before until I do what you told me to do in your first reply?

---

### Post by confused57 on 2007-05-31
> **wvcaudill2 said:**
> So if I install Ubunu I will be able to boot Windows, but it wont be like it was before until I do what you told me to do in your first reply?

Correct, you "should" be able to boot Windows & Ubuntu by reinstalling.  Just make sure not to format your Window's partition & you should be OK.  Burn the SGD iso in Ubuntu, using Gnomebaker or I think Ubuntu comes with a cd writing program(Gnomebaker is easy to install using Synaptic Package Manager).

Have you seen this guide for installing with the Desktop live cd?:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

You might especially want to read the section for "manual partitioning".

---

### Post by wvcaudill2 on 2007-06-01
Okay, I was re-installing Ubuntu, and before it loaded it said something about the screen resolution not being right. I think thats because my screen is a TV aswell. Its completely loaded now . . . . Ok, its opened up into the desktop now, so im going to click the install link. I went through the install using the guide you gave me. I hope I did the partitions right. I used the previous partition for Ubuntu and the swap partition, and reformatted those, and i didnt touch the partitions for windows. I left them mounted as /media or something.

---

### Post by confused57 on 2007-06-01
> **wvcaudill2 said:**
> Okay, I was re-installing Ubuntu, and before it loaded it said something about the screen resolution not being right. I think thats because my screen is a TV aswell. Its completely loaded now . . . . Ok, its opened up into the desktop now, so im going to click the install link. I went through the install using the guide you gave me. I hope I did the partitions right. I used the previous partition for Ubuntu and the swap partition, and reformatted those, and i didnt touch the partitions for windows. I left them mounted as /media or something.
I believe you set up the install partitioning correctly, sounds like it should work.

Added:  If your reinstall goes well, which it should...you could set up grub to automatically boot Windows, without showing the grub boot menu...your Dad wouldn't even know Ubuntu is on the pc.  If you want to consider this, I'll walk you through how to set it up.

---

### Post by wvcaudill2 on 2007-06-01
It worked! I can now get into Ubuntu and Windows! Thanks everyone for your help! Now, im not even going to try to delete Ubuntu after all this toruble, but is there any way to make Windows boot first unless someone selects to load Ubuntu first?

---

### Post by confused57 on 2007-06-01
> **wvcaudill2 said:**
> It worked! I can now get into Ubuntu and Windows! Thanks everyone for your help! Now, im not even going to try to delete Ubuntu after all this toruble, but is there any way to make Windows boot first unless someone selects to load Ubuntu first?

Yes you can...great idea.

All the information you need is in this link:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Read the link, but basically what you would do is edit your /boot/grub/menu.lst:

1.)Remove the # in front of hidden menu
2.)Set the timeout to something like 3 (seconds), you can press "Esc" within the 3 seconds to enter grub menu to boot Ubuntu.
3.)To default to boot Windows(see the link), see how to adjust the number to boot your Window's entry.
The method I prefer to do is to place the Window's entry above the ###BEGIN AUTOMAGIC KERNELS LIST...you could just copy & paste(won't hurt to leave the original Window's entry at the very end of the menu.lst file).

---

### Post by Kuoi on 2007-06-01
Type in terminal > sudo gedit /boot/grub/menu.lst and send here the outcome of it.

That way we can sure help.

Otherwise you can try to change these settings , but maybe first backup your grub file.

Look in the Grub file for the following text , it can change a bit , but it's something like it.> ## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		[COLOR="Red"]saved[/COLOR]


If there's is a number , cange it to "saved" ( see RED text ).

Now search at the bottom of the page for  your Windows , must be something like this > # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP Professional
root (hd0,0)
makeactive
chainloader +1
[COLOR="Red"]savedefault[/COLOR]

Add "savedefault" under it (see RED text )

Now save the Grub file , and it should boot to Windows.

If you want to change more settings , just let us know , Kuoi

---

### Post by Neobuntu on 2007-06-01
Um, you had XP, added Ubuntu. Deleted Ubuntu partition (with GRUB stage 2 -the menu- on it) and now, booting (the Master Boot Record) can't find the partition, right?

If that 's correct and you just want XP back and no Ubuntu then why not just reinstall the Windows direct (no menu) MBR (and let Windows recover the partition space or use it as drive D:).

You'll probably want to use the partitioner "gparted" on the live ubuntu CD to delete (CAREFULLY) the ubuntu created partitions and expand the XP (NTFS file system; most likely) so that when you start Windows XP it will recover the space. 

I think ```
fdisk /MBR
``` from a XP CD (or boot CD with fdisk for XP from the net maybe).

---

### Post by Neobuntu on 2007-06-01
All that said, perhaps you should install Kubuntu instead (in the blank space and not expand back the Windows part), let it do the grub (and everything else) and ask your Dad how he likes Kubuntu. 

Note that I had a non-technical client freak out over how difficult it was to copy a commercial DVD (like it's any harder with Kubuntu, HA!) and he request removal of Kubuntu (because Window is thought to be easy, HA!). I said no problem, I can do it post haste. BUT, I simply asked if he was sure that he wanted to give up all that Kubuntu has to offer. Also, I explained that he wasn't using much hard drive space anyway. Guess what? he decided to keep Kubuntu (just in case)!

---

### Post by DerArzt on 2007-06-01
Neobuntu, if you read the original post, he says he doesn't have an xp disk, so he couldnt just boot ro recovery mode and run fixboot and fixmbr

---

### Post by wvcaudill2 on 2007-06-01
My dad is keeping Ubuntu! I told him about all the trouble, and he said to just leave it :)

---

### Post by handydan918 on 2007-06-02
HAH!! You're going to live after all!!

---

### Post by Neobuntu on 2007-06-11
> **DerArzt said:**
> Neobuntu, if you read the original post, he says he doesn't have an xp disk, so he couldnt just boot ro recovery mode and run fixboot and fixmbr

Hey I said from the net or someplace. Then I said, just install Kubuntu and GRUB comes with it. So GRUB should boot XP too. K?

It seems like he just reinstalled Ubuntu. Close enough.

Smart choice "Dad".

---

