---
title: "[SOLVED] Wubi tougher than Windows"
date: 2007-09-03
forum: General Help
---

### Post by stevelasvegas on 2007-09-03
I have Ubuntu installed on my laptop; I used WUBI. Everything there is good.
Now I want to put Ubuntu on my desktop. I would really like to do it without the training wheels (WUBI), but maybe later (that looks like it's going to be a REAL headache).
So, I installed WUBI and rebooted into Ubuntu but as far as I can get is a black screen that says;
Booting GRLDR.....
Turning on gate A20... success.
And then it stops, with no disk activity.
Here's the info I think is important.
I sure hope someone can get me past this, I really want Ubuntu running on my desktop.
I would like to have the WUBI folder on K:. K is a SATA drive.
Thanks for any help you can provide.

[IMG]http://farm2.static.flickr.com/1231/1314658197_ad0c52fbf7.jpg?v=0[/IMG]

---

### Post by tuxcantfly on 2007-09-04
Seems like you have a lot of spare partitions there. Maybe you should just make a standard installation of Ubuntu, it will work better and be less problematic (just clear out one of those partitions and let Ubuntu use it); if you don't want to use a CD to install Ubuntu use UNetbootin at [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

---

### Post by stevelasvegas on 2007-09-05
Yeah, if I proceed with Ubuntu on this machine, my Windows desktop,  I will probably try the 'real' install. I can tell you that the WUBI install gives me some comfort in knowing that Windows is isolated. One of the downsides of the WUBI install that I have perceived is that when I want to back up my Ubuntu installation, I have to backup the entire WUBI folder (image) instead of only the files that have changed. I don't know what other 'cons' there are associated with a WUBI install. I want a 'real' installation, but I read so many forum postings that say after installing Ubuntu the 'traditional' way, that they are unable to get back into Windows. If the separate partition isolated my Windows installation, then that would be a good thing. I know of only one file that is changed outside of the WUBI folder; boot.ini. Although, all I have to do is image my Windows partitions and even if there is a problem, I can recover.
In the meantime, I have done a traditional installation of Ubuntu on a different Windows machine, and all went well. It might even be better this way because I can see the Ubuntu machine and my Windows machine by using VNC and Remote Desktop, so I can be on my Windows machine (or any other machine in my network) and work with my Ubuntu machine remotely.
This has been a gradual migration for me. I don't think I could ever completely dump Windows, just because I have worked with Windows for so long, and I enjoy tinkering with the newest apps and utilities. It's a comfort zone thing, and that's important to the people around me (since my attitude is directly influenced by how well my computer 'kingdom' is working). So, I started with Ubuntu installed with WUBI, and now I have installed Ubuntu through the traditional method. Working with Linux is a challenge for me; the learning curve is rather steep.
I appreciate your suggestion.
I do have one more question albeit premature. As I said, I am accessing my newly installed Ubuntu by running remote desktop on Ubuntu, and VNC on my Windows machine. How can I get the remote desktop (Ubuntu) to run 'as a service' (the way I do in Windows), so I can connect to it after it has booted. Now, I have to physically log on to that machine before I can connect.
Thanks again for the help.

---

### Post by stevelasvegas on 2007-09-05
[IMG]http://farm2.static.flickr.com/1040/1331773659_8f2404735d.jpg?v=0[/IMG]
[IMG]http://farm2.static.flickr.com/1382/1332662492_a5734aa107.jpg?v=0[/IMG]

I want to install Ubuntu in the partition Windows refers to as Linux L: but it doesn't seem to be an option during the install using Ubuntu current Live CD.

---

### Post by ago on 2007-09-05
> **stevelasvegas said:**
> [IMG]
I want to install Ubuntu in the partition Windows refers to as Linux L: but it doesn't seem to be an option during the install using Ubuntu current Live CD.

Should be available if you select manual partitioning

---

### Post by stevelasvegas on 2007-09-05
Yeah, I looked at that, but I don't know what I'm seeing and I don't know enough about where to put what and the sizing and all. I was trying for something more automatic.

---

### Post by ago on 2007-09-05
> **stevelasvegas said:**
> Yeah, I looked at that, but I don't know what I'm seeing and I don't know enough about where to put what and the sizing and all. I was trying for something more automatic.

In this case the easiest way is to use windows, delete the Linux partition, then create a partition of 261000MB (do not bother formattaing it), this should leave about 15GB unallocated. Then in Ubuntu select: "Use the largest contiguous free space".

---

### Post by stevelasvegas on 2007-09-05
And it will pick the unallocated space, for sure, not the newly created 261000 MB or any other space?

---

### Post by ago on 2007-09-05
It should pick the largest unallocated space, and you should see some confirmation message anyway

---

### Post by stevelasvegas on 2007-09-05
[IMG]http://farm2.static.flickr.com/1038/1333121186_e7bb964197.jpg?v=0[/IMG]

[IMG]http://farm2.static.flickr.com/1131/1333121176_97cfb22fdd.jpg?v=0[/IMG]

This is what I see, but it gives me no comfort. Does it look right to you?

---

### Post by ago on 2007-09-05
looks good to me

---

### Post by stevelasvegas on 2007-09-05
OK. Here goes nutin' honey.
Next post will be tears of joy or sorrow.
:confused:

---

### Post by stevelasvegas on 2007-09-05
No tears either way yet.
Did I neglect to mention I wanted to dual boot this baby?
The install seemed to go well, but when it didn't ask me to import settings during the install, I figured this puppy is going to be autonomous. The partitioning looks right in Partition Magic. I'm assuming there is a boot.ini edit in my future. Maybe something else?
Here's how it looks now.
[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

---

### Post by stevelasvegas on 2007-09-05
OK, Now I can boot in to either Windows or Ubuntu by selecting the proper Disk in the bios. I am guessing that I could continue this method (not my first choice) or modify the Windows boot.ini (although I don't know what the added information to point to Ubuntu would be) or boot to the Ubuntu Disk and modify the Grub menu (I have no idea how to do that).
Thanks for getting me this far. If you could expedite the above for me, that would be great. Otherwise, I keep tinkering. It's so much more fun when you get to the end in a straight line.
Gotta eat something to regain energy, then, back to it.
Thanks again for getting me here. I will review what we have done so I can better understand it all.
I would call this a tears of joy session.
:)

---

### Post by stevelasvegas on 2007-09-05
I think I would like to boot to my Windows C: drive (it is raid 0) and have the boot.ini display the boot options for Windows or Ubuntu. Doesn't that sound like the right thing to do?
Now, HOW?

**Here is what it looks like in Windows**
[IMG]http://farm2.static.flickr.com/1131/1332780091_796c602e14.jpg?v=0[/IMG]

**and here is what is looks like in Ubuntu**
[IMG]http://farm2.static.flickr.com/1140/1332779997_1415c221ac.jpg?v=0[/IMG]
[IMG]http://farm2.static.flickr.com/1263/1332779921_2be1cd23d6.jpg?v=0[/IMG]

---

### Post by tuxcantfly on 2007-09-05
The way I'd do it is install GRUB to /dev/sda

```
sudo grub-install /dev/sda2
```

Then afterwards, you will be able to boot only Ubuntu. However, if you edit /boot/grub/menu.lst, you will be able to boot Windows as well if you add this to the end of /boot/grub/menu.lst:
```

title           Windows
root            (hd1,0)
savedefault
makeactive
chainloader     +1

```

I'd avoid using boot.ini or any of those other methods, since they keep you tied to Windows (if Windows bootloader screws up, you can't boot Ubuntu either).

---

### Post by stevelasvegas on 2007-09-06
I edited the Grub menu.lst by adding the code to the end of the file:

```
title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

title           Windows
root            (hd1,0)
savedefault
makeactive
chainloader     +1
```

But when I rebooted, it booted directly into Ubuntu. Then I realized that for me to access the Grub menu, I had to press esc during the booting process. When the menu presented itself, I arrowed down to the Windows label and received an error like "disk read error occurred - ctrl+alt+del to reboot."

Sorry I wasn't clear. Ultimately I want to be presented with a menu that will allow me to choose which o/s I want *without* any user input. So the computer boots into the menu and that Windows be the default o/s which it will automatically select after X seconds.

The reason I need this functionality, is that I leave my computer off and I access it remotely by powering it up using wake on lan. So it has to go from power up to Windows login screen all by itself.

Although I would like to know the correction necessary for the menu.lst edit that I did and what I should change to make it work (as a learning experience).

Hey, thanks for all the time you have spent getting me through this. It's people like you that make this a great community. I can only hope that I can gain enough knowledge to be able to lend assistance to others.

I hope you will continue with me on this, I think we are very close.

---

### Post by stevelasvegas on 2007-09-06
I neglected to say that I only did part 2 of your instructions. I didn't do part 1 because Grub was already installed.

---

### Post by minhmeoke on 2007-09-07
> Ultimately I want to be presented with a menu that will allow me to choose which o/s I want without any user input. So the computer boots into the menu and that Windows be the default o/s which it will automatically select after X seconds.

To do this, you will have to edit grub's menu.lst file. Open up a terminal, and type in:
```
gksudo gedit /boot/grub/menu.lst
```

Change the timeout value to a value greater than zero (in this example it is 3 seconds):
```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		**3**
```

Then find the following section at the beginning of the file, and set the default number to the position where your windows entry is:
```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		**0**
```

See [http://ubuntuforums.org/showthread.php?t=26988]("http://ubuntuforums.org/showthread.php?t=26988") for an example.

---

### Post by stevelasvegas on 2007-09-07
Yeah, I get the display part. The part I don't understand this part:
# title        Windows 95/98/NT/2000
***# root        (hd0,0)*** <---- This part
# makeactive
# chainloader    +1
# 

What information can I give you (other than the images above) that will tell us what to put here so it will find the Disk(s) (my C: drive in windows consists of 2 physical hard drives ~74 GB each, raided 0) and boot Windows?

---

### Post by confused57 on 2007-09-07
You need mapping lines to boot Windows on a 2nd hard drive:
```
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

I have seen other users able to boot Windows set up on Raid from a non-raid Ubuntu drive.

You can place your Windows entry above the ###BEGIN AUTOMAGIC KERNELS LIST for Windows to boot as default, as described here:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

---

### Post by stevelasvegas on 2007-09-07
I followed Confused instructions:
You need mapping lines to boot Windows on a 2nd hard drive:
Code:

title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

And now I am presented with a Grub menu that includes Windows XP.
It actually boots into Windows XP and it also boots into Ubuntu when I select that. I think we've done it Ole!
Now I can massage Grub to delay and display and select the default OS.
Could this possibly be the end of the thread or is there something else I need to be aware of. Either way, for me this is the beginning of learning WHY this worked.

I will post this in the other thread where this all began.
Thanks, all of you for all of your time and efforts.
Especially Confused57 - hip hip hooray!
I think we all win if we follow the path I have taken and learn all we can from this well participated project.
Again, thank you all so very much. I hope I am able to gain knowledge and in the future help someone else realize the great feeling it is to work with such an excellent community.

---

