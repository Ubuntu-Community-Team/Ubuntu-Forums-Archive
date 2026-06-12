---
title: "General Help and Clarification over Root, Home, and Other HDD Partitions"
date: 2015-10-01
forum: General Help
---

### Post by baudrillard on 2015-10-01
Hi everyone,
[B]
Before anything else, Clarifications: [/B]

[HR][/HR]1) I have already checked other posts, askubuntu.com, ubuntu.com, etc, for answers, none of which gave me a clear answers to the various questions I have. Sorry if what I am asking is redundant or abundantly obvious, I just want to be 100% certain and understand the technical aspects of what is to follow below.

2) system details:
Dual boot, Ubuntu 14.04 LTS and Windows 8.1, uses GRUB 2 with Ubuntu as the main installation

Root and home are on the same partition, 20GB
Swap, 32GB (I am still relatively new to linux and I took the x2 RAM rule quite literally, unfortunately)
General HDD partition for Ubuntu, ~150GB

The roughly ~700GB remaining of HDD is all allocated to Windows 8.1

All partitions are in sequence (wrong term?), as in partition 1 is Grub2, partition 2 is root/home, partition 3 is the 150GB HDD partition, and so forth.

3)system uses:

I am a computer science and economics double major, so I do a lot of work with programming on both sides. I believe I managed to fill up my root partition so quickly because of the various IDEs I had installed, like IntelliJ, PyCharm, WebStorm, Eclipse, DrJava (I have to use certain IDEs for different classes, just to clarify the redundancies), RubyMine, WolframAlpha, Stata, and more. I had installed most of these in my public folder. Also, I use spideroak, which puts its main sync file in home as well, taking up around 2GB of space minimum (I know how to fix this now, however)
[HR][/HR][B]Begin Post 

Context:[/B]
So long story short, I got a warning that I was running low on Root space. I was relatively surprised, since I repeatedly read on installation tutorials/guides that I would never come close to filling the 20GB of directory space given to Root/Home. However, upon looking/reflecting more seriously into the matter, I realized that I was completely stupid to honestly believe that I would be able to install every software platform I use in the 20GB partition I created. Somewhere along the lines, I completely forgot to use the 150GB partition I created, and in all honestly, I'm not sure how to use it.
[B]
Main Questions[/B]
What I mean is this: will I be able to still have the same functionality of ubuntu's launch system, through whatever desktop client I'm using (GNOME, UNITY, KDE), if I begin installing stuff in the 150GB partition? Isn't the whole point of Home is that the hierarchy behind it allows ubuntu to efficiently integrate software for the purposes of updating, installing, launching it, etc?

If so, how would I go about combining the current Root/Home partition with the ~150GB partition immediately next to it on my HDD? 

If not, is there anything I should be aware of when installing most of my software on the 150GB partition? Am I going to have to manually create launch icons for each software I install? How do I configure programs to save all settings and other data in the partition locally, and not in Root/Home?

For instance, I do not even know how I would install chromium, from the software system, onto the separate partition instead of Root/Home. Most of programs obviously have caches, .config files, and other back end data that gets stored in Root/Home, and I don't know how to change that by default over to the 150GB partition.

**One other thing[Possible answer?]**
There is a single file in the 150GB partition named <MyUserName> that seems to direct me back into Root under the following file path: System/media/<MyUserName>/<LongStringofCharacters>/<MyUserName>/

The only contents of that file is another file called Examples, and it contains a Ubuntu Promo video and a random song. Is this some kind of file mechanism that integrates the separate 150GB partition into the Root directory for storage purposes? If so, then all of my confusion and stress may be completely unfounded. I may have my the solution to my question right here, but the problem is I just don't know enough about how Ubuntu works.

**Closing Thoughts:**

I'm sorry if this is in anyway incoherent, I am honestly just confused. I clearly just did not understand how the Root/Home partition was supposed to function, and now I am just trying to do damage control. I installed Ubuntu this way because of the tutorial I used, which I can no longer find.

 I managed to clean out about 5GB of files (old kernals, deb files, trash in Root, and I deleted the IDEs I'm not immediately using), so I am no longer immediately concerned about running out of space, but I am interested in trying to maintain my current Ubuntu install since it was such a pain getting it to work on my laptop (driver incompatibilities were a major hurdle for this specific PC).

**THANK YOU FOR ANY HELP AND CLARIFICATION.**

---

### Post by sudodus on 2015-10-01
> **baudrillard said:**
> ...
**Main Questions**
What I mean is this: will I be able to still have the same functionality of ubuntu's launch system, through whatever desktop client I'm using (GNOME, UNITY, KDE), if I begin installing stuff in the 150GB partition? Isn't the whole point of Home is that the hierarchy behind it allows ubuntu to efficiently integrate software for the purposes of updating, installing, launching it, etc?

It makes things complicated to start installing programs to non-standard locations. Please avoid that! Home is for settings and tweaks plus your personal files (unless you have a separate **data** partition). I have a separate data partition, and it keeps the system rather neat. I have home as a directory in the root partition.
> 
If so, how would I go about combining the current Root/Home partition with the ~150GB partition immediately next to it on my HDD? 

You can use ***gparted*** to edit the linux partitions. Do not move the head end (left edge) of the root partition - it will not be found unless you reinstall the bootloader. Otherwise you can resize and move partitions. ***But it is risky, and you should make a full backup ***(for example a cloned copy or image with Clonezilla) before doing things like this.
> 
If not, is there anything I should be aware of when installing most of my software on the 150GB partition? Am I going to have to manually create launch icons for each software I install? How do I configure programs to save all settings and other data in the partition locally, and not in Root/Home?

For instance, I do not even know how I would install chromium, from the software system, onto the separate partition instead of Root/Home. Most of programs obviously have caches, .config files, and other back end data that gets stored in Root/Home, and I don't know how to change that by default over to the 150GB partition.

**One other thing[Possible answer?]**
There is a single file in the 150GB partition named <MyUserName> that seems to direct me back into Root under the following file path: System/media/<MyUserName>/<LongStringofCharacters>/<MyUserName>/

I don't think this file is particularly important.
> 
The only contents of that file is another file called Examples, and it contains a Ubuntu Promo video and a random song. Is this some kind of file mechanism that integrates the separate 150GB partition into the Root directory for storage purposes? If so, then all of my confusion and stress may be completely unfounded. I may have my the solution to my question right here, but the problem is I just don't know enough about how Ubuntu works.

**Closing Thoughts:**

I'm sorry if this is in anyway incoherent, I am honestly just confused. I clearly just did not understand how the Root/Home partition was supposed to function, and now I am just trying to do damage control. I installed Ubuntu this way because of the tutorial I used, which I can no longer find.

 I managed to clean out about 5GB of files (old kernals, deb files, trash in Root, and I deleted the IDEs I'm not immediately using), so I am no longer immediately concerned about running out of space, but I am interested in trying to maintain my current Ubuntu install since it was such a pain getting it to work on my laptop (driver incompatibilities were a major hurdle for this specific PC).

**THANK YOU FOR ANY HELP AND CLARIFICATION.**

Maybe the following is the easiest way to get what you want (but you need another drive that is big enough).

- Start by cloning Windows to the new drive.

- Shrink the Windows partition (from within Windows), and leave unallocated drive space.

- Use gparted and create a partition table with what you now know is optimal sizes for the partitions.

- It is possible to use ***rsync*** and copy the whole directory tree of your current linux partitions to fresh partitions in a new drive. 

- In addition to that you need to ***install the bootloader***, and then you have moved the system into a new drive with better sizes for your way of using the system.

---

### Post by baudrillard on 2015-10-03
Alright, sorry for the jambled post. I was attempting some recovery stuff at 2 AM and I needed some clarification. What I gleaned from the experience was this:

1. I created some sort of additional memory partition for Ubuntu, and beyond / and swap space, had no other partitions for my Ubuntu install.
2. This system worked perfectly fine, but (for some reason), the memory partition could be accessed via a file in media. The file name was the actual 'name' (a long string of various characters) for the memory partition. This confused me, but it seems to have no influence on the actual functionality of the partition.
3. Regardless of everything above, I ended up crashing my install when I attempted to cleanout some old kernals in /. I resinstalled Ubuntu, but this time I made / and home separate, giving home all the original drive space that was in the memory partition I created previously.

---

### Post by yancek on 2015-10-03
Additional partitions on a hard drive are generally accessed under the /media/username directory.  This is the mount point.  The long string of characters is the Universally Unique Identifier, generally referred to as UUID.  It is equivalent to the device name in general terms.   You can find this information using the blkid command, example below for /dev/sda5 with the UUID following in quotes.  Generally either will work in most cases, the UUID better if you are using an external drive and booting and accessing it from different computers.  The example below shows the UUID for sda5 which would be the first logical partition on the first drive. 

> /dev/sda5: UUID="47891df9-aa27-4df9-99ac-aa96276780ac" TYPE="ext4" PTTYPE="dos" PARTUUID="1549f232-05"

I'm not sure what you are referring to by "memory partition", maybe just another partition besides the root filesystem?

---

### Post by sudodus on 2015-10-04
Is your problem solved now, or do you need any help?

---

