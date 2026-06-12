---
title: "Urgent Help!!"
date: 2014-05-16
forum: General Help
---

### Post by w_Tran on 2014-05-16
Hello Ubuntu community,

I need some serious urgent help right now. I was originally using windows and I was trying to get ubuntu to work. So what happen was I went through a long process to try to get boot manager to work for ubuntu and I came across a software called EasyBCD. I was using EasyBCD to try to get windows 8,1 and ubuntu to load on my boot manager screen. This did not work so i decided to uninstall easyBCD manager. But uninstalling did not get rid of my boot loader screen for Windows, so I decided to reinstall EasyBCD and manually take off WINDOWS 8,1 on the boot loader screen. And I have never felt so stupid. because I did this I can not even go back to Windows 8,1 anymore. I really need help, all my files are saved in windows 8.1. The only access I have right now is on ubuntu through USB. 

Please someone, tell me a way where I can use Ubuntu Linux and still access EasyBCD (Windows) and somehow bring back my desktop to load Windows. I have all access to my hard drive I just cannot open any windows file right now.

---

### Post by dragonfly41 on 2014-05-16
If you can launch Ubuntu from USB then you could try installing boot-repair from Ubuntu Software Centre and run this to look for Windows and Ubuntu. There is a lot of information on boot-repair in various threads in this forum.

You can also post to this forum the url which boot-repair creates.

---

### Post by LastDino on 2014-05-16
Judging by you've W8.1, you seem to be having UEFI. Is that system new? 
If it is, have you turned off secure boot and power save in your BIOS? If you haven't, please do it. 
Then insert the Ubuntu live usb and as dragon mentioned, try to do boot repair or install grub from it, whichever suits you.

---

