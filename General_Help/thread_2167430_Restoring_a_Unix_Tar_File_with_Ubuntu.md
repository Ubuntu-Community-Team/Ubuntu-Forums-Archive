---
title: "Restoring a Unix Tar File with Ubuntu"
date: 2013-08-13
forum: General Help
---

### Post by dFWPspP on 2013-08-13
I have all of these old DDS3 and DDS4 tapes that I need to restore the files off of.  The only information that I really know is that they were put on the tapes about 10 to 20 years ago using Digital Unix.  They are in a Tar file format.  I have been using Ubuntu 13.04 to try to restore these files but I've had zero success so far.  I have really no idea how to get these files off of here.  A couple of commands that we've tried in terminal are:
 
 
/media/archive/SCSI/Linux$ sudo dd if=/dev/st0 ibs=128k | tar -vxf -
 
 
sudo tar - xzf /dev/st0 /media/archive/SCSI/Linux
 
 
 
/media/archive/SCSI/Linux is what I am trying to restore to and st0 is the Tape Drive name
 
 
Please help me out!!
Thanks

---

### Post by VMC on 2013-08-13
can you just copy that tar file to /tmp and then extract from there?
Something like this:
```
tar xfpvz /tmp/tarfile -C [COLOR=#000000]/media/archive/SCSI/Linux[/COLOR]/
```

---

### Post by dFWPspP on 2013-08-13
The error I got from that is
tar: pvz: Cannot open: No such file or directory 
tar: Error is not recoverable: exiting now


Thank you

---

### Post by VMC on 2013-08-13
I made an error on the code section above, in case you just copy&pasted it. Its corrected now.

---

### Post by dFWPspP on 2013-08-14
I didn't just just and paste before, I kinda made my own based off of yours.  But when i copy and pasted your modified code the output I got was 

tar (child): /tmp/tarfile: Cannont open: No such file or directory 
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable:exiting now 


The funny thing is that when I do write something in terminal sometimes the tape drive will act like its starting up and the terminal response imeadiately responds with whatever error is gives me and then I get a response from the tape drive
Thanks

---

### Post by steeldriver on 2013-08-14
Did you actually copy the tar file off the device into /tmp?

I don't have any experience of this, but there are some specific tools for controlling tape devices (mt) and reading from dds devices in particular (dds-dd - in the package dds2tar)

[http://manpages.ubuntu.com/manpages/precise/man1/mt-gnu.1.html](http://manpages.ubuntu.com/manpages/precise/man1/mt-gnu.1.html)
[http://manpages.ubuntu.com/manpages/precise/man1/dds-dd.1.html](http://manpages.ubuntu.com/manpages/precise/man1/dds-dd.1.html)

Hope this helps

---

### Post by zacktu on 2013-08-14
There are so many things to go wrong when you're trying to extract from a source that you're not sure of.  Instead using the 'x' switch, why not use 't' first?  That will list the files in the archive.

---

### Post by dFWPspP on 2013-08-15
Thanks for all of the suggestions.  steeldriver, I looked over those manpages  before and they were little help but thank you.  And zacktu, I tried with the t and it didn't do anything.  If ii run 'mt -f /dev/st0   status' it would show the name and one other name and then it would display 0 for everything else such as files, block #, ect.   My internship is done today so this no longer a problem for me.  But any other suggestions would still be looked at and I can't guarantee that other guys will try it out.  I was starting to think that the tapes might have gone bad seeing that the newest ones are 15 years old.  Thanks guys.

---

