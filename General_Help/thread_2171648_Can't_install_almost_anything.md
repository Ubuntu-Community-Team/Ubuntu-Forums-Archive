---
title: "Can't install almost anything"
date: 2013-08-31
forum: General Help
---

### Post by Errandir on 2013-08-31
I recently downloaded xubuntu onto a very old laptop (Dell Latitude 100L) that was lying around in my house. The livecd worked fine, and I had no problem with installation. Most of the system (browsing with firefox, abiword, terminal stuff) works fine.

The problem is that when I try to install almost any significant program, it ends up cutting to a black screen with a long error message and I have to hard reboot to get the computer running again. It's the same error regardless of what I'm trying to do (I've triggered it trying to install chromium, network card drivers, gmusicbrowser packages, and a few other things). 

Commands to install less significant packages (such as "sudo apt-get install pacman") result in "E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem" - and running that command gets me the black screen error again.

Can anyone explain what's going on and whether it can be fixed? [This]("http://i.imgur.com/yggfO7y.jpg") is the long error message I've been getting. If there's any other information I should add, let me know.

---

### Post by ibjsb4 on 2013-08-31
```
sudo apt-get -f install
```

Get any clues from that?

---

### Post by 3rdalbum on 2013-09-01
Ouch. Looks like a kernel panic.

When you're installing software, there are primarily three parts of the computer at play:

1. Hard disk, which you are unpacking the software to
2. RAM, where the software is being held while decompressing
3. CPU, which is handling the decompressing

Either of these things could be the problem.

1. The hard disk could have lots of bad sectors, causing a cascade of failures leading to the kernel panic each time. As you probably don't have the right tools installed on your system to check for them, and installing them would cause a crash, you can boot the Xubuntu live CD and install the "Disk Utility" package. Use it to check the SMART statistics for the hard disk. If it shows a value of 50 or more for Read Errors or Write Errors, then your disk is dying.

2. The RAM could be bad. Running Memtest86+ from the GRUB menu, and running it overnight, might show if you have bad RAM. Otherwise, you can try taking out one RAM stick and seeing if the problem still occurs, and if it's still a problem, put that stick back and take out the other stick. If you could install software, you could run the memory benchmark from Phoronix Test Suite (which will fairly reliably crash a computer with bad RAM) but installing software is not an option.

3. The CPU might be overheating or undervolting while it works to decompress the packages. Try playing a Flash-based game or watching a movie - if these things work fine, then it's probably not the CPU at fault. If the CPU is overheating, you may need to remove dust from the fans and heatsinks inside the computer. If the CPU is undervolting, it's the power supply that's not getting enough juice to the CPU... not much you can do on a laptop unfortunately. Since it's an old laptop, and power supplies slowly lose their capacity over time, this may be the problem.

---

### Post by Errandir on 2013-09-01
ibjsb4: Running "sudo apt-get -f install" returns the same message as before about dpkg being interrupted.

3rdalbum: Really helpful post, thank you! I can't run the tests you suggested immediately, but it's very likely a hard drive problem. I had forgotten, but when I initially wiped the hard drive to install xubuntu, gparted had a red triangle with an exclamation point by the main partition (indicating bad sectors, I think) and was refusing to shrink it. I reformatted the partition and assumed that had solved the problem, because installation was fine afterward - but apparently not.

I'll still try to run the disk utility (I need to get my livecd back from a friend first), but if that actually is the problem, is there any fix short of replacing the hard drive? (I imagine not, but might as well ask, I guess.) And is it safe to continue using the laptop with the functionality it has now, or will the disk likely continue to deteriorate and lose any data stored on it?

---

### Post by protoss96 on 2013-09-03
Whole lotta binary code, best and safest way is to backup your files to a flash drive, and reinstall Ubuntu, you can backup files by booting ubuntu from cd.

---

