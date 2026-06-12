---
title: "Fixing Windows with Ubuntu"
date: 2007-06-15
forum: General Help
---

### Post by sdrawkcab on 2007-06-15
So my friend got a trojan with Windows, and pretty much ran it to death after that. So not wanting them to pay outrageous prices at the Computer place, I offered to try and fix it.

Well, I finally got the Ubuntu Live CD to boot up, but I couldn't seem to get my external drive with my Ubuntu desktop on it to boot for some reason.

Anyway, I was wondering if there is 

1.) Is there anyway to retrieve the documents from the ruptured internal drive with the Live CD?

2.) Is it possible to fix this computer with the Live CD?

I actually belong in the beginner section, but I thought that this question was maybe a little more advanced/general...

Any in-depth help would be so very VERY appreciated!

---

### Post by hardyn on 2007-06-15
1) yup
2) probably not

boot the live disk.

then create a directory in /media
$mkdir /media/windowsc

mount the windows partition
$sudo mount /dev/sda1 /media/windowsc
use sda1,2,3...n for the different drive partitions C,: D:, E:, n:

if everything worked according to plan, your windows partition should have appeard on the desktop... extract files as required.  when completed, unmount, reboot, and reinstall windows.  (reinstalling is sometimes easier than trying to fix it)
$sudo umount /media/windowsc

hope this helps.

(i know this has been posed before)

---

### Post by sdrawkcab on 2007-06-15
I'm sorry, but I typed in what you wrote there to the terminal and it told me that "/media/windowsc" does not exist. Now I know that I'm trying to make that directory, but I'm not sure why it won't work.

I also tried dropping the "$" just to see what would happen, but it said I didn't have permission.

Probably something really obvious, but those always seem to be the harder things for me.

---

### Post by hardyn on 2007-06-15
the '$' is just your prompt, your correct to ignore it.

no /media/windowsc does not exist, you are having to create it.
and my fault, you do need to use sudo,

sudo mkdir /media/windowsc

---

### Post by merlinus on 2007-06-15
sudo mkdir /media/windowsc

-merlin

---

### Post by sdrawkcab on 2007-06-15
Ok, so on the command of mounting I wrote > sudo mount /dev/C:/media/windowsc

It returned an error saying > mount: can't find /dev/C:/media/windowsc in /etc/fstab or /etc/mtab

Oh, I wasn't sure exactly what you meant when you explained the sda section, so I also tried 

sudo mount /dev/**sdaC:**/media/windowsc

sudo mount /dev/**sda1**/media/windowsc

Sorry if this is a very redundant topic, but in my defense I went back 10 pages in this General section and didn't see anything that would be related.

---

### Post by merlinus on 2007-06-15
> 
sudo mount /dev/sda1/media/windowsc


You left out the necessary space between sda1 and /media

sudo mount /dev/sda1 /media/windowsc

-merlin

---

### Post by sdrawkcab on 2007-06-15
Ok, now that I typed that in, Ubuntu had to think for quite a while before telling me that I had no permission to view the contents of the windowsc folder...

Also, I don't see the drive mounted on the desktop. So I think that it definitely did something, but won't let me see it. I can't remember the command, but maybe I need to make myself the administrator permanently for this session? Just a thought.

---

### Post by ashz on 2007-06-15
Use a Knoppix Live CD...(hmmmm can i say that :P)

---

### Post by sdrawkcab on 2007-06-15
Hmmmm....don't have one of those, and even so I don't have the time to make one :) 

I might check it out sometime though :)

---

### Post by merlinus on 2007-06-15
Knoppix is a great tool!

But perhaps sudo nautilus is all you need....  Then navigate to the drive.

-merlin

---

### Post by ashz on 2007-06-15
Well i only said it because it offers NTFS support which is what you will need to get at a windoze drive. Hence probably why you cannot view it at the moment!!

Laters
Ash

---

### Post by hardyn on 2007-06-15
> **sdrawkcab said:**
> Ok, now that I typed that in, Ubuntu had to think for quite a while before telling me that I had no permission to view the contents of the windowsc folder...

Also, I don't see the drive mounted on the desktop. So I think that it definitely did something, but won't let me see it. I can't remember the command, but maybe I need to make myself the administrator permanently for this session? Just a thought.

typed what?

you are going to have to help us help you a little bit ;)

---

### Post by sdrawkcab on 2007-06-15
So, what exactly is Knoppix used for? Stuff like this?

Well, I navigated to the folder, and it loaded for a long while and finally said that the contents could not be displayed...I then checked the desktop to make sure, but no luck.

---

### Post by hardyn on 2007-06-15
knoppix is just a debian live disk, and yes it has been designed to do things like this... but you have an ubuntu live disk.

you created the directory... and that worked, yes?
you mounted it with no errors?

is it possible that your computer has had a hard disk failure?
do you have some other non standard disk configuration?

---

### Post by sdrawkcab on 2007-06-15
Yes I did everything with no errors including mounting the drive.

Actually this isn't my computer, but I did notice when trying to setup the BIOS boot stuff that the Hard Drive on the computer said something different. It wasn't a type of hard drive or anything...I'm afraid to go check it again because it took me 5 tries to load the Live CD correctly for some reason (different errors each time...it was strange...).

........................I was just informed that the computer place said that it "was broke". Apparently it makes strange noises when it's doing stuff...I didn't hear anything really strange myself, I mean, the disc drive makes loud noises when loading, but I didn't hear anything out of the ordinary.


Anybody think there's any hope?

EDIT: Ok, well this error just popped up in the terminal screen, well, actually, this is what the terminal displayed after trying to view the hard drive...I think this looks bad.... 

> ubuntu@ubuntu:~$ sudo nautilus
Initializing gnome-mount extension

**** (nautilus:11867): WARNING **: Hit unhandled case 6 (I/O error) in fm_report_error_loading_directory**

---

### Post by sdrawkcab on 2007-06-17
IDEA!! What if I were to switch the hard drive to slave mode instead? Think that would work?

I know there's someway to get the stuff off of there 'cause the computer place said they could do it.

---

### Post by sdrawkcab on 2007-06-23
Ok, well, my idea did work. I can now see all of the files. I'm just having trouble getting the files.

I tried copying and pasting and just dragging them into my flash drive, but for the life of me it just won't do anything.

Any ideas on this?

---

### Post by confused57 on 2007-06-23
> **sdrawkcab said:**
> Ok, well, my idea did work. I can now see all of the files. I'm just having trouble getting the files.

I tried copying and pasting and just dragging them into my flash drive, but for the life of me it just won't do anything.

Any ideas on this?
You might want to check out this guide for mounting a FAT32 or NTFS partition:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop)
May not work any better than what you've tried?

---

### Post by louieb on 2007-06-23
well i see you have been messing with this for a week. time to bring out the heavy stuff. if the [SystemRescueCd]("http://www.sysresccd.org/Main_Page") can't get the data your looking at hiring a pro.

---

### Post by sdrawkcab on 2007-07-03
Wow, that looks pretty cool. So, it looks like it works for Windows systems as well?

I guess what I should do is take the drive and plug it internally into a PC and try to access it as slave. I'm just kinda freakin' out 'cause I need it in a couple of days.

---

