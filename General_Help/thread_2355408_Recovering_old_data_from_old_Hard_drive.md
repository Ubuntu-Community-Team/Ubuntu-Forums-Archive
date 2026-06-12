---
title: "Recovering old data from old Hard drive"
date: 2017-03-12
forum: General Help
---

### Post by oilyfish on 2017-03-12
I have an Fdisk -L printout of almost 6000 characters I can post
Tell me if you think it'll help.
Or maybe tell me what to look for in it, and how to use that. 
-------------------------
The issue
I had been running an older version of Ubuntu on a hard drive and on it  are data files  that I wish to transfer to a new hard drive  upon which I have installed the most recent version of Ubuntu.
However I can't find the old drive.  
When I open the Ubuntu file manager it  does not show  a 1 TB drive  But then  I don't know what to look for, so there's that. 
I have them both in  drive bays.
 The UFEIBOIS can see them both 

The old version of Ubuntu is still resident on the old drive but the disc was never encrypted. 
There is  a password, but didn't encrypt the disc so access should be no issue except I don't know how.

---

### Post by deadflowr on 2017-03-12
What shows in the sidebar of the file manager?
(Do you see a sidebar in the left side of the file manager?)

---

### Post by oilyfish on 2017-03-12
> **deadflowr said:**
> What shows in the sidebar of the file manager?
(Do you see a sidebar in the left side of the file manager?)
Lets see if this works
The two volumes  displayed appear to be part of the new 3TB drive. I've explored them  quite a bit and there's nothing about them from the old 1TB drive





[IMG]http://i1024.photobucket.com/albums/y302/oilyfish/Home_001_zpsuq1qlrwf.png[/IMG]

---

### Post by deadflowr on 2017-03-12
Look at what Disks tells you 
(it's graphical program that should show you the state of any connected disks or storage devices (usb, et al) 
Just highlight the device in the left sidebar and the layout will show in the main area)

---

### Post by oilyfish on 2017-03-12
> **deadflowr said:**
> 
Just highlight the device in the left sidebar and the layout will show in the main area)

Yah, that's my problem,  the drive that I  am looking for is not there.

Ohh  Wait~!! EDIT>  
I'm stupid
I clicked the little arrow next to them and got the messagethat I could "unplug" the media. So I did it to both and   then popped the drive out and those two volumes disappeared.  Odd how I can't find my files anywhere in them. They should be under directories titled  Documents , Downloads, Pictures, and Videos  and I don't seem to be able to locate them.

---

### Post by deadflowr on 2017-03-12
Maybe a misunderstanding, but I was referring to a program called Disks, which differs from the file manager.
You open that program and then highlight the device from the listing on it's left sidebar.

(unless you meant you did this, in which case, classic miscommunication all around)

---

### Post by oilyfish on 2017-03-12
Disks - - Found it.  Yah it sees the drive. Now I gotta learn how to use the app
 Thanks

Yah nowhere can I find any of my data files. I tried to change the permissions for the volumes and Nautilus was unable to do it.  It seems that I formatted this  drive in windows back when I  started using it and the Ubuntu 12 didn't reformat on installation. SO I'm sort of stuck.

BRAIN FART EDIT>

WHat  if I open that operating system up and make all the files public 
I stumbled onto this
sudo chmod -R a+rwX /var/www
Before doing this I should probably disconnect from the internet. 

Or I could establish public folders and migrate  the files to them and then migrate them to the 3TB disk later 
I dunno  they are ideas.

---

### Post by deadflowr on 2017-03-13
When you highlight the disk you want, it should then show the disks partition scheme layout in the main window.
Here you can click to highlight a partition in that window, and then click on the > play button in the bottom left corner area of the window.
The > play button thingy is the button that should mount the partition. Do not press the - minus button, that one deletes partitions.
If from some reason it refuses to mount, it should show some error message.

When properly mounted in Disks it'll show in the File Managers left sidebar under whatever name it shows as being listed in the mounted at line in Disks.
(You can access it directly by clicking on the Mounted at link; Under the main window area it should show a few lines, the last should show Contents >> stuff (probably ext4 version1.0 and then Mount at with an orange link, clicking the link auto-opens the file manager directly in that mounted location, if that makes sense.)
 
If it's from another Ubuntu install the files for you would most likely be in home >> your username.
> WHat if I open that operating system up and make all the files public 
I stumbled onto this
sudo chmod -R a+rwX /var/www

No, don't do that.

---

### Post by dcsoldschool53 on 2017-03-14
How did you mount your physical hard drives in the machine...is one a master and the other one the slave drive? If you have 2 drive that are masters, I think they won't see each other. Refer to you hard drive manual. Also, you can try inserting a Linux disc, not to install it but to try it. Then, open a file manager to see if it mounts its self.

---

