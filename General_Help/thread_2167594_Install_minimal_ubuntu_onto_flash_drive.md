---
title: "Install minimal ubuntu onto flash drive"
date: 2013-08-14
forum: General Help
---

### Post by chrissound on 2013-08-14
Hi there how do I go about doing this?

I'd like to install a minimal ubuntu (using the net installer) onto a flash drive. I'd like to run the ubuntu installation from the flash drive. 

According to this site it is possible using Remastersys. I was wondering if theres an easier way/more direct way?
[http://andyduffell.com/techblog/?p=361](http://andyduffell.com/techblog/?p=361)
> 

[LIST=1]
[*]The Minmal CD image is a 10MB download (!) that can boot you up into  the installer. From there you can choose one of a whole slew of  different types of system to install, from servers to the regular KDE or  Gnome desktops. What we want to install though, is the basic command  line system.
[*]From there, use the command line to add packages until you get the system you want.  To do this really easily, you can use my [Perfectminimal script]("http://andyduffell.com/techblog/?p=689").
[*]If you don’t want to use the script a good suggested list of packages for a fairly minimal Gnome desktop is:
[*]The dependencies from these packages will cascade down and install a  very minimal Gnome system that punches well above it’s weight.
[*]Enjoy!
[/LIST]

If you want to put this on a USB stick, then you can install [Remastersys]("http://www.geekconnection.org/remastersys/remastersystool.html").  Run Remastersys in backup mode and it’ll generate an .iso of your  customised minimal system, which you can then feed to Ubuntu’s regular  “USB startup disk creator”, or the cross-platform LiveUSB creator [Unetbootin]("http://unetbootin.sourceforge.net/").
 If you use the former to create a “persistent” LiveUSB you can  allocate a couple of hundred MB for persistence on even a 2GB USB stick.  That’s enough room to store files, perform updates, install new  software, and generally do everything on a USB stick that you’d do on a  hard drive.



---

### Post by ibjsb4 on 2013-08-15
> The Minmal CD image is a 10MB download 

Its more like 30M unless your loading something old and not supported.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

