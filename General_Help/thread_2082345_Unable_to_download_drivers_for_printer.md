---
title: "Unable to download drivers for printer"
date: 2012-11-09
forum: General Help
---

### Post by Starsound on 2012-11-09
Hello,

I have Ubuntu 12.04. I am unable to download the drivers for my printer. I inserted the disc and nothing came up. (It just spun for a short while) As I wrote in another discussion, I have no online sound (although there is sound offline through my speakers) and no videos on some sites. I have adobe and updated my video drivers. I'm not very computer savvy. Does anyone know how to solve these problems?

Thank you

---

### Post by dharmeshhchauahn on 2012-11-09
First off all you must have to know which hardware you are used

 motherboard ? ( eg: intel model )

---

### Post by robert shearer on 2012-11-09
Usually in Ubuntu you simply plug your printer in and turn it on.
Ubuntu will then detect it and install the driver.
Your driver cd is not needed.Ubuntu will take care of the drivers.

Some printer manufacturers are not linux friendly and there may be additional steps needed.
If your printer is not automatically detected and setup then post back quoting any error messages and tell us the Make and Model of your printer.

For your Multimedia problems try installing 
ubuntu-restricted-extras either from the Ubuntu software centre or open a terminal (Ctrl+Alt+t) and enter..
```
sudo apt-get install ubuntu-restricted-extras
```
press 'enter'
It will ask for your password and when you type it **no letters will show on the screen**.(this is normal-your password is a password so should not be seen by anyone else looking at your screen :-)  )
press 'enter' again and the packages should begin to install.

(ubuntu-restricted-extras has the codecs you may be missing to play media files)
Post back if this does not solve the problem.

---

### Post by lightning slinger on 2012-11-09
>  Some printer manufacturers are not linux friendly and there may be additional steps needed.List of supported printers and manufacturer-specific installation is on this page!

[https://help.ubuntu.com/community/Printers](https://help.ubuntu.com/community/Printers)

---

### Post by Mark Phelps on 2012-11-09
> **Starsound said:**
> Hello,

I have Ubuntu 12.04. I am unable to download the drivers for my printer. I inserted the disc and nothing came up. (It just spun for a short while) 

If that's a CD that came with the printer, those are Windows drivers and will do you no good in Linux.

Take a look at the link that lightening slinger provided for info on Linux support for printers.

---

### Post by linuxcoffeelover on 2012-11-09
I wouldn't bother with windows drivers on Ubuntu you should go to the manufacturers website and look for a linux script or a tar with the ppd file for your printer.

thats what i had to dow for my 9 pin okidata

---

