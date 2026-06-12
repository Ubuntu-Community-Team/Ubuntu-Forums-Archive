---
title: "How to uninstall Ubuntu?"
date: 2008-06-19
forum: General Help
---

### Post by Felliph3 on 2008-06-19
I am running Ubuntu on my Acer laptop and it has 2 internal hard drives(45GB C:\ and 45GB D:\). When I made a dual boot with Windows and Ubuntu 1 of my hard drives was formatted to accommodate Ubuntu. Now I have 1 normal hard drive(45GB C:\) and a 3GB (F:\) that was made from the Ubuntu installation. D:\ is apparently about 42GB and is being used by Ubuntu and I cannot access it in Windows.

I would like to uninstall Ubuntu and the grub loader,etc,etc and also get my 2 drives back. 2 45GB drives instead of having 1 45B hard drive, 1 3GB hard drive and 1 42GB hard drive. I just want 2 hard drives back.

How can I do this? Is there a way to format D:\ into a windows format and with this format clean the Ubuntu slate and be back like normal again when it came from the factory?

BTW the reason why i dont want ubuntu is that I need my space on windows and it runs like complete **** since i have a crap video driver that makes ubuntu very laggy. Thanks

---

### Post by x_hxc on 2008-06-19
So you partitioned D:\ for Ubuntu, as i read. 

In Windows:

What you can do is on your 'My computer' button, right click it and select 'Manage'. Go to Disk Management. You should then see all of your hard drives. For the 42gb(since this is what Ubuntu is partitioned on), right click and delete. The 42gb should now be labeled unallocated. Now, right click 3gb(originally D:\) hardrive and click extend and you should have an option how much to extend it to which would be the 42gb. 

Have you tried this already?

---

### Post by Felliph3 on 2008-06-19
Very sorry. Turns out I have C:\ (45GB) D:\ (3GB) and F:\ (391MB) I have not tried going into manage though, ive never been there b4 actually. Ill look into which drive i should take care of. Thanks


Heres a picture

[IMG]http://img518.imageshack.us/img518/5383/partitionyl5.jpg[/IMG]

---

### Post by Felliph3 on 2008-06-19
Ok. I have deleted F:\ and the 3 blanks. So I just have D,C, and PQSERVICE. I dont know how to connect the free space (42.20GB) to D:\. I dont see extend on the right click.

---

### Post by x_hxc on 2008-06-19
You were to delete the drive which Ubuntu was partitioned on. So it was F:\ then? And you should delete the three top volumes that i see in your picture. Then try right clicking D:\ and extend it to all of the unallocated space.

---

### Post by x_hxc on 2008-06-19
Lol well i was slow to that reply. They are labeled unallocated right? I use vista so i'm not sure if it's different in xp for the extending part.

---

### Post by Felliph3 on 2008-06-19
I renamed F to D so that i could turn that unallocated space to D. I am now formating the new D. F which used to be D will be deleted once i move the files in there to C and after all is said and done I will have C and D :-)

Thanks a lot man, your really helped me out. I thought that getting rid of ubuntu would be a pain in the *** but it was very easy. Thanks!

---

### Post by x_hxc on 2008-06-19
Hopefully everything works out :) I've never repartitioned in xp since Vista has the 'do it yourself' programmed within it so that you can move stuff about wihtout reformatting. 
GL Hope it works.

---

### Post by Felliph3 on 2008-06-20
Yeah I got everything back fine. Havent restarted yet so idk if it will crap out on me as far as loading windows goes but yeah it really should work. 

The drives are good now, I have C and i have D and theyre both 45GB each


:-)

---

### Post by Felliph3 on 2008-06-20
Ok. As I feared when I restarted the pc it would not start back up. The boot loader Gives me error 21 and stays there loading. I left it overnight by mistake and when I woke up it was still flashing the _ . What am i supposed to do now?

---

### Post by jocko on 2008-06-20
> **Felliph3 said:**
> Ok. As I feared when I restarted the pc it would not start back up. The boot loader Gives me error 21 and stays there loading. I left it overnight by mistake and when I woke up it was still flashing the _ . What am i supposed to do now?

You need to repair the mbr of your hard drive (that's the part of the hard drive where the boot loader is installed. When you installed ubuntu, grub was installed instead of the windows boot loader, and when you formatted the ubuntu partition you lost the folder where grub looks for it's configuration files).
To fix the mbr you need a windows install cd, which you can boot into recovery mode and use the command "fixmbr".

If you don't have a windows install cd, there may be some good tools you can download that can do the same.
I think [Super Grub Disk]("http://www.supergrubdisk.org/") may have an option to remove grub and restore the windows mbr.

---

### Post by x_hxc on 2008-06-20
^ Yup, had to do the same thing the first time i uninstalled Ubuntu. Grub is the most evil mbr :D. This helped me before.


Edit** Just incase "fixmbr" doesn't work for you (for some it doesn't) try "fdisk /mbr")



> If for some reason you find the need to get back to your Windows XP bootloader instead of the one installed by your Linux distro, simply follow these instructions:

1. Boot up with your Windows XP disc.

2. Select the option Recovery Console.

3. At the prompt, type "fdisk /mbr" (without the quotes of course)

4. Restart your computer.

----->[SOURCE]("http://www.neowin.net/forum/index.php?showtopic=292614")<-----

---

### Post by Djinn Effer on 2008-06-20
Oh shi---

When I first saw this topic my jaw dropped when I read the first instructions you were given and were about to follow... Then I sighed as I saw that you did actually end up following them before I could warn you against it. Dang!

Ok so basically... Never remove non-windows native partitions in the disk manager, sometimes you WILL have problems, and you are taking that huge risk. When I deleted the partition Ubuntu was on through the way you were instructed a year ago, it deleted the entire disk, rather than just the partition.

I had to use Hiren's Boot CD & Partition Recovery 3.0 to get *mostly* everything back. Here's one thread on that on another forum: [http://www.techsupportforum.com/microsoft-support/windows-xp-support/166541-hard-drive-disappeared-randomly.html#post974713](http://www.techsupportforum.com/microsoft-support/windows-xp-support/166541-hard-drive-disappeared-randomly.html#post974713)

And here was the thread on these forums: [http://ubuntuforums.org/showthread.php?p=2994440#post2994440](http://ubuntuforums.org/showthread.php?p=2994440#post2994440)

So, for future reference, here are instructions how to uninstall:

1. FIRST before you do ANYTHING else, fix your MBR, easiest way to do this is [Super GRUB](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html), there are other ways though. You can see [this](http://www.users.bigpond.net.au/hermanzone/p18.htm#STEP_ONE) page for many examples of how to do so.
2. Remove the partition with a program. Not the Windows one. Personally, I use Acronis Disk Director Suite, I hear GParted is alright too, as well as most "Parted" partitioners, as they're Linux friendly, where as not all Windows programs are.

If you have problems, see the aforementioned page. It has quite a lot of info, and I see it even mentions me, lol.

---

### Post by Felliph3 on 2008-06-21
Hmm. Odd, i had posted the follow up but I guess the internet took a crapper when i hit post so it didnt show up. 

Right after I posted my last msg this is what happened:

I stumbled across an IOLO Technologies CD that i had burned which came with System Mechanic I believe and it has restore functions. Basically, I booted with that and it had a FIX MBR checkbox. It said it was corrupt. I checked it and hit next to fix it. It fixed the MBR in 2 secs haha. Immeadiatly restarted and fired windows up :guitar:

I didnt have anything that i wanted to keep in ubuntu. All my files were on C so i was ok. It worked out perfect though. I now have a C and D drive both 45gb each and my windows boots without the sight of grub, i wonder what happened to it. Its gone now i suppose. windows boots and everything is fine. Im glad i found that cd though since i didnt have any blanks that i could burn super grub into. :lolflag:

Thanks for everyone that helped out.

---

