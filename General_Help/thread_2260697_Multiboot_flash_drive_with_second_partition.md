---
title: "Multiboot flash drive with second partition"
date: 2015-01-13
forum: General Help
---

### Post by C.S.Cameron on 2015-01-13
I am trying to boot an iso on the second partition of a multiboot flash drive.
(Experimenting with multiple casper-rw persistence files).
I figure using the UUID is the way to go but I can't seem to get the iso to boot.
Following is the grub.cfg file, the last ubuntu menuentry is among the attempts that failed to boot.
This grub.cfg file was built using Kumar and Ima's MultiBootUSB script.


```
set default="1"
set timeout=10
if loadfont /boot/tools/fonts/unicode.pf2 ; then
set gfxmode="640x480"
insmod gfxterm
insmod vbe
terminal_output gfxterm
if terminal_output gfxterm; then true ; else
terminal gfxterm
fi
fi
insmod tga
if background_image /boot/tools/images/bg.tga ; then
set color_normal=blue/black
set color_highlight=red/black
else
set color_normal=white/black
set color_highlight=white/light-gray
fi

menuentry "First Partition of First HDD" {
set root=(hd0,1)
chainloader +1
}

GRUB_GFXMODE=1024x768x16
insmod vbe


	menuentry "ubuntu-12.04-desktop-i386" {
		loopback loop /boot/iso/ubuntu-12.04-desktop-i386.iso
		linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/ubuntu-12.04-desktop-i386.iso noeject noprompt -- persistent
		initrd (loop)/casper/initrd.lz
	}


	[COLOR="#FF0000"]menuentry "ubuntu-14.04-desktop-i386" {
		set root=UUID=8282-274E
		loopback loop /8282-274E/ubuntu-14.04-desktop-i386.iso
		linux (loop)/vmlinuz iso-scan/filename=/8282-274E/ubuntu-14.04-desktop-i386.iso noeject noprompt -- persistent
		initrd (loop)/initrd.lz
	}[/COLOR]


	menuentry "Restart" {
		insmod reboot
		reboot
	}
	
	menuentry "Shutdown" {
		insmod halt
		halt
	}


```

---

### Post by sudodus on 2015-01-14
I was able to boot from a second iso file when it was copied/cloned into the second partition. See this link, where I think it is explained well enough.
[URL="http://ubuntuforums.org/showthread.php?t=2259682"]
One pendrive for all PC (Intel/AMD) computers[/URL]

But I did not solve the problem, that is your main problem now - separate persistence with multiple casper-rw persistence files. *Good luck*, it would be valuable to get a solution to this problem :-)

-o-

Maybe it would work, if the content of the iso file is copied to a FAT32 file system in the second partition and a casper-rw file there would be identified as belonging to that system, while a casper-rw file in the first partition would be identified as belonging to the system in the first partition - I don't know, I'm only writing down my thinking.

---

### Post by sudodus on 2015-01-14
If you want to go along the grub 2 path, maybe this excerpt from the 40_custom file in my production computer might help

```
menuentry "Boot UBUNTU 10+ BASED SYSTEM from /media/multimed-2/CD/candidate.iso" {
 set isofile="/CD/candidate.iso"
 set root='(/dev/sda,msdos2)'
 search --no-floppy --fs-uuid --set=root d3f3f4a3-3d6e-4e4f-8e1a-c2f0de792f90
 loopback loop ($root)$isofile
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
 initrd (loop)/casper/initrd.lz
}
```

I used it a lot before to hard link iso files to "/media/multimed-2/CD/candidate.iso" and boot from them. Not so much any more, but it works well. Maybe you have some problems with defining the partition. Try using the search command like I do. (I learned this method from *jerrylamos*).

---

### Post by C.S.Cameron on 2015-01-14
Thanks Sudodus:
I will give it a try as soon as I get some time.
What I noticed so far is that when plugging a persistent flash drive into an old 4GB EEE running a persistent install on the internal drive, the default casper-rw file is the internal one.
Probably the casper-rw the boot process first sees is the one that is used. 
Not sure how to control this yet.

---

### Post by C.S.Cameron on 2015-01-14
Thanks again Sudodus:
I got the iso on the second partition to boot by modifying your suggestion to:

	menuentry "ubuntu-12.04-desktop-i386 Partition 2" {
 		set isofile="/ubuntu-14.04-desktop-i386.iso"
 		set root='(/dev/sda,msdos2)'
		search --no-floppy --fs-uuid --set=root 8282-274E
		loopback loop ($root)$isofile
		linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile persistent noprompt noeject
 		initrd (loop)/casper/initrd.lz
	}

Only problem is that the Ubuntu on the second partition is still using casper-rw on the first.
Hmm, perhaps if I put the ubuntu and casper-rw from the first partition onto a third partition???

---

### Post by sudodus on 2015-01-14
Is there a ***grub command*** to rename a file (casper-rw file) or re-label a partition (casper-rw partition) from and to something else? I had a look at a tutorial with a list of grub commands but did not find such a command, but there might be some work-around.

---

### Post by yancek on 2015-01-14
> [COLOR=#FF0000]menuentry "ubuntu-14.04-desktop-i386" {
		set root=UUID=8282-274E
		loopback loop /ubuntu-14.04-desktop-i386.iso
		linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/ubuntu-14.04-desktop-i386.iso noeject noprompt -- persistent
		initrd (loop)/casper/initrd.lz
	}[/COLOR]

Your original entry in the first post did not work because you had the UUID on the 'linux' line which is not necessary as the set root line already 
points to it.  You also did not have casper preceding the vmlinuz and initrd lines which is necessary because that is where those files are located.  
I also always have used the "boot=casper" which I think is necessary although I've never tested without it.  This should also work and is just a different
method than the one you got to work above.  When a set root line is used, it always has single quotes.  Might need that with UUID also but I'm not sure as 
I've never used UUID in this type situation.

I'm not sure why you are not able to use the casper-rw on the second partition if it exists.

---

### Post by sudodus on 2015-01-14
The idea is to check if it is possible to have separate casper-rw files for different live systems in the same pendrive. Can we make the installer select the one we want it to select, when there are two or more of them?

---

### Post by yancek on 2015-01-14
> What I noticed so far is that when plugging a persistent flash drive  into an old 4GB EEE running a persistent install on the internal drive,  the default casper-rw file is the internal one.

I'm not sure what the OP is referring to above or why he would have a persistent install on an internal drive, frugal install with unetbootin or similar software??

You can create a casper-rw partition and have it be accessible from different systems.  
I installed grub2 on a flash drive then copied the iso files for Ubuntu 14.04, Lubuntu 14.04 and Mint 17 to that partition.  I created a grub.cfg file for these iso files and tested to verify they all booted which they did.  I then booted Ubuntu from the hard drive and used GParted to create a second partition with the remaining unallocated space on the flash drive formatted ext2 and labelled casper-rw.  I then created directories for each on the casper-rw partition.  I then booted Ubuntu and Lubuntu from the flash drive and was able to create directories in the /home/user for each.  The lubuntu and ubuntu directories I created for each were also available in the root of the filesystem and I created test directories on each.  In both all the directories I created were saved on reboot.  So basically, this isn't exactly what the OP was referring to but he could have separate directories on the casper-rw partition for each install.  I think having a separate casper-rw partition is better than casper-rw files.  The lubuntu directory in casper-rw is available in Ubuntu and the ubuntu directory is available in Lubuntu.  That could be an advantage or disadvantage, depending on what the user wants.

The Mint did not work.  When I booted, I got an error the MDM user mdm does not exist, please correct in MDM configuration, then authentication failure.

Before doing the above, I tried separate partitions for each and created a casper-rw file on each partition.  I had problems booting Ubuntu as I kept getting "system running in low graphics mode and saw several options, none of which did anything for me.  I was able to create a directory and save on reboot in Lubuntu and then did the same with Mint but when I rebooted Lubuntu it wouldn't boot so I gave up on that.  I had no problem rebooting and creating files on Mint in this scenario but Ubuntu and Lubuntu didn't work.

I don't know if multiple casper-rw files would work, I tend to think not but I haven't spent that much time on it.   Since creating a partition requires a label of casper-rw, it wouldn't be possible to create multiple partitions, at least I don't know any way.

I made an dual-boot flash drive with persistence for two systems but only one was an Ubuntu, Peppermint Linux and the other was Knoppix which has a different label name for its persistence.

Maybe the OP will have better luck.

---

### Post by sudodus on 2015-01-15
Thanks [URL="http://ubuntuforums.org/member.php?u=1928724"][B][COLOR=#000000]yancek,

[/COLOR][/B][/URL] for the description of what you have managed to get working with multiple users in a casper-rw partition. I think it can be a good alternative in several cases, but I'm afraid it will be necessary to have different casper-rw units (files or partitions) for one 32-bit and one 64-bit system, if program packages are installed. If that is not possible, it might be better to have one live system (with persistence) and one installed system, or two installed systems in the pendrive.

If it is necessary at all to have more than one system :-P What would you suggest to provide a pendrive that works in anything from an old 32-bit computer to a new UEFI computer?

---

### Post by yancek on 2015-01-15
I made the mistake of trying to get the Mint to boot by resolving the " MDM user mdm does not exist, please correct in MDM configuration, then authentication failure" error I posted yesterday.  I found some information on the Mint forums which enabled me to boot Mint but that created other problems.  After doing this, Lubuntu would not boot at all.  The Lubuntu logo showed then a black screen for 5 minutes so I shut down.  I then booted Ubuntu and instead of seeing user ubuntu at the login screen I saw user mdm.  Tried a number of different passwords, none of which worked.  I think the method would work with just Ubuntu and Lubuntu but I think it would only be useful for storing data and not additional software.

I removed the Mint and Lubuntu iso files and kept Ubuntu 14.04 and added the 12.04 iso both on the same partition.  I didn't think it would work but didn't know what to expect so booting 12.04 and on the Desktop were the install icons for both 12.04 and 14.04.  Tried to boot 14.04 but it failed by freezing at the Ubuntu logo purple screen.  Gave that up.

I then tried 3 partitions, first with the boot directory and 14.04 iso, 2nd with 12.04 iso and the third an ext2 casper-rw partition.  I did this because I wanted to see what happened with installing software.  I booted 14.04 and this time had only the Install Ubuntu 14.04 icon on the Desktop.  I then installed VLC.  I rebooted to 12.04 and again had the Install 12.04 AND Install 14.04 icons on the Desktop.  I created a directory in /home/ubuntu when I was booted to 14.04 and it showed up on 12.04 also.  I opened a terminal and started VLC from 12.04 which I had installed on 14.04.

So if someone wants a persistent flash drive to just save personal data on, a single casper-rw should work.  If they want different software on the different iso, like 12.04 and 14.04 it won't work as anything installed on one will be on the other and I can see a lot of potential for conflict in that.  Using an ext2 filesystem rather than FAT32 for the casper-rw will allow a larger partition.

I've never tried multiple casper-rw partitions but I don't think it would work.  It needs the label casper-rw and I'm not sure you can create two partitions with the same label.
Creating casper-rw files on separate partitions might work.  I spent a little time with that yesterday and didn't have any luck.  If I remember correctly, I could only boot one of the isos.

For someone using a flash drive on the same computer, installed systems should be better.  A Live CD is designed to detect hardware on whichever machine it is booted on which is advantageous if using on multiple machines.

> If it is necessary at all to have more than one system :razz: What would you suggest to provide a pendrive that works in anything from an old 32-bit computer to a new UEFI computer? 		

Knoppix is very easy to use to create a persistent flash drive.  One Ubuntu and one non Ubuntu so you don't have to deal with the multiple casper-rw.  Maybe a Debian variant like LMDE.  I'm not really sure multiple casper-rw files will work.  Googled it yesterday and didn't find anything useful.

---

### Post by sudodus on 2015-01-15
> **sudodus said:**
> Thanks [yancek**[COLOR=#000000], [/COLOR]**]("http://ubuntuforums.org/member.php?u=1928724")... :-P What would you suggest to provide a pendrive that works in anything from an old 32-bit computer to a new UEFI computer?

> **yancek said:**
> ... For someone using a flash drive on the same computer, installed systems should be better.  A Live CD is designed to detect hardware on whichever machine it is booted on which is advantageous if using on multiple machines.

Knoppix is very easy to use to create a persistent flash drive.  One Ubuntu and one non Ubuntu so you don't have to deal with the multiple casper-rw.  Maybe a Debian variant like LMDE.  I'm not really sure multiple casper-rw files will work.  Googled it yesterday and didn't find anything useful.

1. I agree that ***installed systems*** are an alternative, they are portable too, at least without installing proprietary drivers, and in computers where such drivers are not necessary.

2. I think it is a good idea [IMG]http://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG] with a persistent Ubuntu system and a persistent Knoppix system would work in the same pendrive.

In this case I would suggest ***standard Ubuntu desktop 64-bit*** and ***Knoppix 32-bit***. Knoppix is good at recognizing old hardware.

3. Thinking further: In order to extend the pendrive to even older computers, ***Wary Puppy*** or ***TahrPup*** would be a good alternative. They have also their own file for persistence, different from those of Ubuntu and Knoppix.

-o-

Now we are waiting for you *C.S.Cameron*. After hi-jacking your thread for a while it is time for you to get it back :-D

---

### Post by Mike_Walsh on 2015-01-15
Sudodus;

Don't forget the current 'Puppy' release, 'TahrPup' 6.0! We established that it definitely worked with that 'awkward' old graphics card of mine in the 2002 Dell Inspiron 1100...

Regards,

Mike. ;)

BTW; I'll let C.S Cameron have his thread back..!

---

### Post by yancek on 2015-01-15
> Don't forget the current 'Puppy' release, 'TahrPup' 6.0

I put it on a multiboot flash drive last week and I thought it was about the best release of Puppy I've used.  

>  I think it is a good idea :smile: with a persistent Ubuntu system and a persistent Knoppix system would work in the same pendrive.

They will.  I did this about a year ago on separate partitions of a flash drive and both worked as persistent Live CDs.  Actually not with Ubuntu but Peppermint which is derived from Ubuntu so I'm sure most Ubuntus would work.

---

### Post by C.S.Cameron on 2015-01-15
> **yancek said:**
> Your original entry in the first post did not work because you had the UUID on the 'linux' line which is not necessary as the set root line already 
points to it.  You also did not have casper preceding the vmlinuz and initrd lines which is necessary because that is where those files are located.  
I also always have used the "boot=casper" which I think is necessary although I've never tested without it.  This should also work and is just a different
method than the one you got to work above.  When a set root line is used, it always has single quotes.  Might need that with UUID also but I'm not sure as 
I've never used UUID in this type situation.

I'm not sure why you are not able to use the casper-rw on the second partition if it exists.

Thanks Yancek

I keep promising myself I will learn grub 2, probably be about the time grub 5 comes out.

If I disable the casper-rw file on the first partition, the casper-rw file on the second partition takes over.
Similarly, if I make a third partition with an iso file and a casper-rw file and disable the persistent file on the first partition, the one on the second partition takes over, etc, etc.

Edit:
The reason for a persistent install on the EEE internal drive is that it was only a 4GB drive.

---

### Post by sudodus on 2015-01-16
> **Mike_Walsh said:**
> Sudodus;

Don't forget the current 'Puppy' release, 'TahrPup' 6.0! We established that it definitely worked with that 'awkward' old graphics card of mine in the 2002 Dell Inspiron 1100...

Regards,

Mike. ;)

BTW; I'll let C.S Cameron have his thread back..!

That's right :-)

I'll edit my post about Puppy ...

---

### Post by sudodus on 2015-01-16
> **C.S.Cameron said:**
> ...
If I disable the casper-rw file on the first partition, the casper-rw file on the second partition takes over.
Similarly, if I make a third partition with an iso file and a casper-rw file and disable the persistent file on the first partition, the one on the second partition takes over, etc, etc.
...

I suppose this means that we have found no easy way to select casper-rw file (or partition) for persistence automatically - the files must be renamed manually or the partitions re-labeled manually in the previous session. What do you think about using Knoppix or Puppy as the second system with persistence?

---

### Post by sudodus on 2015-07-24
I have found that you can have more than one set of persistence in a casper-rw partition. See [this link](http://ubuntuforums.org/showthread.php?t=2259682&p=13327118#post13327118)

You start with persistence for a released system Lubuntu 14.04.2 LTS.

After that you install one or more daily build flavours of Ubuntu (when this is written it is the version Wily). If you boot Wily with persistence, it will be stored in

```
.../casper-rw/upper
```

and will not interfere with Lubuntu 14.04.2 LTS, which is stored in ```
/casper-rw
```

But the different flavours of Ubuntu Wily will interfere with each other, which is no problem for data files, but if you test both 32-bit and 64-bit versions and install or update program packages, where 32-bit versions are different from 64-bit versions, there can be big problems. So it is a good idea to back up the content of the casper-rw file, for example in a tarball.

---

