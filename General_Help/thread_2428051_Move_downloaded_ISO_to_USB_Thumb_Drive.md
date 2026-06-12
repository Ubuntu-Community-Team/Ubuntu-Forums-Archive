---
title: "Move downloaded ISO to USB Thumb Drive"
date: 2019-09-29
forum: General Help
---

### Post by freddy58 on 2019-09-29
I am running Ubuntu on this laptop and I am need of a program that can burn a downloaded ISO file of an operating system to USB thumb drive and make it bootable.  Any Ideas on what works good?

---

### Post by jeremy31 on 2019-09-29
Doesn't startup disc creator work?  You might need woeusb for Windows ISO's

---

### Post by freddy58 on 2019-09-29
What I am trying to do is put Ubuntu Studio on my desktop, then install Linux Mint 19.2 behind that

---

### Post by deadflowr on 2019-09-29
> What I am trying to do is put Ubuntu Studio on my desktop, then install Linux Mint 19.2 behind that
behind how?
What do you mean?

---

### Post by freddy58 on 2019-09-29
I want to put both ISO files on the same hard drive and I want to install Linux mint second, so grub puts Linux Mint on the top of the list.
I had it running that way, then Linux mint stopped sounds, while ubuntu studio and windows 7 had sound, I did everthing on told to do on lunux mint forun and it still did not work so I deleted the drive partition It sat on and then reistalled it from a DVD.  Then when I restarted my computer, it would boot into Grub, it showed a grub and a line to enter what to tell it to do.

---

### Post by freddy58 on 2019-09-29
I want to put both ISO files on the same hard drive and I want to install Linux mint second, so grub puts Linux Mint on the top of the list

---

### Post by ajgreeny on 2019-09-29
So can you now boot anything on the computer or is is simply stalling at the grub> prompt?

Without more info about your computer and the current situation of OSs on the hard disk it is impossible to give you many details, so I suggest you boot to your DVD live version and go to **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script from the live OS

**Do not run the default repair** but simply copy back here the pastebin link you get which will show us a lot more about your system.

---

### Post by #&amp;thj^% on 2019-09-29
> **freddy58 said:**
> I want to put both ISO files on the same hard drive and I want to install Linux mint second, so grub puts Linux Mint on the top of the list.


If the repair dose not work try the below.
Here is five tools to look at: [https://www.linuxbabe.com/apps/create-multiboot-usb-linux-windows-iso](https://www.linuxbabe.com/apps/create-multiboot-usb-linux-windows-iso)

**BTW: You can also change the grub default boot entry from the command line without having to install any additional tool.** This won't change the order in the list but it will allow a different OS to boot by default, 
```
sudo cp /etc/default/grub /etc/default/grub.bak
```
Then edit the file using nano or the text editor of your choice:
```

sudoedit  /etc/default/grub
```

Find the line that contains
```

GRUB_DEFAULT=0
```

and set it to
```

GRUB_DEFAULT=xxx
```

where xxx is the index of grub menu item to which you would like to boot to by default. 

You can also chose the default by the name instead of index, e.g.:
```

GRUB_DEFAULT='Ubuntu'
```

if there was a menuentry 'Ubuntu' line on /boot/grub/grub.cfg. This may be a better method, as it does not depend on the order of the entries, which could change.

To use a kernel in the "Previous Linux Versions" sub-menu use:
```

GRUB_DEFAULT="Previous Linux Versions>x"
```

(make sure to include the quotations), where x is the index of the old kernel on the sub-menu, or the name of the kernel as it appears in /boot/grub/grub.cfg. For example,
```

GRUB_DEFAULT="Previous Linux Versions>4.13.0-43-generic"
```

Then update grub menu:
```

sudo update-grub
```

---

### Post by freddy58 on 2019-09-29
I did get Start up to write the ISO of 2 operating systems written the USB Thumb Drive.  I have already installed Ubuntu Studio, and I am writing to the Thumb drive as I type this, Linux Mint gets installed next

---

### Post by freddy58 on 2019-09-29
Installing Linux mint on the same hard drive as I type this

---

### Post by jeremy31 on 2019-09-29
The problem with having Ubuntu and Mint as dual boot is that you download the same updates twice on the same computer

---

