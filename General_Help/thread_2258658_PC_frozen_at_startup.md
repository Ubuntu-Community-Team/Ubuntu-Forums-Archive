---
title: "PC frozen at startup"
date: 2014-12-29
forum: General Help
---

### Post by Camilia on 2014-12-29
Since I turned my desktop PC off pushing the button on the tower it won't start up. It is frozen at point with ubuntu symbol. :confused::  Now communicating via a laptop. 

Tried F9 diagnostic and is okay.
Started it with F11. Clicked repair and prompted to log in. Tried previous ubuntu and also prompted to log in. I get message that ubuntu 12.01 is no longer supported. So turned it off at the tower. Turned the power via power strip off to the PC for a few hours. Still can't get in.

I think it needs a command. For after logging in page looks like terminal.

---

### Post by phidia on 2014-12-29
You could try > startx or > sudo startx and see if that starts your gui/desktop or provides an error message.

For reference [the startx command/ubuntu]("http://askubuntu.com/questions/518454/what-does-startx-command-do")

---

### Post by Camilia on 2014-12-29
> **phidia said:**
> You could try  or  and see if that starts your gui/desktop or provides an error message.

For reference [the startx command/ubuntu]("http://askubuntu.com/questions/518454/what-does-startx-command-do")
Did sudo startx
Got error in locking authority file and usr/bin/x: not found

Perhaps I could start up using the boot menu?
Options are:
WDC WD6400AAKS OR hp DVD A DH16ABLH.
Which 1 should I use?

---

### Post by phidia on 2014-12-29
> **Camilia said:**
> Did sudo startx
Got error in locking authority file and usr/bin/x: not found

Perhaps I could start up using the boot menu?
Options are:
WDC WD6400AAKS OR hp DVD A DH16ABLH.
Which 1 should I use?


The WDC ... entry is your hard drive so that's where the install is right?

You might want to read [this related thread]("http://ubuntuforums.org/showthread.php?t=1890457") from the forums that I got to by searching that error.

---

### Post by Camilia on 2014-12-29
> **phidia said:**
> The WDC ... entry is your hard drive so that's where the install is right?

You might want to read [this related thread]("http://ubuntuforums.org/showthread.php?t=1890457") from the forums that I got to by searching that error.
I don't know. My son-in-law download the program on my pc. Guess I could try that.

Tried the reboot. Still frozen

Read the thread. 
Tried these
cd mv .Xauthority .XauthorityBak
Result no such file

ls -l /home/user/.Xauthority
Result no such file

---

### Post by phidia on 2014-12-29
Try > sudo apt-get update and when that completes try startx again.

If that fails to get you a desktop then perhaps do > sudo mv .Xauthority .XauthorityBak
and reboot.

---

### Post by Camilia on 2014-12-29
Tried sudo apt-get update 
Result The package list or status file could not be parsed or opened.

Tried sudo mv .Xauthority .XauthorityBak
Result unable to open /var/lib/sudo/user/tty1: Read-only file system my: missing destination file openrand after '.Xauthority.XauthorityBak 

Thinking it would be easier to put ubuntu on a usb drive and reboot. Problem is my desktop can't except current ubuntu 14.01. Found 12.04 download from softpedia but it had broken files.

Perhaps something in recovery menu would work. Just don't know which option.
Options are:
run in falisafe graphic mode
update grub bootloadeer
drop to root shell prompt

---

### Post by phidia on 2014-12-29
You could try [this]("http://distrowatch.com/table.php?distribution=antix") or go to the home page there at distrowatch and look for another linux variety. The distro I linked is good on older hardware. There should also be links for 12.04 that work. if I find one I will insert a link to the download.

This link should work for [12.04 images]("http://releases.ubuntu.com/12.04/")

---

### Post by Camilia on 2015-02-03
I ended up burning ubuntu to a flash drive and reinstalled it. Success!! Now just got to add email addresses to desktop. I prefer desktop to laptop. Thanks everyone for your help!!

---

