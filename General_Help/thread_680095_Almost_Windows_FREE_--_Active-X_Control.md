---
title: "Almost Windows FREE -- Active-X Control"
date: 2008-01-27
forum: General Help
---

### Post by glenna on 2008-01-27
OK -- Here's a good one (maybe not):

I need to have remote access to work....it is primarily an XP environment.  I am supposed to use IE to dial-in.  I have found that using Mozilla with user agent switcher seems to work (at least I can sign in).  To remote into my personal work computer, it says I need to install Active-X controller.  I believe this is an IE thing.  Any thoughts on how to get around this?

I believe this is my last issue to be Windows free!!!!  

Thanks, 

Glenn

---

### Post by Lord Illidan on 2008-01-27
I have no idea how to get Active-X working under Linux, but why not try VNC for remote access?

---

### Post by glenna on 2008-01-27
I don't know much about VNC...I will do some reading.  My work network is extremely secure with limited access.  I will let you know what I learn.

Thanks, 

Glenn

---

### Post by Matt Yun on 2008-01-27
You have several options.  The easiest might be to install [IEs4Linux,]("http://www.tatanka.com.br/ies4linux/page/Main_Page") which is a specialized WINE installation of Internet Explorer 6.  The IEs4Linux package automagically takes care of the WINE setup and configuration, and installs all of the necessary files for IE6.  However, there may be [issues with ActiveX]("http://www.gagme.com/greg/linux/activex-linux.php").

If IEs4Linux doesn't work with your ActiveX site, or you need Internet Explorer 7, probably the best option is to install WindowsXP in a virtual machine.  Both [VMWare]("https://help.ubuntu.com/community/VMware") and [VirtualBox]("https://help.ubuntu.com/community/VirtualBox") have packages available for Ubuntu.  Both virtualization products have great performance, and both enable internet access through the Linux host without any configuration from the user.  Internet Explorer 7 will run with ActiveX as if it were a native installation.  However, all virtualization software require that you own a copy of the WindowsXP setup CD.

---

### Post by glenna on 2008-01-27
Thanks for the help.  I tried to install IE (I have wine loaded)...following the instructions on the link...but I keep getting an error "error with cabextracting"

Glenn

---

