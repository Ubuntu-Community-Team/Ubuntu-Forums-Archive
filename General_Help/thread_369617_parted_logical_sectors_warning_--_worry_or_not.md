---
title: "parted logical sectors warning -- worry or not??"
date: 2007-02-24
forum: General Help
---

### Post by Dave / Mosaic on 2007-02-24
I have a brand new Seagate 120 GB disk (model ST3120814A if that matters) that I am trying to partition with parted.

Parted (booting on the Live CD) is not completely sure if she is happy:

> ubuntu@ubuntu:~$ sudo parted /dev/hdc
> Warning: Device /dev/hdc has multiple (0) logical sectors per physical sector.
> GNU Parted supports this EXPERIMENTALLY for some special disk label/file system
> combinations, e.g. GPT and ext2/3.
> Please consult the web site for up-to-date information.
> Ignore/Cancel?
> GNU Parted 1.7.1
> Using /dev/hdc
> Welcome to GNU Parted! Type 'help' to view a list of commands.

I can't find any discussion of this warning anywhere, on the suggested GNU web site, on SourceForge, on these forums, or on forums like debian's, or on the internet for that matter, which I think is strange...

Do I need to worry about this?  Parted seems to work OK on this disk, but I'm wondering if I'm doing something wrong; also it's weird that the "multiple" number (quoted above) is zero.

Thanks--

--dave

---

### Post by Dave / Mosaic on 2007-02-26
Just a bump, to see if anybody during the week has any ideas about this...

---

### Post by Dave / Mosaic on 2007-03-01
Okay,,,  sorry to keep bugging everybody; I just thought I'd try this one last time, in the daytime during the week,,,

Wondering, if anybody else has seen this same "Warning: Device /dev/hdc has multiple (0) logical sectors per physical sector." from parted.

thanks...

---

### Post by jesser on 2007-04-07
Hi

I'm getting this same warning:

      Device /tmp/hde has multiple (0) logical sectors per physical sector.

This is while trying to install Ubuntu 6.10 Server on a PPC machine - an Apple XServe - with 4 x 500GB disks installed. 

I get the same error on Fedora Core 6 installation as well. However Fedora seems to keep going, whereas Ubunto fails to partition the disk properly and so fails to install anything. 

Jesse

---

### Post by Dave / Mosaic on 2007-04-07
jesser--

You know, I had something a little different happening here than you do...  for me, I got the warning, but when I proceeded anyway, everything partitioned without apparent problems and ever since then seems to work fine.  I've got a pretty complicated partitioning scheme on my G3 machine here, with multiple OSs and some shared partitions, and I've not had any problems...

I never did hear anything about this from anybody else on this list, which I think is kind of strange; I'm sure others have run into it.  I had also tried to find reference to this warning on the GNU parted web site, but no mention of it.  I can find where the warning gets generated in the parted source code...  but no reasons to cause me concern...

I think it's not surprising that you would get the same warning happening with Fedora but with possible different results; maybe just a different revision of parted?  If you really wanted Ubuntu, I bet you could use the parted on your Fedora installer CD to create your partitions, and then erase and install onto them using the Ubuntu CD...  Or maybe get a Feisty live CD to do your partitioning with...

--dave

---

### Post by jesser on 2007-04-08
Dave

Yeah, I think it must be a warning when parted finds a GPT partition table. Good to know at least one other person in the world has recieved this warning!

Cheers
Jesse

---

### Post by meowsus on 2007-11-07
I just sat down to install Xubuntu Gusty on my wifes computer (when she's at work, *snicker*) and got this same error message. I went gung-ho, threw caution to the wind, and ignored all of its kind (and very mysterious) warnings.

I always try Guided partitioning with LVM, but this time it kept nagging me and nagging me and finally gave me a very strange error (wish i wrote it down), i quickly aborted and just used regular old Guided partitioning and its currently installing the base system.

I think i'll be in good shape if i can keep my stupid cat off the keyboard while i'm trying to install. I'll keep you guys updated if anything goes awry, but it seems like everything smooth sailing. Until the wife gets home. Ruh roah.

---

