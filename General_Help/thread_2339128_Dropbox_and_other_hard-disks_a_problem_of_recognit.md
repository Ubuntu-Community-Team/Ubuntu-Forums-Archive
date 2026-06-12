---
title: "Dropbox and other hard-disks: a problem of recognition?"
date: 2016-10-05
forum: General Help
---

### Post by acidraindance on 2016-10-05
Greetings,

I am an enthusiastic, first time Ubuntu user and am having difficulty with a handy but problematic program called Dropbox. This machine involves is a 60GB SSD on which I've the OS (Ubuntu 16.04) install, and then a 2TB hard-disk which houses most of my media. 

In short, I don't want Dropbox to be on the tiny OS hard-disk, but on the more appropriate and accommodating larger drive. This should be easy, achievable by going to Dropbox's Preferences, then Account, then clicking the 'move' function--yet this is where my troubles begin; for no matter what I seem to do, the 2TB disk does not register in this menu and I cannot select it. Hence the little SSD fills up and complains and I can't properly access my data... 

I've read a lot of blog posts and forum responses about how Dropbox doesn't like going on external drives, and a few different work arounds, but all of them require the Dropbox desktop app to recognise the disk in question... I suspect my problem may be something to do with the HPFS/NTFS or some other technicality of the disk mounting process that I do not understand. I've attached a screen shot of the disk utility and mount options window, in case this is a factor. 

Many thanks in advance for any help!

---

### Post by coffeecat on 2016-10-05
Not a Multimedia Software question.

*Thread moved to **General Help**.*

---

### Post by clymbon on 2016-10-05
The disk utility screenshot shows your problem: The disk is not mounted.

Go to the "Mount Options" and turn automatic mounting on.  The mount options display is a little confusing - move the slider over the "On" position.  You will then see the "Off" label.  That means the option is turned on.  Get it?  As I said, it's confusing.  I think the idea is that it's a slider that can be moved to the "on" or "off" position.  When you move it to the "on" position it covers the "on" label.  (Personally, I think this is bad user interface design.)

---

### Post by DogMatix on 2016-10-05
> **clymbon said:**
> The disk utility screenshot shows your problem: The disk is not mounted.

The mount options display is a little confusing - move the slider over the "On" position.  You will then see the "Off" label. That means the option is turned on.)

Wow! not the best UX. That does need addressing.

---

### Post by acidraindance on 2016-10-05
> **clymbon said:**
> The disk utility screenshot shows your problem: The disk is not mounted.

Go to the "Mount Options" and turn automatic mounting on.  The mount options display is a little confusing - move the slider over the "On" position.  You will then see the "Off" label.  That means the option is turned on.  Get it?  As I said, it's confusing.  I think the idea is that it's a slider that can be moved to the "on" or "off" position.  When you move it to the "on" position it covers the "on" label.  (Personally, I think this is bad user interface design.)

Gha, that is a little confusing, thanks for pointing that out. However it does not seem to be the cause of my problem.  
  
 I initially turned auto-mount off while following [these instructions,]("https://www.liberiangeek.net/2013/12/move-dropboxs-folder-to-an-external-drive-in-ubuntu/") yet whether it is on or off does not seem to affect Dropbox inability to recognize the hard-disk... 

Perhaps I should add that the Ubuntu system recognizes the disk fine, its just Dropbox…

---

### Post by QLee on 2016-10-06
> **acidraindance said:**
> Perhaps I should add that the Ubuntu system recognizes the disk fine, its just Dropbox…

If I remember correctly, dropbox needs to have its folder with user (owner) only permissions, does your mount allow a folder with such permissions?

---

### Post by clymbon on 2016-10-07
Actually, I'm sorry, I had that backwards...  I think you want the "Automatic Mount Options" slider set so that it displays "ON".  Slide the slider to the right.  Unless you want to manually tweak the mount options.

But anyway it does show your disk is not mounted.

---

### Post by Geoffrey_Arndt on 2016-10-08
So, along with changing the 2nd or extra drive to automount (per post #7 above), then . . . just use the Dropbox utility (widget) in the desktop top panel to "move" the folder to the new drive.   As long as the drive is "available" for read/write upon startup, and remains mounted until shutdown, all should work as the OP wants.

See:  [http://www.howtogeek.com/246590/how-to-change-the-location-of-your-dropbox-folder/](http://www.howtogeek.com/246590/how-to-change-the-location-of-your-dropbox-folder/)

---

### Post by acidraindance on 2016-10-08
> **QLee said:**
> If I remember correctly, dropbox needs to have its folder with user (owner) only permissions, does your mount allow a folder with such permissions?

Weirdly, when I look at my 2TB drives permission, it says in a little sentence down the bottom 'You are not the owner, so you cannot change these permissions'. I can create and delete files, but apparently am not the owner... Does this mean I need to formate the drive or something the such? Could this be the problem preventing DropBox from recognizing the drive?

---

### Post by acidraindance on 2016-10-09
> **Geoffrey_Arndt said:**
> So, along with changing the 2nd or extra drive to automount (per post #7 above), then . . . just use the Dropbox utility (widget) in the desktop top panel to "move" the folder to the new drive.   As long as the drive is "available" for read/write upon startup, and remains mounted until shutdown, all should work as the OP wants.

The 2TB drive is now set to auto-mount, and it is read-able and write-able from start up to shut down. I've tried using the DropBox utility to move the folder, the problem is that Dropbox does not recognize 2TB drive, only the 60GB drive that Ubuntu is installed on. Here is a screenshot of the DropBox utility as I attempt to move the folder. As far as I can tell it displays a notable lack of other drives... 

 [ATTACH=CONFIG]271558[/ATTACH]

---

### Post by Skaperen on 2016-10-09
i am wondering if Dropbox builds a table of drives/devices at install/setup time.  maybe try uninstalling Dropbox and install it again with the 2TB drive mounted.

---

### Post by Geoffrey_Arndt on 2016-10-13
> **acidraindance said:**
> The 2TB drive is now set to auto-mount, and it is read-able and write-able from start up to shut down. I've tried using the DropBox utility to move the folder, the problem is that Dropbox does not recognize 2TB drive, only the 60GB drive that Ubuntu is installed on. Here is a screenshot of the DropBox utility as I attempt to move the folder. As far as I can tell it displays a notable lack of other drives... 

 [ATTACH=CONFIG]271558[/ATTACH]

Try clicking on the drop-down arrow in the bar to right of "Look In" . . . on my display I can see plugged in usb flash-sticks and other drives.   Also, you can probably manually type in the file path in this same field (might have to display it first in another file manager and copy it).

---

### Post by acidraindance on 2016-10-18
> **Geoffrey_Arndt said:**
> Try clicking on the drop-down arrow in the bar to right of "Look In" . . . on my display I can see plugged in usb flash-sticks and other drives.   Also, you can probably manually type in the file path in this same field (might have to display it first in another file manager and copy it).

None of the graphical interfaces, like the drop-down 'Look In' menu, seemed to detect any of the drives I have plugged into my machine; neither hard-disks or USBs. 

However, the good news is typing in the file path manually --or as you suggest copying it, as there consist of a series of highly unmemorable names like "/mnt/4C942754942852B6"-- seemed to do the trick. This means I can happily write the following word in friendly bold letters: 
[INDENT=2]**SOLVED**.
[/INDENT]
 
This is to say that I have now successfully moved the Drop-box folder and it seems to be working perfectly. Also, the same trick seems to work with my torrent download folder, which likewise couldn't show the drives in its GUI. 

So, to everyone who responded with suggestions - thank you very much for your help!

---

