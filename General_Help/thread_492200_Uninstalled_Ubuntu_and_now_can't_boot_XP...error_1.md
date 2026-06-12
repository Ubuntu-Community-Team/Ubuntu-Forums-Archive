---
title: "Uninstalled Ubuntu and now can't boot XP...error 17"
date: 2007-07-04
forum: General Help
---

### Post by likemyredhair on 2007-07-04
So I decided that I was going to delete Ubuntu from my laptop.  I liked Ubuntu but I never got the wireless working so it was just taking up space on my hard drive.  I read on some other site that to uninstall Ubuntu to use a Windows disk manager program and delete the partition that it is on.  So I did that and re-booted my computer.  Now when I start my computer it says:
"GRUB loading, please wait...
Error 17"
I'm using an HP laptop.  Ubuntu and XP are (were) on the same hard drive.
Any help would be greatly appreciated, especially since I can't use my laptop now.

---

### Post by xubu_caapn on 2007-07-04
you got rid of grub, your bootloader. it comes with ubuntu and overwrites the windows bootloader.

i used this handy disc: [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/) to restore my windows xp bootloader when i needed to. worked great, just follow the prompts to "fix windows mbr" or something equivalent.

---

### Post by louieb on 2007-07-04
Yes its a common mistake. GRUB should have been replaced first. Now its just a little harder. [Remove/Replace Grub (Dual Boot Site)]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

---

### Post by mattyrigby00 on 2007-07-04
boot to an xp cd, go into the recovery console and type fixmbr, then fixboot (press yes when it asks each time), then reboot. this will restore the old windows MBR and remove grub.

---

### Post by likemyredhair on 2007-07-05
thanks for the responses!!!
ok I'll give these a try... and let you know how it goes
btw is there a way to make the partition Ubuntu was on go away or am I stuck with it?

---

### Post by bigken on 2007-07-05
just use windows disc manager to reformat it as ntfs

---

### Post by likemyredhair on 2007-07-05
I just tried the the Super Grub disk.  It doesn't work for me.  I tried it two ways.  I made one a bootable CD using the ISO (with Cheetah CD Burner) and then extracted the ISO and made a data disk.
With the bootable CD it doesn't show anything (after the HP symbol), there is just a blinking _ .
With the data disk it does the same as before...error 17.
Maybe I don't know how to put it onto disk.

I'll try what LouieB suggested now.

To mattyrigby00, I don't know where any XP cds are.  Maybe I could ask someone I know if they have one.

To bigken, I can't boot Windows

---

### Post by splintercellguy on 2007-07-05
You have burned the ISO incorrectly. What you want to do is to select an ISO Burning option in your CD burning program. The point is that the program should be writing the contents of the ISO to the CD, not write the ISO file to CD.

---

### Post by likemyredhair on 2007-07-05
> **bigken said:**
> just use windows disc manager to reformat it as ntfs

oh, did you mean to fix the partition?

---

### Post by splintercellguy on 2007-07-05
He meant that you should have Windows Partition Manager format over the old Ubuntu partition as NTFS.

---

### Post by likemyredhair on 2007-07-05
> **splintercellguy said:**
> You have burned the ISO incorrectly. What you want to do is to select an ISO Burning option in your CD burning program. The point is that the program should be writing the contents of the ISO to the CD, not write the ISO file to CD.

I used "Burn ISO", selected the ISO file and it burned it.  But its not loading on my laptop. ... "Error 17"

---

### Post by splintercellguy on 2007-07-05
Is your boot order set so that the CD-ROM drive goes first? If burned and booted properly, you should get some cool text from the Super GRUB CD.

---

### Post by likemyredhair on 2007-07-05
I got the super grub disk running...
now...I'm at a black and blue screen:

"Gnu/Linux
Windows
Boot & Tools
Advanced
Quit"

I'm not sure where to go from here

---

### Post by splintercellguy on 2007-07-05
Windows -> Fix Windows boot or something like that, the little blurbs for each option when you select one should tell you.

---

### Post by likemyredhair on 2007-07-05
nice...I got it to work!...i mean, uh, WE got it to work. ha

thanks a lot everyone!!!  

now I'll work on that partition.
and then putting Ubuntu on an old iMac... I've had trouble in the past with it.  If I remember correctly, it would start working and then the screen would go black.  Know anything about that?

---

### Post by splintercellguy on 2007-07-05
Hmm, not much of a Mac person. iMacs are PowerPC amirite, so you probably need to use Dapper. I suggest posting in Apple PPC for help.

---

### Post by likemyredhair on 2007-07-05
how do I reformat the partition to ntfs with disk management?

---

### Post by splintercellguy on 2007-07-05
Right-click the partition entry and select Format.

---

### Post by likemyredhair on 2007-07-05
> **splintercellguy said:**
> Right-click the partition entry and select Format.

I don't have that option.  Am I using the right program?

I run "compmgmt.msc" and it opens Computer Management.  Then I click on Disk Management on the left side.

---

### Post by splintercellguy on 2007-07-05
Can you post a screenshot of the window? Personally I prefer to use GPartEd for this stuff :).

---

### Post by likemyredhair on 2007-07-05
> **splintercellguy said:**
> Can you post a screenshot of the window? Personally I prefer to use GPartEd for this stuff :).

[img]http://www.dropshots.com/photos/70204/20070705/052458.jpg[/img]
[Photo Sharing](http://www.dropshots.com/) - [Upload Video](http://www.dropshots.com/) - [Video Sharing](http://www.dropshots.com/)


its not actually vista, just a vista theme

---

### Post by bigken on 2007-07-05
go to control panel administrave tools then select computer management disk management

---

### Post by likemyredhair on 2007-07-05
> **bigken said:**
> go to control panel administrave tools then select computer management disk management

yeah, this is the same program i was using.

ok i noticed that with the list of partitions on the top, when I right click them, format *is* an option.  but the partition that linux was on is not on that list.

---

### Post by bigken on 2007-07-05
it should show as unknown

---

### Post by bigken on 2007-07-05
another way would be to use gparted liveCD which was mentioned earlier ;)

you might even be able to resize your ntfs partitions

---

### Post by likemyredhair on 2007-07-05
> **bigken said:**
> it should show as unknown

[img]http://www.dropshots.com/photos/70204/20070705/055152.jpg[/img]

ok I'll just check that program out

---

### Post by bigken on 2007-07-05
thats its just right click and and follow the prompts

---

### Post by likemyredhair on 2007-07-05
> **bigken said:**
> thats its just right click and and follow the prompts

the partition im talking about is the black one there..."Unallocated"
its not up there on that list on the top... the blank one up there is the lighter blue one on the right on "Disk 0"

when i right click "Unallocated" i get the options:

New Partition...
Properties
Help

---

### Post by bigken on 2007-07-05
new partition

---

### Post by likemyredhair on 2007-07-05
> **bigken said:**
> new partition

ok...
should I mount it with C: in the New Partition Wizard?

---

### Post by bigken on 2007-07-05
you can use any letter you like as long as its not taken

---

### Post by bigken on 2007-07-05
I noticed you have WD passport is that the black 2.5in hdd if it is I would backup any data on it had one a few weeks back to recover data got 75% of it drive just crashed no reason also read somewhere its a common problem with that drive

---

### Post by likemyredhair on 2007-07-05
> **bigken said:**
> I noticed you have WD passport is that the black 2.5in hdd if it is I would backup any data on it had one a few weeks back to recover data got 75% of it drive just crashed no reason also read somewhere its a common problem with that drive

its a portable external hard drive...same one?

---

### Post by likemyredhair on 2007-07-05
ok so the partition is formatted as ntfs
so can i make this one and the original C: back into one?

---

### Post by bigken on 2007-07-05
you can try using gparted Live CD to try and do this

---

### Post by likemyredhair on 2007-07-05
I'm running the gparted live cd,
should I resize the old linux drive to be really small and then just extend the C: drive or is there a way to make the two into one?

---

### Post by bigken on 2007-07-05
delete the linux drive and see if you can extend the windows partition but be careful

---

### Post by likemyredhair on 2007-07-05
> **bigken said:**
> delete the linux drive and see if you can extend the windows partition but be careful

gulp...haha
how do you mean be careful?

---

### Post by Brucevdk on 2007-07-05
> **likemyredhair said:**
> gulp...haha
how do you mean be careful?

Delete the ext3 partition or whatever you've made it into and then resize the NTFS partition into the unallocated space. I've done it many times before, it didn't go wrong for me. There's always a chance it won't go right so backup your data.

---

### Post by bigken on 2007-07-05
like ur man says backup your data

---

### Post by likemyredhair on 2007-07-05
deleted the "linux" partition and extended the C: drive
works great
thank you thank you thank you

---

### Post by bigken on 2007-07-05
:lolflag: so you got there in the end

---

