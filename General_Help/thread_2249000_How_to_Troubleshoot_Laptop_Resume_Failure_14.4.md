---
title: "How to Troubleshoot Laptop Resume Failure 14.4"
date: 2014-10-18
forum: General Help
---

### Post by 7-webmaster on 2014-10-18
I have posted this before but received no answers, so I repeat the question.

About 25% of the time when I open the lid of my laptop running Ubuntu  14.4 the system does not resume.  It just sits there with the screen  blank, the keyboard dead, and no disk activity.  The only way out is to  power off and back on again which, of course, wipes out everything I was  working on when I closed the lid.  When the system resumes Ubuntu  reports EIGHT crashes, which I diligently transmit, hoping for some  improvement in resume support.  The system has been doing this since I  bought it, and the problem has not changed in behavior since 12.4.

Since the screen and keyboard do not work and the laptop is not  listening to the network how can I troubleshoot this problem?  I cannot  go to the OEM because the system is only supported for Windoze.  When I  look at the dmesg output after the reboot it starts with the reboot,  with no knowledge of what happened before, which is of course  understandable since the memory was cleared by the power off.

---

### Post by Bucky Ball on 2014-11-02
'Bump'

... which takes it back to the top of the new posts search list.

Feel free to link to any of your closed threads which may have useful info.

Please open a terminal and post the output of:

```
lspci
```

... and the make and model of your machine.

Absolutely nothing happens when you hit ctl+alt+F1? I'll do some digging.

---

### Post by Bucky Ball on 2014-11-02
This is a known bug and it appears the fix will be in the 3.15 or 3.16 kernel. See [HERE]("https://bugzilla.kernel.org/show_bug.cgi?id=76761#c10").

In the meantime, there is a workaround [HERE]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1283938"):
> 
WORK-AROUND

- Installing the "fglrx" proprietary package.

In other words, boot the machine, install fglrx from software centre or:

```
sudo apt-get install fglrx
```

... reboot, when at a desktop close lid, open it again. Did it work?

Also, how big is your RAM? You are going into suspend and not hibernate?

* And yet another suggestion from [HERE]("http://www.linuxforums.org/forum/ubuntu-linux/201167-14-04-black-screen-after-suspend.html#post949234").

- Boot the recovery kernel (should be second on the grub list);
- When at the options choose 'Drop to root shell', drop to the shell;
- Then:
```

sudo apt-get remove lightdm
sudo apt-get install gdm
sudo reboot -h now
```

The machine will reboot and your login screen will look different. Ignore for now and we can change the login manager later. When at a desktop, close the lid, open it again. Could be a lightdm issue so we've uninstalled it and replaced with another, gdm. We can swap it back later if things go pear shaped.

---

### Post by 7-webmaster on 2014-11-11
> **Bucky Ball said:**
> This is a known bug and it appears the fix will be in the 3.15 or 3.16 kernel. See [HERE]("https://bugzilla.kernel.org/show_bug.cgi?id=76761#c10").

In the meantime, there is a workaround [HERE]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1283938"):


In other words, boot the machine, install fglrx from software centre or:

```
sudo apt-get install fglrx
```

... reboot, when at a desktop close lid, open it again. Did it work?


Also, how big is your RAM? You are going into suspend and not hibernate?

* And yet another suggestion from [HERE]("http://www.linuxforums.org/forum/ubuntu-linux/201167-14-04-black-screen-after-suspend.html#post949234").

- Boot the recovery kernel (should be second on the grub list);
- When at the options choose 'Drop to root shell', drop to the shell;
- Then:
```

sudo apt-get remove lightdm
sudo apt-get install gdm
sudo reboot -h now
```

The machine will reboot and your login screen will look different. Ignore for now and we can change the login manager later. When at a desktop, close the lid, open it again. Could be a lightdm issue so we've uninstalled it and replaced with another, gdm. We can swap it back later if things go pear shaped.

Thank you for responding.

uname:

3.13.0-39-generic

Since kernel 3.16 is already available in Utopic Unicorn I will try installing 14.10 to see if that improves things.

```
lspci:

00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] BeaverCreek [Radeon HD 6620G]
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] BeaverCreek HDMI Audio [Radeon HD 6500D and 6400G-6600G series]
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 12h Processor Root Port
00:06.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 12h Processor Root Port
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 03)
00:10.1 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 03)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 13)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD] FCH IDE Controller
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:14.7 SD Host controller: Advanced Micro Devices, Inc. [AMD] FCH SD Flash Controller
00:15.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE port 0)
00:15.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE port 1)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 7
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter (rev 01)
```

There are so many different symptoms.
[LIST]
[*]failure to suspend when the lid closes
[*]failure to resume far enough to activate the keyboard (so I can't even use Ctl-Alt-PSc commands)
[*]failure to start X (although Ctl-Alt-PSc REISUB works)
[/LIST]

I tried fglrx in both 12.04 and 13.04, and saw no improvement in  reliability, while the functionality of fglrx is poor compared to the  open-source driver.  Back in 12.04 the X-open driver was less reliable than fglrx, but is very much improved in 13.04, and has the enormous advantage of actually being supported.

I have 6GB RAM.  The system is definitely set to Suspend on close lid.

I can understand that the dumps I submit when I reboot may elucidate problems with resume, but I am not always offered that option.  From the lights on the laptop I can see that the system starts to resume, even reads from the HD, but sometimes it just stops dead before starting X.  It is slightly better in 14.04 than in previous releases:  the back-light is now reliably turned on to illuminate the LCDs, and the system only reports 3 crashes if X does get started as opposed to the 8 crashes on 13.04 and 13.10.  In other cases the system does not suspend when the lid is closed, leaving the system consuming power, driving down the battery, and generating heat, which potentially could burn out the system if I don't notice it before packing the system away in my backpack.  How can I collect information on the failure to suspend or the failure to resume when I have no GUI, no keyboard, and no external access to the system across the network?  If I have to power the system off and on to get access to the system so I can perform diagnosis, it seems to me that all of the information about what went wrong is lost.  Without information I cannot see how anybody can fix these problems.  That is why I have been asking for advice on how to collect information.

If the system gets as far as starting X the GUI always comes up, so I am reasonably confident this is not a window manager problem.

I have upgraded to 14.10, with the 3.16 kernel, and the problem persists.  When I restarted the system when the system did not resume there was no failure reported.  I therefore conclude that this is NOT the known problem with ATI graphics which is supposedly fixed in kernel 3.16.

So I repeat the request for information on how to collect documentation to understand why the system is not resuming.

---

### Post by nur4 on 2015-09-20
> **7-webmaster said:**
> Thank you for responding.

uname:

3.13.0-39-generic

Since kernel 3.16 is already available in Utopic Unicorn I will try installing 14.10 to see if that improves things.

lspci:

00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] BeaverCreek [Radeon HD 6620G]
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] BeaverCreek HDMI Audio [Radeon HD 6500D and 6400G-6600G series]
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 12h Processor Root Port
00:06.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 12h Processor Root Port
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 03)
00:10.1 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 03)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 13)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD] FCH IDE Controller
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:14.7 SD Host controller: Advanced Micro Devices, Inc. [AMD] FCH SD Flash Controller
00:15.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE port 0)
00:15.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE port 1)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 7
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter (rev 01)

There are so many different symptoms.
[LIST]
[*]failure to suspend when the lid closes 
[*]failure to resume far enough to activate the keyboard (so I can't even use Ctl-Alt-PSc commands) 
[*]failure to start X (although Ctl-Alt-PSc REISUB works) 
[/LIST]

I tried fglrx in both 12.04 and 13.04, and saw no improvement in  reliability, while the functionality of fglrx is poor compared to the  open-source driver.  Back in 12.04 the X-open driver was less reliable than fglrx, but is very much improved in 13.04, and has the enormous advantage of actually being supported.

I have 6GB RAM.  The system is definitely set to Suspend on close lid.

I can understand that the dumps I submit when I reboot may elucidate problems with resume, but I am not always offered that option.  From the lights on the laptop I can see that the system starts to resume, even reads from the HD, but sometimes it just stops dead before starting X.  It is slightly better in 14.04 than in previous releases:  the back-light is now reliably turned on to illuminate the LCDs, and the system only reports 3 crashes if X does get started as opposed to the 8 crashes on 13.04 and 13.10.  In other cases the system does not suspend when the lid is closed, leaving the system consuming power, driving down the battery, and generating heat, which potentially could burn out the system if I don't notice it before packing the system away in my backpack.  How can I collect information on the failure to suspend or the failure to resume when I have no GUI, no keyboard, and no external access to the system across the network?  If I have to power the system off and on to get access to the system so I can perform diagnosis, it seems to me that all of the information about what went wrong is lost.  Without information I cannot see how anybody can fix these problems.  That is why I have been asking for advice on how to collect information.

If the system gets as far as starting X the GUI always comes up, so I am reasonably confident this is not a window manager problem.

Thank you!
That fixed my problem of wireless not reconnecting and a clickpad freezing after a resume on Ubuntu 14.4.

---

