---
title: "VirtualBox: kernel driver not installed"
date: 2012-11-29
forum: General Help
---

### Post by asb3 on 2012-11-29
I'm running ubuntu 12.10.  I installed VirtualBox using the Ubuntu Software Center. I created a windows XP virtual machine, but when I tried to run it I got the error
 p, li { white-space: pre-wrap; }  Kernel driver not installed (rc=-1908)


  p, li { white-space: pre-wrap; }  The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

[COLOR=#0000ff]'/etc/init.d/vboxdrv setup'[/COLOR]

as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.


I executed 

> sudo /etc/init.d/vboxdrv setup
and I got the error
[COLOR=#0000ff][/COLOR]
sudo: /etc/init.d/vboxdrv: command not found


[COLOR=#0000ff][COLOR=Black]How do I install vboxdrv? I can't find it.
[/COLOR][/COLOR]
[COLOR=#0000ff][COLOR=Black][/COLOR]
[/COLOR]
[COLOR=#0000ff]
[/COLOR]

---

### Post by howefield on 2012-11-29
Do you have the headers to match your kernel install ?

---

### Post by Statia on 2012-11-29
[http://ubuntuforums.org/showthread.php?t=2055886](http://ubuntuforums.org/showthread.php?t=2055886)

---

### Post by asb3 on 2012-11-29
Following the suggestion on the thread 
[http://ubuntuforums.org/showthread.php?t=2055886](http://ubuntuforums.org/showthread.php?t=2055886)  
I tried

sb@cavu:~$ sudo dpkg-reconfigure virtualbox-dkms
[sudo] password for asb: 
Sorry, try again.
[sudo] password for asb: 

------------------------------
Deleting module version: 4.1.18
completely from the DKMS tree.
------------------------------
Done.
Loading new virtualbox-4.1.18 DKMS files...
Building only for 3.5.0-18-generic
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
 * Stopping VirtualBox kernel modules                                                                                                            [ OK ] 
 * Starting VirtualBox kernel modules                                                                                                                    * No suitable module for running kernel found

How do I install the kernel source?

---

### Post by Statia on 2012-12-03
[https://www.google.com/search?client=ubuntu&channel=fs&q=Ubuntu+install+kernel+source&ie=utf-8&oe=utf-8&redir_esc=&ei=Mnu8UKmCDOaj0QWTpoG4Dw](https://www.google.com/search?client=ubuntu&channel=fs&q=Ubuntu+install+kernel+source&ie=utf-8&oe=utf-8&redir_esc=&ei=Mnu8UKmCDOaj0QWTpoG4Dw)

---

### Post by SeijiSensei on 2012-12-03
[http://ubuntuforums.org/showthread.php?t=2090299](http://ubuntuforums.org/showthread.php?t=2090299)

---

### Post by asb3 on 2012-12-04
I installed the kernel headers using
sudo apt-get install linux-headers-$(uname -r)

and I was able to start Virtual box.

Thank you for your help.

Note to SeijiSensei:
Please have the courtesy to wait more than 5 hours before scolding someone for not checking responses and thanking helpers.

---

### Post by Adler on 2013-01-09
Hi All,

I'm trying to Virtualize MS 7. I've just gotten a new machine with a 128 GB SSD.

I've done this often in the past, but keep getting message errors with Oracle's VB box, that I
don't have the Kernel installed. 

Can someone run me through what I should do? BTW, I am running the lastest Linux Kernel. 

Thanks in advance for any responses.

---

### Post by CharlesA on 2013-01-09
Run this:

```
sudo /etc/init.d/vboxdrv setup
```

There is also a huge thread about it in the Virtualization forum.

---

### Post by Adler on 2013-01-09
CharlesA,

Thanks for the reply. I have done this several times, and never got the error messagesthat I have. I keep burning coasters if you know what I
mean. LOL!

I'll get back to you.

---

### Post by Adler on 2013-01-09
CharlesA,

That worked. THX.

---

