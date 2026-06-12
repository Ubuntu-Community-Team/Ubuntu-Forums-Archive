---
title: "Installing Programms on a USB Stick"
date: 2015-10-11
forum: General Help
---

### Post by Mamsie on 2015-10-11
Hello,

because my Hard Drive is almost full, I would want to install programms on a USB Stick (for example Steam). Everytime I try to install the .deb package, it doesn't even ask me where I want it.

How can I install Steam onto a USB Stick because my hard drive is full?

(I am very new to Linux, I always used Windows before, so don't be mad if this is a stupid question)


Thanks in the future,

Greetings, Mamsie

---

### Post by yancek on 2015-10-11
I doubt that would work.  Software programs in Linux are dependent upon libraries which are expected to be in a specific location and the software (Steam) expects to be in a specific location.  I've never used that specific software but I expect that if you wanted to do it this way it would involve some pretty serious programming on your or someone's part.  Get a bigger drive or remove some software or data.

---

### Post by Mamsie on 2015-10-11
Removing Data is sadly not possible, because nothing is on it except for Lubuntu (3,2GB disk).

I thought it would be as easy as it is for most programms under windows.

Thank you for answering!

---

### Post by mcduck on 2015-10-11
The difficulty is that programs aren't really installed in a single location like they are in Windows. Instead, all the files are placed in different places based on the purpose of the file (executable binary file in /bin or /usr/bin, system-wide configuration files inside /etc, icons in /usr/share/icons, documentation in /usr/share/doc, library files in /lib or /usr/lib and so on.). Because of this it's not really possible to easily move a individual programs to another drive, you'd have to move one of these directories instead.

Much easier way to gain free space on your main drive would be moving user home directory, /home, instead. Or perhaps just some of the stuff from your own home.

Also keep in mind that Steam doesn't use same system for installing it's games, so even if Steam itself is installed in the normal location(s), you can freely choose where it keeps it's games. Although installing games on USB stick would give you some horrible loading times...)

---

### Post by ajgreeny on 2015-10-11
With a drive of only 3.2GB I think you will probably soon run out of space anyway, so trying to do what you want may, unfortunately for you, be a waste of time.

Normal OS activity will very quickly fill the remaining 700MB you have free according to your other thread [http://ubuntuforums.org/showthread.php?t=2298460&p=13371315#post13371315](http://ubuntuforums.org/showthread.php?t=2298460&p=13371315#post13371315) unless you are prepared to carry out some very regular cleaning up of the system files to release space.

Sorry to say it but the only sensible answer, particularly if you want to play games which are usually space hogs, is to get a new hard disk, either SSD or standard spinning disk instead of your tiny 3.2GB disk.

---

### Post by Mamsie on 2015-10-12
Thank you for answering. It's too bad I can't install programms on a stick.

I won't buy a new disk because I'm only using this PC for two weeks while my normal one is in repair.
I would also not even try to play games on this PC, I just wanted to browse around steam and activate some product keys I have laying around here.


Thank you for answering then this thread can be closed.

---

### Post by sudodus on 2015-10-12
What you can do is **install the *whole* linux system** into a USB stick, or run a ***persistent live*** system (from the stick). See this link

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it)

---

