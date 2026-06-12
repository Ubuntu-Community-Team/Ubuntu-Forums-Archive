---
title: "Problem..."
date: 2008-01-27
forum: General Help
---

### Post by CorryJm on 2008-01-27
This seems to be a common problem from what I've read thus far.  But nothing I found really helped me specifically.

I installed Linux thinking that it would simply partition my drive and then allow me to choose my OS each time I started my computer... but Linux seems to boot automatically when I start it.

Is Windows lost entirely?

This isn't a problem if I can access my files... where might those be?
I'm entirely new to Linux and can't seem to locate them wherever I look.

I had my important stuff saved to my partitioned D: drive.

---

### Post by yabbadabbadont on 2008-01-28
When you boot and see the Grub prompt, try hitting the Escape key to bring up the Grub menu.  If there isn't an option there to boot windows, it may be that you accidentally chose the wrong option while installing, and overwrote it...  One way to tell, is to look at the list of the partitions on the drive(s) and their types.  In a terminal window run ```
sudo fdisk -l
``` which will list all of the existing partitions.  Please post the output.

---

### Post by CorryJm on 2008-01-28
thanks for the help

here is the result

[IMG]http://i57.photobucket.com/albums/g210/CorryJM/Screenshot.png[/IMG]

---

### Post by Rocket2DMn on 2008-01-28
You don't need to post a screenshot, you can just copy and paste from terminal next time :)
Looks like you overwrote windows, sorry man.  There is no partition with NTFS, just your root partition plus swap.
I hope you have backups of all your data :(

---

### Post by seventhc on 2008-01-28
Did you read the screens during the install??
There is one part that you are supposed to tell it to use the remaining free space, this looks as if you used the entire disk. :(
If you choose remaining free space, it doesn't touch your windows partition and will offer you a choice of which system you want to boot into at start up.
I don't see any ntfs partitions there. :(

---

### Post by CorryJm on 2008-01-28
wow, I messed up.

are all of my files gone as well?
like, actually, really gone?

I had originally chosen this "use free space" option then got some sort of error message, but I made it continue somehow.

thanks for the help guys.
guess I can start over here on Linux now.

---

### Post by Rocket2DMn on 2008-01-28
Yeah, your files are gone for good - there is no way to recover them, that's what happens when you format a drive.  I hope you didn't have anything too important on there.  But, that's a good way to look at it, you can get a fresh start here :)
You can always start with a good backup program too.  I would suggest investing in an external hard drive to keep backups on, nothing fancy.  I use a program called "sbackup" to keep backups of my system - it uses compressed archives and is available in the repositories (through apt-get or Synaptic).
System->Administration->Synaptic Package Manager or
```
sudo apt-get install *programname*
```

---

### Post by CorryJm on 2008-01-28
yeah, there was nothing terribly *essential* in there... just tons of music, pictures, essays, etc... I feel as if I just formated my memories from the last 6 years.

looks like I have a lot of work ahead of me in the realm of downloads.

infinite thank yous to all of you who helped. :)

---

### Post by seventhc on 2008-01-28
If the data was extremely important, there is recovery software, but I don't know of any free one. You'd probably have to install windows and spend a lot of money for the recovery program. There might be some available on linux, but I don't know of any. It doesn't mean they don't exist, I've just never looked into it before. I know they have a forensics linux(something like that) but never used it.

---

### Post by seventhc on 2008-01-28
> **CorryJm said:**
> wow, I messed up.

are all of my files gone as well?
like, actually, really gone?

I had originally chosen this "use free space" option then got some sort of error message, but I made it continue somehow.

thanks for the help guys.
guess I can start over here on Linux now.
I have done something similar before, got an error, proceeded anyway...never again ;) now if I get an error, I cancel and find out why I got the error. saves a headache or two. :D

---

### Post by yabbadabbadont on 2008-01-28
For future reference, imagine Steve Balmer bouncing around like a maniac yelling, "Backups backups backups backups backups..."

Sorry that you lost everything.

---

### Post by CorryJm on 2008-01-28
> **seventhc said:**
> I have done something similar before, got an error, proceeded anyway...never again ;) now if I get an error, I cancel and find out why I got the error. saves a headache or two. :D

haha, yeah.
lesson learned for sure

and seventhc: thanks for the advice, I might look into that. :)

---

