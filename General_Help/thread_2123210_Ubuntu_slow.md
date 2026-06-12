---
title: "Ubuntu slow"
date: 2013-03-07
forum: General Help
---

### Post by lumaja on 2013-03-07
This happens some times when I am in Firefox and doing something in Libreoffice computer slows
down  after a while the page where I am greys up the Hard Disk led keeps flashing meaning
hard disk action, stays on these conditions until restart computer. Other times just going Dash Home and open an application takes long time, an window opens with “Sorry, Ubuntu 12.04 has experienced an internal error”
Thinking what could be the fault and has I have Clamtk I decide to scan, on the end got an long report
wish as 57 files all infected with PUA.win32 (this is for Windows) Windows with Virtualbox only, the report has Quarantine and Delete, dint click nothing but try to copy as usual but cant be copied, so I decide to ask for help, I think this is the reason for Ubuntu problem. What should I do to clean this files and computer?
Thank you

---

### Post by prismctg on 2013-03-07
I am not sure about your problem , but clam antivirus gives lots of false alerm .....  :) , I had some performance issue using firefox ... i just activated default theme then my problem solved :)

---

### Post by philinux on 2013-03-07
> **lumaja said:**
> This happens some times when I am in Firefox and doing something in Libreoffice computer slows
down  after a while the page where I am greys up the Hard Disk led keeps flashing meaning
hard disk action, stays on these conditions until restart computer. Other times just going Dash Home and open an application takes long time, an window opens with “Sorry, Ubuntu 12.04 has experienced an internal error”
Thinking what could be the fault and has I have Clamtk I decide to scan, on the end got an long report
wish as 57 files all infected with PUA.win32 (this is for Windows) Windows with Virtualbox only, the report has Quarantine and Delete, dint click nothing but try to copy as usual but cant be copied, so I decide to ask for help, I think this is the reason for Ubuntu problem. What should I do to clean this files and computer?
Thank you

What are the machines specifications?

---

### Post by lumaja on 2013-03-08
[SIZE=4]**Mother board**[/SIZE]
 [SIZE=3]Gygabyte G41M-Combo[/SIZE]
 [SIZE=4]**Ubuntu**[/SIZE]
 Release 12.04 (precise) 32-bit
 Kernel Linux 3.2.0-38-generic-pae
 GNOME 3.4.2
 [SIZE=4]**Hardware**[/SIZE]
 Memory: 966.4 MiB
 Processor: Pentium(R) Dual-Core CPU E5400 @ 2.70GHz x 2
 [SIZE=4]**System Status**[/SIZE]
 Available disk space: 143.1 GIB
 

 Summary of infected files:
 In Directory My Videos
 Few in My Pictures
 Few in Cannon (my camera instructions fies)
 Few in directory IMPORT BANK (this must be a very bad one)
 One in directory Home/Windows Data/kyo.zip (not unzipped)  
 One mozilla/firefox/--------/chrome/forecasfox.jar
 Penty in clamav-0.97.6/test/------------------/clam-exe. (others)
 

 Plenty From PENDRIVE
 

 My worry is the first group, the kyo.zip I can delete it Windows game for my wife
 but the rest are quite important  I ask again how to clean this from hard disk. This is
 one of the very top reasons I gave up Windows, after I read much how good Ubuntu
 is about this subject, I am on the some boat.  
 I receive notification having 29 files Update Ubuntu, must I carry-on with this update
 with all this virus?
 I appreciate if some could supply this answers.
 Thank you

---

### Post by c2tarun on 2013-03-08
> **lumaja said:**
> [SIZE=4]**Mother board**[/SIZE]
 [SIZE=3]Gygabyte G41M-Combo[/SIZE]
 [SIZE=4]**Ubuntu**[/SIZE]
 Release 12.04 (precise) 32-bit
 Kernel Linux 3.2.0-38-generic-pae
 GNOME 3.4.2
 [SIZE=4]**Hardware**[/SIZE]
 Memory: 966.4 MiB
 Processor: Pentium(R) Dual-Core CPU E5400 @ 2.70GHz x 2
 [SIZE=4]**System Status**[/SIZE]
 Available disk space: 143.1 GIB
 

 Summary of infected files:
 In Directory My Videos
 Few in My Pictures
 Few in Cannon (my camera instructions fies)
 Few in directory IMPORT BANK (this must be a very bad one)
 One in directory Home/Windows Data/kyo.zip (not unzipped)  
 One mozilla/firefox/--------/chrome/forecasfox.jar
 Penty in clamav-0.97.6/test/------------------/clam-exe. (others)
 

 Plenty From PENDRIVE
 

 My worry is the first group, the kyo.zip I can delete it Windows game for my wife
 but the rest are quite important  I ask again how to clean this from hard disk. This is
 one of the very top reasons I gave up Windows, after I read much how good Ubuntu
 is about this subject, I am on the some boat.  
 I receive notification having 29 files Update Ubuntu, must I carry-on with this update
 with all this virus?
 I appreciate if some could supply this answers.
 Thank you

I don't think virus in windows files will have any affect on Ubuntu (can anyone please confirm this)

According to [this]("https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop") wiki page, your system requirements are fine, but even with 3GB RAM I feel lag while using Unity 3D. Since your RAM is pretty low, I'll suggest you to try Ubuntu 2D (you can choose it before entering password on Login Screen).

If you still feel lag and slow system, try installing XFCE4 and LXDE as your desktop environments, you'll surely see some improvements. (try XFCE4 first)

Also Please don't install lubuntu-desktop or xubuntu-desktop instead of LXDE and XFCE4.
Please install plain-vanilla lxde and xfce4
To install LXDE:
```
sudo apt-get install lxde
```

To install xfce4:
```
sudo apt-get install xfce4
```

---

### Post by mastablasta on 2013-03-08
what graphics card/chip do you have?
```
lspci | grep VGA
```

---

### Post by lumaja on 2013-03-10
-G41M-Combo:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)

Should I install the waiting Ubuntu update?
Thank you

---

### Post by 3rdalbum on 2013-03-10
> **lumaja said:**
> -G41M-Combo:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)

Should I install the waiting Ubuntu update?
Thank you

Yes, it can't hurt.

Also, you do not have a virus on Ubuntu. Maybe on Windows, but it won't affect Ubuntu. Also, viruses rarely cause slowdown even on Windows.

Have you checked the SMART statistics for your hard disk? Open the Disk Utility program and click on your disk, then click SMART Data. Any little red lights indicate a problem.

If there's no problems reported there, you could try running IOtop. In the terminal, type:

```
sudo apt-get install iotop
sudo iotop
```

When you start having the problems where the disk is being used a lot and the windows go grey, have a look at the window where IOtop is running, and see if there's a program consistently at the top of the list DURING THE PROBLEM. If there is, then please let us know what it is.

To quit IOtop, press Q or close that window.

You could also run Memtest from the GRUB boot menu to check your RAM. Run it for eight hours. If there are any errors, any errors at all, you have bad RAM that may be causing the problem.

---

### Post by Laobi on 2013-03-10
Since you have just 1GB of RAM, it could also be that the system starts to use swap a lot, especially when you run such memory hungry applications as Firefox and LibreOffice at the same time.

Try running this in terminal **when your system begins to slow down** to see how much memory is used and if it uses swap:
```
free -m
```

---

### Post by lumaja on 2013-03-11
Thank you 3rdalbum and Laobi for your responses.
 To 3rdalbum
 I did checked SMART immediately and the results are:
 Self Assessment: Passed
 Self-tests: Completed OK
 Power cycles: 3012
 Bad Sectors: (Green) Disk is healthy.
 The list compromise of:
 Some with green, others with black N/A.
 I got more adventure and Run Self-test
 Choose Short (default)
 After starting to run it stopped with red X Cancel Self-test
 I dint install iotop yet first send this to you.
 To I will free -m after this, another clever idea.
 

 **Again Thank you very munch.  **

---

### Post by mastablasta on 2013-03-11
it seems disk is having issues.

but usually there are always some bad sectors. 

try also the other tow. the GPU is not something strong while unity runs in 3D. so it may be slowing it all down.

---

### Post by 3rdalbum on 2013-03-11
As long as there are no red lights in the SMART data, we can rule out the disk being the problem.

The other suggestion given about free -m is good, give it a try as well as IOtop.

---

