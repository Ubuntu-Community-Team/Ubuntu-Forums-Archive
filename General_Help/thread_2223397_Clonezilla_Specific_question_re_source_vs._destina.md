---
title: "Clonezilla: Specific question re: source vs. destination"
date: 2014-05-10
forum: General Help
---

### Post by Kurt_Alan on 2014-05-10
[COLOR="#000000"][SIZE=5]****[/SIZE][/COLOR]

This is my first experience using Clonezilla.  I have successfully created a live USB bootable flash drive after installing the Tuxboot PPA. I've tried it and it works.  I just don't know how to use it :-)

When I initiate Tuxboot from terminal in GUI, I am confused about selections for source vs. destination since nothing is labeled or explained.

I want to clone an .iso image of 14.04 FROM my ssd TO my flash drive, so that I can later restore my configured OS TO my ssd FROM my flash drive.

Or from /dev/sda1 to /dev/sdb1 in the first case and the reverse in the second.  (I have run df to check which drive is which).  In the Tuxboot window I check "Show All Drives."

In the left drop-down menu I can select Hard Drive or USB Drive.  I don't know which one to pick.  In the right drop-down menu I can select sda1 or sdb1.  Again, I don't know which one to pick from the point-of-view of Tuxboot because it does not label source or destination.

---

### Post by Kurt_Alan on 2014-05-10
[SIZE=5][COLOR="#000000"]****[/COLOR][/SIZE]

More comments:

I went back to clonezilla.org and looked again at their tutorial with screenshots on Save Disk Image, which is what I want to do. The generic example is "Save 1st disk (sda) as an image on 2nd disk (sdb).  

The directions then state to start Tuxboot from the USB device as opposed to from the terminal beginning with a GUI interface.  Then why is the GUI interface there? Most confusing . . . 

Now I found the problem but I don't know the solution.  I proceed smoothly through all the screens (from USB) until I am told to install a USB flash drive, wait a few seconds, then Enter.  (Later I will select this sdb as my image repository).

But wait! I am already working from my USB drive! How am I supposed to install it if it is already installed and mounted???  Am I supposed to install a SECOND USB drive? --One USB for Tuxboot and a second USB for the image?  No mention is ever made of TWO USB's to clone an image . . . And if I pull it out and reinsert it, the process aborts . . .

---

### Post by Kurt_Alan on 2014-05-12
**[SIZE=5][/SIZE]**

Update:

Yes, two USB pendrives are required: one to boot the clonezilla tool and the other to use as the repository of the image.

I don't know if this is self-evident but it should have been mentioned!

I successfully cloned an image.  It was easy and straightforward.
I'm now doing a test restore . . .

When this succeeds, I will close this thread, then write out the basic steps for using clonezilla and put that in the beginners' section.

---

### Post by sammiev on 2014-05-12
> **Kurt_Alan said:**
> **[SIZE=5][/SIZE]**

Update:

Yes, two USB pendrives are required: one to boot the clonezilla tool and the other to use as the repository of the image.

I don't know if this is self-evident but it should have been mentioned!

I successfully cloned an image.  It was easy and straightforward.
I'm now doing a test restore . . .

When this succeeds, I will close this thread, then write out the basic steps for using clonezilla and put that in the beginners' section.

Good Luck on the restore. :popcorn: I never had trouble with a restore yet.

---

### Post by Kurt_Alan on 2014-05-15
**[COLOR="#000000"][SIZE=5][/SIZE][/COLOR]**

My original system was 14.04 on top of 12.04 on top of 10.04 via clean install.
I tested my restore on this and it worked perfectly!  I then did a clean install of 14.04, configured that for two days unit it was "just right," then created an image of that.

The one "gotcha" in the restore process was that when I was following the clonezilla screenshots for restore and they were the same as for create image EXCEPT that you had to choose Advanced instead of Beginner default to reveal the restore option . . . 

And the fact that you have to use two flash drives, one for Tuxboot and the other for the restore repository, even though the directions never make that clear . . . 

But once the "first time experience" bugs are worked out, clonezilla works like a charm!

---

### Post by spynappels on 2014-05-15
If you have access to another Linux box running an ssh server, you can set up networking in Clonezilla and save the image directly to the other linux box by mounting a directory on it on the Clonezilla fs using sshfs.

One less USB stick to worry about...

---

