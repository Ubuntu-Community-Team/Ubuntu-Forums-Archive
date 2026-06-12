---
title: "[SOLVED] Installing app from Vendor"
date: 2007-10-04
forum: General Help
---

### Post by MacDuff on 2007-10-04
I am installing a new Samsung ML-2571N laser printer and am trying to install the printer GUI interface to change printer settings.

I am still quite new to Ubuntu and the instructions provided by Samsung require installation from the CD which in turn requires re-starting the computer using command lines.  It all gets quite complicated for a newbie, so I copied the Linux directory from the CD to my desktop and followed the instructions provided on other forum pages to install .sh files but I just get error messages. 

Here is my most recent attempt and the result I got:

mac@ubu-comm:~$ sudo sh Desktop/Samsung_ML-2571N/Linux/install.sh
Desktop/Samsung_ML-2571N/Linux/install.sh: 1167: source: not found
ERROR: HARDWARE_PLATFORM undefined, execution aborted

Can someone suggest what I am doing wrong and how I can make this application run?

Thanks

---

### Post by distroman on 2007-10-04
Could you link to the howto you're following?
I am not sure about this mind you, but give this a try. 
```
cd Desktop/Samsung_ML-2571N/Linux
```
```
sudo sh install.sh
```
Post errors if any.

---

### Post by MacDuff on 2007-10-05
Distroman:
That produced the same error message as in my original post.

As requested, here is one of the instructions from the thread "How to install ANYTHING in Ubuntu"

"Shell Script Installer (.sh, .bash, ...)
    You can run the shell script inside a terminal with the command sh. If the script is called test.sh and is on the desktop of user carl, you can install it with sh /home/carl/Desktop/test.sh. Keep in mind that the script might not have permission to execute in your file-system."

The following are the instructions from the Samsung Installaton manual:

" Installing the Unified Linux Driver
1 Make sure that you connect your machine to your computer. Turn both the computer and the machine on.
2 When the Administrator Login window appears, type in root in the Login field and enter the system password.

NOTE: You must log in as a super user (root) to install the printer software. 

3 Insert the printer software CD-ROM. The CD-ROM will  automatically run.
If the CD-ROM does not automatically run, click the icon at the bottom of the desktop. When the Terminal screen appears, type in:
If the CD-ROM is secondary master and the location to mount is /mnt/cdrom,
[root@localhost root]#mount -t iso9660 /dev/hdc /mnt/cdrom
[root@localhost root]#cd /mnt/cdrom/Linux
[root@localhost root]#./install.sh

NOTE: The installation program runs automatically if you
have an autorun software package installed and configured."

End of Quote from manual
The Samsung instructions appear to be similar to those provided in the Forum but I did not try the Samsung instructions because I was not clear on whether the CD-ROM is a secondary master etc.
Any more advice you can provide would be appreciated.

---

### Post by Seisen on 2007-10-05
nevermind

---

### Post by distroman on 2007-10-05
Sorry did not read though it, but this might help.
[http://ubuntuforums.org/showthread.php?t=287747](http://ubuntuforums.org/showthread.php?t=287747)
[http://ubuntuforums.org/showthread.php?t=288397](http://ubuntuforums.org/showthread.php?t=288397)

---

### Post by MacDuff on 2007-10-07
Thanks Distroman:

I had a quick look at the recommended postings and it looks like that will solve my problem.  When I have a moment to spare, I will try out their suggestions.

BTW, How did you find those references?  I did some searches and they did not show up for me.  I am quite new to Ubuntu and there is so much to learn.  There seems to be answers, somewhere, to almost every question I might have but is there some central repository of information that is searchable?

You folks on the forums are great and a huge asset to Ubuntu/Linux but I hate to ask the same questions that may have been asked and answered dozens of times before.  It seems a big waste of your time.

Mac

---

### Post by distroman on 2007-10-07
> **MacDuff said:**
> Thanks Distroman:

I had a quick look at the recommended postings and it looks like that will solve my problem.  When I have a moment to spare, I will try out their suggestions.
Hope it works out, gl.

> **MacDuff said:**
> BTW, How did you find those references?  I did some searches and they did not show up for me.  I am quite new to Ubuntu and there is so much to learn.  There seems to be answers, somewhere, to almost every question I might have but is there some central repository of information that is searchable?

uhm, not sure what to say, google and yes I agree, you can find just about anything.
[http://sudarmuthu.com/blog/2006/05/07/google-search-syntax-dissected.html](http://sudarmuthu.com/blog/2006/05/07/google-search-syntax-dissected.html)

```
site:ubuntuforums.org ERROR: HARDWARE_PLATFORM undefined, execution aborted
```

> **MacDuff said:**
> You folks on the forums are great and a huge asset to Ubuntu/Linux but I hate to ask the same questions that may have been asked and answered dozens of times before.  It seems a big waste of your time.

Mac
As for waste of time I am not so sure someone has to be the first to ask (you never know) and nobody is forcing anyone to answer. ;-)

---

