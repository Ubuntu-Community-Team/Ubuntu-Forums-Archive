---
title: "Performance Issues With Libreoffice"
date: 2016-08-10
forum: General Help
---

### Post by texpat on 2016-08-10
Hi and thanks for reading,

I'm experiencing serious performance issues with Libreoffice, especially with Calc. Even with very basic spreadsheets, no diagrams or graphics, things slow down so as to make the program unusable. This is a recent problem: I've been using LO for years on this computer without a problem.

When I run [FONT=Courier New]**top**[/FONT] I see [FONT=Courier New]**Xorg**[/FONT] going up to 99% when I begin to scroll the page or switch tabs in Calc. LO Writer also slows down, but not as much.

The "About" dialogue gives the following information:
Version: 5.1.5.2
Build ID: 1:5.1.5~rc2-0ubuntu1~trusty1
CPU Threads: 4; OS Version: Linux 3.16; UI Render: default; 
Locale: de-DE (en_GB.UTF-8); Calc: group

I'm on Xubuntu 14.04.4 LTS

lshw -c video reports:
```
*-display               
       description: VGA compatible controller
       product: GT218 [GeForce 210]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:45 memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f7000000-f707ffff
```

Any hints greatly appreciated!
Tx

---

### Post by ajgreeny on 2016-08-10
It looks as if you are already using the nvidia driver (from Additional Drivers?) for that card, so I am a bit surprised that you have problems with xorg using such huge cpu resources, but have you tried using the open-source nouveau driver instead, or looked for alternative drivers in Additional Drivers?

It certainly sounds like a graphics or driver problem, but I admit I have no experience with nvidia cards or drivers so could be wrong.

Could [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1001550](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1001550) be of any help to you; I have read it but have never heard of "marching ants" so I'm not sure what is meant by that term.

---

### Post by vasa1 on 2016-08-10
> **ajgreeny said:**
> ... I have read it but have never heard of "marching ants" so I'm not sure what is meant by that term.
When you copy cell or cells in Calc there's a different type of border --- dashes of black and white give the impression, to someone with an active imagination, of ants marching along. I too have read about that being the cause of high cpu usage but OP can easily test that.

I attached a small video of the ants as a compressed mp4 file.

---

### Post by vasa1 on 2016-08-10
Do you have *libreoffice-gnome* or *libreoffice-gtk* or *libreoffice-gtk3* installed? These packages are meant to integrate LibreOffice with your desktop environment. But I've seen claims that *removing* these packages eases CPU issues.

And what version of gtk3 do you have? The output of```
dpkg -l libgtk-3-0
```will provide that information.

---

### Post by ajgreeny on 2016-08-10
> **vasa1 said:**
> When you copy cell or cells in Calc there's a different type of border --- dashes of black and white give the impression, to someone with an active imagination, of ants marching along. I too have read about that being the cause of high cpu usage but OP can easily test that.

I attached a small video of the ants as a compressed mp4 file.
Aah!

Thanks vasa1.  I've seen this, of course, but didn't associate it with "marching ants".  Obviously I do not have such an active imagination as some people, but then in UK we don't see ants marching like that very often.

---

### Post by texpat on 2016-08-11
Hi guys and thanks for this hint. I tried this out and its definitely not a marching ants issue.
When I open my spreadsheet, Xorg will go to 100% and it takes up to 10 seconds to draw the screen. Scrolling in any direction, either by cursor or using the scroll bars causes the same problem.
This is also true for the LO starting page where it presents you with thumbnails of recent documents. Navigating that page also causes Xorg to go through the roof.

[FONT=Courier New]**dpkg -l libgtk-3-0**[/FONT] returns
```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                        Version            Architecture       Description
+++-===========================-==================-==================-===========================================================
ii  libgtk-3-0:amd64            3.10.8-0ubuntu1.6  amd64              GTK+ graphical user interface library

```
Not sure what that means though.

---

### Post by texpat on 2016-08-11
Today a new version of Libreoffice was installed.

"About" now reads:

Version: 5.2.0.4
Build ID: 1:5.2.0~rc4-0ubuntu1~trusty2
CPU Threads: 4; OS Version: Linux 3.16; UI Render: default; 
Locale: de-DE (en_GB.UTF-8)

The problem, however, remains.

Other stuff I tried (as per launchpad bug report mentioned above):

In Tools -> Options -> View

Toggled "Use hardware acceleration": no improvement
Toggled "Use antialiasing": no improvement
Toggled "Use OpenGL": LO crashes on start

---

### Post by vasa1 on 2016-08-11
> **texpat said:**
> ...
[FONT=Courier New]**dpkg -l libgtk-3-0**[/FONT] returns
... 3.10 ...
Not sure what that means though.
That means that you're using the gtk2 mode. On my oldish laptop, running LibreOffice in gtk3 mode is more resource-hungry. So your problem doesn't lie there.

---

### Post by texpat on 2016-09-05
OK, so after fartassing around for a week or two I decided to uninstall LibreOffice and reinstall. Problem solved, which is more important right now than knowing exactly what went wrong in the first place.

Note that this is on my 14.04 LTS installation of xubuntu, so nothing to do with another thread of mine concerning 16.04.

Thanks for all who read and tried to help :-)

Tx

---

