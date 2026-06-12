---
title: "old dying hard drive transfer to new hard drive"
date: 2015-04-25
forum: General Help
---

### Post by wog on 2015-04-25
I suspect this'll be an easy question for someone. I'm not a total beginner, but I lost all my notes on how to do things in Linux, and I need help again. 

I have an old (small) hard drive that's finally starting to make noise, but has 14.04 and all my files on it.
I have a new hard drive I've already plugged in, and went after it with gparted. So it's ready to go.
I *was* going to boot off a thumb drive and have my personal files on the hard drive, but this machine is too old to boot from a thumb drive, so I can just scratch that idea off the list.

I can't remember if there's an easy way to move or copy the entire contents of the old drive to the new one, as in Ghost from the Windows environment. Does anyone know how to do that? Or is there a way to install Linux from one hard drive to another, and then just copy the personal files over? I'd install from the thumb drive, but as I said, this machine won't recognize a thumb drive before there's an OS in place.

---

### Post by yancek on 2015-04-25
Can't you put Ubuntu on a DVD, boot that and install to the new drive and then copy your personal files?
If you have an Ubuntu iso downloaded to your old drive, you can boot it from the old drive and install to the new drive and then copy the personal files.  You would need an appropriate entry in the grub.cfg file to do that, an example below.  You would need to change the set root= line to show the drive/partition on which the iso file resides.  The iso would need to be in the root of the filesystem partition and you would need the exact name of the iso file.   

> menuentry "UBUNTU 14.04" {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos3' 
        loopback loop (hd1,msdos3)/ubuntu-14.04.2-desktop-i386.iso
        linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/ubuntu-14.04.2-desktop-i386.iso
        initrd (loop)/casper/initrd.lz
}

---

### Post by RobGoss on 2015-04-25
Are trying to clone your old drive? If so I was advise to use this tools for such matters [https://youtu.be/Rujl5QkNLqo](https://youtu.be/Rujl5QkNLqo) I haven't use it yet but it looks great for situations like this.

---

### Post by HereInOz on 2015-04-25
If you install Ubuntu as a fresh install on the new hard drive, use the "Something else" option when it comes to partitioning, and set up partitions for root "/"  about 32GB, /home; almost the rest, and swap about 8GB, you can then put the old drive in a USB cradle and copy all your /home files over to the new /home directory.  Do this before you run any programs on the new install, and make sure that you get all the hidden files; CTRL-H; and most of your old system will be there for you.  

You will still have to set up printers and wireless networks, and install the software which you had installed on the old machine, but this is the best option to give you a shiny new system which addresses your old data.

By having the separate partition for /home, you can then do a clean install of a new version on the same disk without losing your data (just don't format the /home partition when you do so).

---

### Post by highspider on 2015-04-26
this is very advanced for a beginner and might be too much for you; but, this is how I would clone the drive

I would just boot from the live cd and clone the disk with the dd command. 
so boot from the live cd and do the try ubuntu. 
(so you **DON'T** have a mounted file system to work with).

open a terminal **CTRL+ALT+T**

type this in the terminal to open disk manager 
```
**gnome-disks**
```
note what your disk are called most likely /dev/sda and /dev/sdb.
  click on the disk to the left and look the right of screen to see the /dev/xxx name 
 unmount them if any partitions are mounted 
(click partition) on the right of screen 
then click the gear looking icon next to plus sing below the partion and unmount them all!
then exit gnome-disk (close the window) 

And then back at the your terminal window use the dd command
make sure you have the correct drive for if=/dev/xxX of=/dev/xxX as below is for
From physical disk /dev/sda to physical disk /dev/sdb
```

**dd** if=/dev/sda of=/dev/sdb bs=32M conv=noerror,sync

```

or change bs= to something smaller which will slow down the transfer rate but I don't know how fast your old can read or new drive can write

```

**dd** if=/dev/sda of=/dev/sdb bs=128K conv=noerror,sync

```

this will take awhile don't worry about it not displaying anything in your terminal thats normal and DONT close the that terminal 
progress it display on its own when finished

when its all done you have a perfect clone of your old drive so you can shut-down and remove you old hard drive.
reboot check that its working.

if you have know its current progress before dd is done then you can

open an _**NEW!**_ terminal **CTR+ALT+T **and type in the NEW terminal
```

**pgrep **-l '^dd$'

```
should display something like this
9872 dd

except 9872 will be something different on your pc change number
then type ```

**kill **-USR1  9872

```

now if you look on your other terminal where type the dd it will show how much it has progressed
you can repeat the above kill if you want to see progress again  

I would then boot back up off the live cd and run gparted to change any partition sizes around

here some more explanation on my post
[https://wiki.archlinux.org/index.php/Disk_cloning](https://wiki.archlinux.org/index.php/Disk_cloning)
[http://unix.stackexchange.com/questions/144172/full-dd-copy-from-hdd-to-hdd](http://unix.stackexchange.com/questions/144172/full-dd-copy-from-hdd-to-hdd)
[http://linuxcommando.blogspot.com/2008/06/show-progress-during-dd-copy.html](http://linuxcommando.blogspot.com/2008/06/show-progress-during-dd-copy.html)

---

### Post by wog on 2015-04-28
Okay. For the sake of closure.
I will be studying these responses to learn from them, btw.
I swear I took my meds today.

I have two machines, side by side. The Windows machine is a bottom-of-the-line Dell, which, when I tried to burn a LiveCD of Lubuntu 14.04, complained about every single disc I gave it. So I couldn't burn a DVD on that one.
The other machine is older, and refused to boot from a 32 gig thumb drive I expected to run Ubuntu from, leaving the hard drive for my personal files. Rats.

My first plan was to find the most up-to-date version of Ubuntu I had on disc and install that to the new hard drive, download the new version and burn it to DVD (since that machine would likely use the media I had on hand), and then re-install the new version over the old version. Comedy gold. I swear I took my meds this morning.
I was looking for a 64-bit version of Ubuntu, but what I found was one copy of 11.10, but 32-bit, and the other two discs didn't say. I pessimistically assumed that meant they were 32-bit, reinforcing the idea that I would need to re-install the 64-bit version over whatever I could install on the new hard drive. One of the unmarked discs was 11.04, so I went with that.
When I tried to install, it got up to almost 50% and then the animations froze. I assumed the system crashed, and rebooted.
I did this with the other unmarked disc, which was listed as 10.04LTS. Same thing happened.
Finally, I realized there was another way.
I put in the old drive with the current version of Lubuntu and booted from that. Then I transferred the unburned disc image from the Windows machine to the Linux box using a thumb drive, and burned it using one of the discs the Windows machine swore was incompatible. Then I shut down the Linux box, switched to the empty new hard drive and booted off the DVD and installed directly. All went well, and I even updated to 15.04. All done.
I suspect I'll use the intended thumb drive to keep my personal files on until I can buy another hard drive to take its place.

yancek, I have no idea what that code snippet means or how to use it. It sort of looks like C, but I can't be sure.

robert159, I followed the link, but couldn't find any instructions about how to get it or use it. It kinda looked like a kickstarter video. 

HereInOz, good advice. If the above hadn't worked, I'd have been tempted to go this route. I *think* I have the skills to do it with gparted, but I'm not really sure. If nothing else, it would have made a good experiment. I really like that tagline. :)

highspider, I'm going to have to study your answer a bit longer. I've never used dd before, but I really do appreciate the three-finger commands being spelled out and the command line entries given. I will be checking out the links and keeping notes. A very useful post!

From here, I have a SATA to USB cable to copy the files from the old hard drive and I'm good.
Thank you, everyone, for your help and suggestions.

---

### Post by kunitoki2 on 2015-04-28
yancek described how to boot a machine with an iso file
which is by the way a cool way to ensure your system boots into the same state every time
we all download isos and use them to create bootable sticks for example
but you can also just copy the single iso file onto your hard drive and enable grub to use this iso to boot your system
grub just needs some information (where is the iso and where are some files inside the iso) and that's what his snippet is for
the crub.cfg inside the boot folder is just a text file and you have to add some lines in order to 'activate' the iso boot method
yancek just provided a code example you can use if you want to boot from an iso file
booting isos is nice sometimes, for example if you teach a class full of young students who like to mess up installations
just shut down and boot again because the iso doesn't change

---

### Post by wog on 2015-04-29
So, if grub boots using the iso file and this snippet, that means grub needs to be installed, right? Or does that snippet tell the system how to use the iso without actually installing Ubuntu?

Is that snippet placed in the root directory of the hard drive as a text file, or is there another step? Does the file need to have a certain name or file extension? I really am completely baffled about how to use that snippet. 

Okay, I re-read what you wrote. This is how I envision your instructions:
1. Make a directory called 'boot'.
2. Put yancek's snippet in a text file in the boot directory and name it 'grub.cfg'. No editing will be needed.
3. Put the iso file in the root directory.
4. Reboot and enjoy linux when it automagically boots up.

Is this correct?

---

### Post by kunitoki2 on 2015-04-29
Sorry my post wasn't really clear and exact - I was in a hurry and also english is not my first language :)
Yes, grub needs to be installed.
Grub stores some text files in different folders (boot for example) which can be edited with a simple text editor to enhance grub's capabilities.
I found a nice page about the whole grub iso topic:
[http://www.howtogeek.com/196933/how-to-boot-linux-iso-images-directly-from-your-hard-drive](http://www.howtogeek.com/196933/how-to-boot-linux-iso-images-directly-from-your-hard-drive)
Hope this helps - I already played with grub and some isos and it works great.
I think I will use this method in school so the students can't mess up the systems anymore since the isos become the system's boot source and there's no need to install an OS anymore which can be ruined.

---

### Post by highspider on 2015-05-01
O-my bad,

I thought you had both hard drives in the "same" computer and just wanted to clone the drive of the crappy one to a new one.

[stolen from wiki] [http://en.wikipedia.org/wiki/Dd_%28Unix%29](http://en.wikipedia.org/wiki/Dd_%28Unix%29)
**dd is a [command-line]("http://en.wikipedia.org/wiki/Command-line") utility for [Unix]("http://en.wikipedia.org/wiki/Unix") and [Unix-like]("http://en.wikipedia.org/wiki/Unix-like") [operating systems]("http://en.wikipedia.org/wiki/Operating_system") whose primary purpose is to convert and copy file**

---

