---
title: "Retrieving Data from Corrupted NTFS Partion"
date: 2007-01-25
forum: General Help
---

### Post by Goober on 2007-01-25
Hello fellow Ubuntans!

I posted a thread about retrieving data from an ext3 drive using Windows, but now my situation has reversed - Windows decided to become corrupted, such that I can no longer access it.  Some beginning info: I have a 160 gig Hard drive, with a corrupted Windows installation, with 2 partitions, on 2/3 of it, and the other 1/3 as a Edgy partition.  I am presently in Edgy (and loving it!), and trying to retrieve some important files that are stuck on the corrupted 2/3 of my Hard drive that is partitioned as NTFS.

Edgy does not recognize those 2 NTFS partitions, in fact, it shows it as "unallocated space" in gparted, which suggests that it is corrupted.  I can't mount the NTFS partitions.  What I am looking for is a program that I can use to try and recover files off the NTFS partitions.  I've tried looking for a program, but have come up empty handed thus far.  If anybody knows of such a program, or of another way to retrieve those files (Such as using the Windows XP CD?) I would really, really appreciate it!

Thank you very much in advance!!!

---

### Post by bodhi.zazen on 2007-01-25
See if test disk can help: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by Goober on 2007-01-25
Hello,

I successfully managed to download TestDisk, and it looks like a very viable solution.  Unfortunately, I am not sure how to install it.  It has been a long time since I last used the Terminals, and I have forgotten how to go between folders.  I know how to install it, once I navigate to the right folder using the Terminal, but I forgot how to do that.  

Is there a thread with instructions of how to navigate using the Terminal?

Thank you very much for the suggestion.

---

### Post by Happy_Man on 2007-01-25
Well...

```
cd <source dir> <target dir>
```

usually does it... :D

---

### Post by bodhi.zazen on 2007-01-25
You run test disk as a live CD. It is on the Gparted Linve CD

Gparted Live CD : 

Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)

	Download: [Download Gparted](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)


Basic CLI tools : [http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

Test disk wiki: [Test Disk wiki](http://www.cgsecurity.org/wiki/TestDisk)

HTH

Post if you have a specific question.

---

### Post by Goober on 2007-01-25
Ok, I understand how testdisk is supposed to work, I read through that wiki, I just don't know how to install it in Edgy.  If I do the LiveCD, will that allow me to "fix" the boot record for Windows so I can then log into Edgy, and save my files?  Or will that allow me to log into Windows, and directly save my files?

If I am not making sense please let me know.  Thanks for the continued assistance.

---

### Post by bigken on 2007-01-25
I would try and the [ubd4win]("http://www.ubcd4win.com/") and see if you can restore the registry or get the data :wink:

---

### Post by bodhi.zazen on 2007-01-25
Hard to know for sure but I do not see why Test disk would be different if you run it from a live CD or from Edgy.

As far as data transfer/copy, you can do that either from the gparted CD or once you repair the partition boot to windows or edgy ...

If you use the gparted CD, you will need to manually mount the partitions.

Gparted will not allow you to do this with /mnt or /media, but you can in /tmp

Thus:

```
mkdir /tmp/windows
mount /dev/hda1 /tmp/windows

mkdir /tmp/edgy
mount /dev/hda3 /tmp/edgy

cp /tmp/windows/file_to_copy /tmp/edgy/home/user_name
```

Or you can use Thunar if you prefer a gui.

---

### Post by Goober on 2007-01-25
> **bigken said:**
> I would try and the [ubd4win]("http://www.ubcd4win.com/") and see if you can restore the registry or get the data :wink:

Hello,

Thank you very much for providing this link, it doesn't look like it will work, however.  All the mirror sites show a .exe file, which, upon further reading, you use to install in Windows to create a .iso file along with your WinXP CD.  I am currently in Linux, with Windows not working period, so I can't execute the .exe files, and thusly cannot create the .iso file.  If they had the .iso file downloadable, then I could easily make the LiveCD, and it might work, but I can't even do that in Linux.  Thanks again, but that option doesn't look like it will work.

From the FAQ ... 

"Why isn't UBCD4Win available completed in ISO format?

Simply, copyright laws. In order to create the UBCD4Win boot disc, XP files are pulled from your XP CD. That is how the project boots into a mini "XP" environment. If we made the ISO available MS would shut the site down and probably sue me. "

Just as a general comment, then problem with the internet today is there is simply too much information!  I have been googling, and looking at various sites, and, well, it is difficult to determine which option would work, and which wouldn't.  Ahh well, I guess I must simply continue searching ...

---

### Post by Goober on 2007-01-25
> **bodhi.zazen said:**
> Hard to know for sure but I do not see why Test disk would be different if you run it from a live CD or from Edgy.

As far as data transfer/copy, you can do that either from the gparted CD or once you repair the partition boot to windows or edgy ...

If you use the gparted CD, you will need to manually mount the partitions.

Gparted will not allow you to do this with /mnt or /media, but you can in /tmp

Thus:

```
mkdir /tmp/windows
mount /dev/hda1 /tmp/windows

mkdir /tmp/edgy
mount /dev/hda3 /tmp/edgy

cp /tmp/windows/file_to_copy /tmp/edgy/home/user_name
```

Or you can use Thunar if you prefer a gui.

Firstly, let me say I really appreciate the help you are giving me.  

Now, one small issue I see with this plan is that gparted (and thus Edgy) does not recognize the  Windows partitions that I know I have on this hard drive.  It is recognizes as "unallocated space", not /dev/hda3.  So I think I need to make it a recognized partition first.  If I do this, however (By selecting the space in gparted, Partition -> New -> Filesystem: unformatted), will that allow Edgy to mount it, as you say above?  or will that make matters worse?

---

### Post by bodhi.zazen on 2007-01-25
> **Goober said:**
> Firstly, let me say I really appreciate the help you are giving me.  

Now, one small issue I see with this plan is that gparted (and thus Edgy) does not recognize the  Windows partitions that I know I have on this hard drive.  It is recognizes as "unallocated space", not /dev/hda3.  So I think I need to make it a recognized partition first.  If I do this, however (By selecting the space in gparted, Partition -> New -> Filesystem: unformatted), will that allow Edgy to mount it, as you say above?  or will that make matters worse?

I think you should try to use test disk to repair the partition or recover the data rather then trying to mount it (before it is repaired).

I am afraid if you try to mount the partition or format it you will lose more data.

---

### Post by Goober on 2007-01-25
Just to report in, I have successfully managed to install testdisk (Apparently it was on the repositories, I did it through Synaptic!), and I ran it, and gparted now recognizes one of my 2 missing partitions!  I am going to attempt to mount it, and see if I can get back the files I want to save on there.  

I will report back if I have any problems, but I think my problems might be solved!!!  Thank you all very much!!!

---

### Post by Goober on 2007-01-25
Ok, I have yet another small problem I have enountered.  Following the directions that bodhi.zazen gave me on the other page, I did this:

mkdir /tmp/windows
sudo mount /dev/hda3 /tmp/windows

Which allowed me to successfully mount the partition that I recovered in that folder.  Unfortunately, however, I cannot access the folder, It says that I do not have the proper permissions.  Does anyone know how to get around that?

---

### Post by bodhi.zazen on 2007-01-25
gksudo nautilus

navigate to /tmp/windows :)

---

### Post by Goober on 2007-01-25
Hrm ... Ok, I have never used Nautilus before, in fact, never even heard of it before, so if this seems like it is a stupid question, then it probably is.

Using Nautilus, I copied all the files I wanted to keep off of the Mounted Partition onto new folders I created on my Desktop - all using Nautilus.  After I got everything I wanted, I exited Nautilus, and went to the Desktop.  Except the new folders I saved, and all of the files I put in them, wasn't there.  Are those files only accessible through the root in Nautilus?  Can I make them accessible through the non-root user?  I noticed that if I right-clicked on the folders in Nautilus, and went to Properties, I could change the permissions and such, but I don't really want to mess around with anything at this stage, lol.

---

### Post by bodhi.zazen on 2007-01-25
LOL Nautilus is the name of the program you use when you browse home or computer :p

You can change the permissions and ownership of those files if you wish.

Lets look at the ownership and permissions:

In a terminal:```
cd ~/Desktop
ls -la
```

Post the results ...

And it is possible you saved the files to /root/Desktop ;)

---

### Post by Goober on 2007-01-25
```

total 20
drwxr-xr-x  5 nathangl nathangl 4096 2007-01-25 15:27 .
drwxr-xr-x 31 nathangl nathangl 4096 2007-01-25 15:34 ..
drwxr-xr-x  2 nathangl nathangl 4096 2007-01-25 15:31 Movies
drwxr-xr-x  3 nathangl nathangl 4096 2007-01-25 15:32 Music
drwxr-xr-x  2 nathangl nathangl 4096 2007-01-25 14:31 Nathan's Folder

```

Yes, I have successfully changed the ownership and permission of one file, but there is a LOT of files there, lol.  In Nautilus, I did put them to the /root/Desktop.  Which I thought was the "regular" desktop at the time, not the root one.  I feel like such a newbie ...

---

### Post by bodhi.zazen on 2007-01-25
LOL ;)

I think the easiest thing to do is to gksudo nautilus and copy the files from /root/Desktop to /home/user_name/backup.

I am guessing the permissions will change when you move them to your home folder.

If they do not, in a terminal:

sudo chown -R nathangl:nathangl /home/nathangl/backup/*
sudo chmod -R /home/nathangl/backup/*

---

### Post by Goober on 2007-01-25
Oh, we are getting far, lol ... 

I tried the first method, I couldn't copy mp3 files. As for the second method, the first line worked, the second line game me this: 

```
nathangl@NathanComputer:~$ sudo chmod -R /home/nathangl/backup/*
chmod: missing operand after `/home/nathangl/backup/*'
Try `chmod --help' for more information.
nathangl@NathanComputer:~$ 
```

Any suggestions?  I have figured out that I can manually allow permissions to each and every folder, plus all the files inside of them, but that would be a lengthy process, to say the least.

---

### Post by bodhi.zazen on 2007-01-25
> **Goober said:**
> Oh, we are getting far, lol ... 

I tried the first method, I couldn't copy mp3 files. As for the second method, the first line worked, the second line game me this: 

```
nathangl@NathanComputer:~$ sudo chmod -R /home/nathangl/backup/*
chmod: missing operand after `/home/nathangl/backup/*'
Try `chmod --help' for more information.
nathangl@NathanComputer:~$ 
```

Any suggestions?  I have figured out that I can manually allow permissions to each and every folder, plus all the files inside of them, but that would be a lengthy process, to say the least.

Oh sorry, small typo on my part :redface:

sudo chmod -R 755 /home/nathangl/backup/*

---

### Post by Goober on 2007-01-25
I am sorry to say that latest suggestion did not work.

I think I am just going to go through each file and manually change the permission.  It will take me awhile, but it will work.  First I am going to restart so that my sound works ... 

But anyways, thank you so much for all of your help!  I am fairly sure that I know what to do from this point on.  Thanks again!

---

### Post by helliewm on 2007-02-01
How did you get on? Have you manged to retrieve the data? I had a similar problem and discovered through the forum that Bigken ( who has responded to your thread) lived literally just down the road so he very kindly offered to sort the problem for me. I am just curious as it gave me serious headache and Ken was ready to throw the offending PC out the window! 

My problem was caused by my Sister ( it was her machine) not defragging the hard disk and it did not occur to me to do so as I had done a dual boot on my PC with no problems but then I maintain my PC and laptop!

Helen

---

