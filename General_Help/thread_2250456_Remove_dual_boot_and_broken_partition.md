---
title: "Remove dual boot and broken partition"
date: 2014-10-28
forum: General Help
---

### Post by jrosado on 2014-10-28
I have Xubuntu and Win XP on an old laptop.  Ubuntu has become corrupted can't be updated. 

I want to delete the dual boot and the broken ubuntu partition without deleting the WinXP partition.

Any help will be greatly appreciated.

[IMG]C:\\Owner\desktop\laptop boot.jpg[/IMG]

---

### Post by ajgreeny on 2014-10-28
If you are using grub to boot both OSs you must restore the WinXP bootloader files prior to removing the Ubuntu partitions or you will be unable to boot any OS at all.

You can do this with the XP Installation disk, or you can even do it with a live Ubuntu disk by doing the following from your Live CD:
```
sudo apt-get install lilo
```
Ignore the warning then 
```
sudo lilo -M  /dev/sda mbr
```

Then you should be able to boot directly into Windows again if all goes well.

---

### Post by jrosado on 2014-10-31
I tried your suggestion, but when I insert either of the discs you mentioned, the DVD light stays on (over 10 minutes) and nothing appears on screen. Eventually, the boot menu that Ubuntu originally created comes up.

[IMG]http://heart.kumu.org/laptop boot.jpg[/IMG]

---

### Post by Bucky Ball on 2014-10-31
Which release of Ubuntu are you using?

You say 'it's become corrupted' but give no indication of how.

---

### Post by Bucky Ball on 2014-10-31
Which release of Ubuntu are you using?

You say 'it's become corrupted' but give no indication of how or what the issue is re. corruption of Ubuntu. What's happening?

Anyway, you want to go back to XP and that has been explained in the last post.

---

### Post by jrosado on 2014-11-01
Perhaps "broken" wasn't the right word.  Maybe "crippled" would have been more accurate. I can boot into Ubuntu (don't know the version or remember how to find it), but it tells me that I need to update it.  When I try to update, 
the following pops up in the upper right corner:

     "An error occurred, please run Package Manager
     from the right click or apt-get in a terminal
     to see what is wrong.
     The error message was: 'Error: Broken Count>0'
     This usually means that your installed packages 
     have unmet dependencies.

When I tried to run Package Manager I got more error messages (and gave up).

In Xubuntu, as it is now, I can use the browser and the few apps I've installed.  

I hadn't used this laptop in quite a while. When XP dropped all support I thought I might take it out and then put the latest version of Xubuntu in.  (Some years ago, when I attempted to install Ubuntu in this machine, it didn't work, but Xubuntu did).  

I've been working with computers for over 40 years, Cobol, Algol, CP/M, DOS and Windows since version 1 and even built some from scratch,  But I don't mind admitting I'm over my head in this one.

---

### Post by Bucky Ball on 2014-11-01
Open a terminal and type:

uname -a

Post the result here, please.

---

### Post by jrosado on 2014-11-02
Results in Terminal:

owner@PCG-37:-S uname -a
Linux PCG-K37 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:12:00 UTC 2013 1686 
1686 1686 GNU/Linux[FONT=verdana][/FONT]

---

### Post by Bucky Ball on 2014-11-02
From this I'm guessing you're running 13.10 or older? 14.04 LTS is at kernel 3.13.0-39.

If this is the case, it has reached EOL (end of life) and that would be the problem with attempting to update. EOL releases are no longer supported by Canonical or these forums. If you are using 12.04 LTS (but don't think that kernel got there) then disregard, otherwise, read [THIS]("http://ubuntuforums.org/showthread.php?t=2229730").

Please install a supported version (I recommend 14.04 LTS with five years support) and post a new thread with a descriptive title and detail any issues you face (include which release you are using in all new threads).

Thanks and good luck.

---

