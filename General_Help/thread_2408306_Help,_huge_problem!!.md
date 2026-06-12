---
title: "Help, huge problem!!"
date: 2018-12-16
forum: General Help
---

### Post by Amelia_Hayner on 2018-12-16
Computer has crashed. I am typing with tiny mouse hands on kindle. We have stuff pending on EBay for Christmas!
We get an screen that says:
Dev/sd1 contains a file system with errors, check forced.
Inboxes that were part of a corrupted orphan linked list found.
Dev/sda1: UNEXPECTED INCONSISTENCY; run fsck manually.
Cisco exited with status code 4
Root filesystem on dev/sda1 requires a manual deck.
...and then other stuff about somewhere called BusyBox.
Man I feel like I need to call a priest in here to splash holy water or something on it at this point.
Any help earns points with Santa.
Thank you!!!!

---

### Post by findingthebalance on 2018-12-16
Give this a go,At the (initramfs) prompt, type fsck -f /dev/sda1 to check/repair your file system.

---

### Post by Amelia_Hayner on 2018-12-17
That was not found.

I am letting it run a memory test now, don't know what else to do.

---

### Post by ra7411 on 2018-12-17
There are people in here who can probably help you.
Post what kind of machine, what kind of drives, is Windows also on the machine, what Ubuntu you're running, etc.
Post  as much about err messages as you can, any prior problems
That will put experienced people in the position to give informed help.

---

### Post by Amelia_Hayner on 2018-12-17
Asus, running Mate 16.04

128 bit mode

Still saying it needs a manual fsck

Wiped windows off when mate was installed

---

### Post by speartip on 2018-12-17
> **Amelia_Hayner said:**
> Still saying it needs a manual fsck

And did you run that check as in post 2?

---

### Post by Amelia_Hayner on 2018-12-17
I tried. It said not found. I just completed second memory test ' pass complete, no errors, press Esc to exit'

Ok, tried fix cited earlier. It says fsck from util-linux 2.27.1

Also, enter "help" for a list of built-in commands. That look like gibberish. And.. how would you know which one? And how to enter it? What a mess.

---

### Post by #&amp;thj^% on 2018-12-17
> **Amelia_Hayner said:**
> I tried. It said not found
And how to enter it? What a mess.

You need space's and the proper "absolute/path" to get the command and argument. The command is fsck, and the argument is the device /dev/sda1. Try:
```
 fsck /dev/sda1
```
Note that there is a space between fsck and /dev/sda1.

[B]To avoid data loss due to disk failure, this command should be given from a "live" Ubuntu session.
[/B]

Additionally you may want to use "**fsck -y /dev/sda1**" to answer yes automatically to any questions fsck asks.
Good Luck.

---

### Post by ra7411 on 2018-12-17
I'm wondering if you have used the cd/dvd or usb thumb drive that was used to install Mate to deal with this problem. The process is to shut down the machine, then power up with the install cd/dvd/usb install plugged in. The machine's bios should detect the install stuff and boot up with that, and that will let you work on the machine.

With some computers, you have to get into the bios, or press some function key, to get the boot up process to go to the install disc rather just going to the regular drive (that now has problems).

I did some work on an Asus a couple years ago, and it went something like this:

[LIST=1]
[*]Plug in your USB drive
[*]Turn the Zenbook on
[*]Enter UEFI (BIOS) through pressing ESC or F2
[*]In 'Boot' tab: 'Disable Fastboot' (*)
[*]Press F10 to save & exit
[*]Immediately press ESC or F2 again
[*]In 'Boot' tab: your USB drive should be listed - change the order
[*]Press F10 to save & exit
[*]Your Zenbook should now boot from the USB drive
[/LIST]
[FONT=inherit]Good luck[/FONT]

---

### Post by Amelia_Hayner on 2018-12-17
Got the disc in there and stuff is happening! Will let you know....

---

### Post by Amelia_Hayner on 2018-12-17
Well, just went whole hog and reinstalled . We lost some stuff but heck. Now. Everything looks ok BUT it's offline. We have cable hook up. Kindle is working.

---

### Post by 4kh3RAm on 2018-12-17
Use Clonezilla and you'll never have that problem again.

---

### Post by klundermann on 2018-12-30
Thanks, everybody -- I just had the same problem, and running ```
fsck <path shown in error message>
``` fixed it.  I do wish, though, that I read as far as 1fallen's post about the -y option before I ran fsck!

BTW, I had this problem under Ubuntu 18.04 on a machine that dual-boots with Windows 10.  I'm not certain, but I believe the problem occurred after a major Windows update.

---

