---
title: "Virtual Desktop"
date: 2007-03-18
forum: General Help
---

### Post by Astral Abraxas on 2007-03-18
I would like to run windows through a program on ubuntu. I have seen this a couple times, and was wondering if vmware is what I am looking for?

Also do I load windows from a seperate partition and the stuff I do through the program writes changes to that partition?

---

### Post by derjames on 2007-03-18
VMware lets you create virtual machines. The Virtual MAchine emulates all the devices of a 'real' PC. In particular the hard drive is a simple file which lies in a folder somewhere in the directory structure of the host machine. The guest operating system is installed into this file (*.vmx for vmware) and vmware takes care to translate whatever happens in this 'virtual' drive comunicating it to the outer world. This is very convenient since you don't have to install the operating system in a separate partition and both operating systems live happily in a single session... even copy and paste between the machines is possible....

Dual boot requires you to install the second operating system in a different partition which you can select later at boot time.... with dual boot only one operating system can be loaded at a time... with a virtual machine you can load multiple operating systems at the same time...

hope this helps

---

### Post by Astral Abraxas on 2007-03-18
Yes, but I am already dual booted lol, and I would like to run that information on here... is it possible?

---

### Post by llamakc on 2007-03-18
What does "run that information on here" mean? Please be specific.

---

### Post by jimbob on 2007-03-18
I haven't tried this but it is possible to make a virtual machine (VM) from your existing XP installation.

Here is the link if you want to try it:

     [http://www.howtoforge.org/vmware_converter_windows_linux](http://www.howtoforge.org/vmware_converter_windows_linux)
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by derjames on 2007-03-18
if you are on WIndows you need to install the appropriate drivers to 'see' the Linux Partition
if you are on Linux you can see the Windows partition provided you mount it - simply use the mount command to have access to the windows partition...

---

### Post by Astral Abraxas on 2007-03-18
Thank you, I will follow that guide, and I already have my windows partitions mounted. I primarily run on ubuntu ^_^.

---

### Post by Astral Abraxas on 2007-03-18
Um... thats a tutorial for people running on windows x.x... Do I use VMConverter on windows to convert windows into a virtual machine?

---

### Post by jimbob on 2007-03-18
Like I say, I haven't tried it but that is the general idea I believe - make a VM out of your existing XP installation and move it to Ubuntu to be run under Linux.

I took the opposite tack and actually made a fresh install of XP as a virtual machine so that it went right on the Ubuntu disk.  Works great.

Let me know if the other way works if you have success.

EDIT:  Look at this other thread also: [http://www.ubuntuforums.org/showthread.php?t=381940](http://www.ubuntuforums.org/showthread.php?t=381940)
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

