---
title: "Two questions for a new installation"
date: 2008-04-01
forum: General Help
---

### Post by sideburns on 2008-04-01
For several months, my sister's been curious about Linux.  (I dual boot Windows and Fedora.)  Last Thursday evening, she was given a live CD of Ubuntu and the next morning, after only fifteen minutes of experimentation, decided that she WANTED it.  (I'm so proud of her!)  The next morning, she started the install, with me there for hand holding.  (She's not a geek; I'd never have suggested Fedora to her, if you're curious about that.)

All went well, and she's having fun, but we have two questions.  First, as she was using a Lexmark printer, we had trouble getting it working with Ubuntu.  I found instructions on how to install drivers that should work, but when she tried using apt-get, we were asked to insert the installation CD/DVD, which of course, we don't have.  I'm sure this is just a matter of editing a config file, but I don't know which one.  A pointer to the appropriate Useful Information would be appreciated.

Second, we didn't have it import her Documents and Settings from Win2k.  Now, we'd like to have access to her Windows disk (Literally.  She has two hard disks, one for Windows and one for Linux, because whoever had this second-hand computer before her installed two 40Gig drives.) from Linux.  As far as I can see, Ubuntu doesn't automount Windows disks like Fedora does.  Is there a simple command to change this, or do I need to play with fstab?  If so, will I need to use umount=0,0,0,0 as a mount option to avoid having it mounted read only?

All in all, I must say I'm impressed by Ubuntu, and would recommend it to any non-geek interested in experimenting with Linux, or in fleeing from Microsoft.

---

### Post by forrestcupp on 2008-04-01
First, about the CD thing.  Go to System->Administration->Software Sources.  In the 'Ubuntu Software' tab make sure every box is checked **except** the CD one, uncheck that one.  Then open a terminal and type:
```
sudo apt-get update
```
Then do whatever you were going to do.

About the Windows drive.  What version of Ubuntu are you using.  If you are using Gutsy (7.10), it should automount an NTFS drive.  Look in /media to see if it's there.  If not, try installing the NTFS read/write support just to be sure you have it
```
sudo apt-get install ntfs-3g
```
If you already have it, and still can't find your drive, try booting to Windows and make sure you get a complete shut down.  If Windows doesn't shut down properly, Linux can't mount the drive.

---

### Post by forestpixie on 2008-04-01
First - open software sources in sys >admin - enable all except cdrom and src - if you want go to 3rd party tab and enable the partner in there - close and reload when asked.

The file it modifies is  /etc/apt/sources.list

Second - I though that gutsy dealt with ntfs automatically - you cane get the ntfs config tool which sorts read/write for ntfs drive open a terminal and

```
sudo apt-get install ntfs3g ntfs-config
```

it might already have ntfs-3g installed

---

### Post by sideburns on 2008-04-03
Thanx to both of you for your help.  I'd have gotten back to you sooner, but we've just had the time to try your suggestions out.  As it turns out, we didn't need to install anything for the Lexmark printer, because my sister bought an Epson, which plays nicely with Linux, TYVM.  Also, her Windows drive turned out to be mounted as /DRIVE_C, which I hadn't spotted before.  As Cutey Bunny used to say, "All's swell that ends swell!"

---

