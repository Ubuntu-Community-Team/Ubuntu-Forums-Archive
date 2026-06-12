---
title: "RDP to Windows Server"
date: 2014-08-11
forum: General Help
---

### Post by wikedawsum on 2014-08-11
Please excuse me if this is not the correct forum. I'm having some issues with remote desktop from a Xubuntu machine to Windows Server 2003. My connection works fine, I'm able to access the server and everything functions correctly. The problem is the screen refresh rate. Every time I click anything the screen has to refresh all text and images. I've tried this using freerdp, rdesktop, and even 2x client. When using Remmina, I don't have this issue, but I am unable to use Remmina in my environment (unless anyone can tell me how to forward serial ports using Remmina?). I've included a link to a short video showing the issue. I've tried different configurations of freerdp/rdesktop/2x client, but cannot get past this issue. Is there something I need to configure server side? I've Googled all I can with no results. Hoping someone here can lend a hand.

[https://www.dropbox.com/s/udra7wxt7hj35wa/20140811_124148.mp4](https://www.dropbox.com/s/udra7wxt7hj35wa/20140811_124148.mp4)

Thanks in advance for the help!

---

### Post by MartyBuntu on 2014-08-11
Would you consider switching to TeamViewer?

---

### Post by wikedawsum on 2014-08-11
I'm certainly not opposed to it as I have used it before. My only concern is that I am hoping to use Xubuntu on serveral desktops for a business and don't want to incur any costs for using TeamViewer. That's also one of the reasons I need to be able to forward the serial port. We use signature capture devices. They are working great.. it's just that screen refresh that's the issue.

---

### Post by wikedawsum on 2014-08-12
[FONT=arial][SIZE=2]I have installed and tested FreeRDP on two virtual machines as well as an old laptop and have not had any issues with performance. Now, I'm wondering if my problem is hardware related. Below are the specs of the computers having the issue. They are all identical machines.

CPU: AMD 5150 1.6GHz Quad-Core Kabini (AMD Radeon HD 8400 Graphics)
MOTHERBORAD: ASUS AM1I-A Mini-ITX
MEMORY: G-Skill RipJaws Series 4GB DDR3-1333
STORAGE: Kingston SSDNow V300 Series

[/SIZE][/FONT]

---

### Post by wikedawsum on 2014-08-12
In case anyone runs across this in the future.. the solution was to install the proprietary AMD graphics driver. I was using the open source driver, but after installing AMD drivers the issue has disappeared.

---

