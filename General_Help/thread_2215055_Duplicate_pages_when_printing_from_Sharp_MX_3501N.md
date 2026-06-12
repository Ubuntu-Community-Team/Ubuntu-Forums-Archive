---
title: "Duplicate pages when printing from Sharp MX 3501N"
date: 2014-04-04
forum: General Help
---

### Post by Luis_Rivas on 2014-04-04
Hello Ubuntu Friends,

I'm having an issue utilizing the Sharp MX 3510N printer. It seems like it's printing duplicate pages every time I print.

Printer Driver: PXLCOLOR.PPD
Make and Model: Sharp MX 3501N Foomatic/pxlcolor (recommended)
Printer: Sharp-MX-3501N

Any help would be greatly appreciated!

Thanks,

Luis

---

### Post by bapoumba on 2014-04-05
Would you have configured or changed settings for your browser from the cups web interface ? [http://localhost:631](http://localhost:631)

---

### Post by Luis_Rivas on 2014-04-07
I didn't touch the CUPS we interface [http://localhost:631](http://localhost:631). However, I could verify what the configuration is? Would you like me to see and post? Not sure exactly what Cups web interface does really. 

Thanks for your help!

---

### Post by bapoumba on 2014-04-07
CUPS is at the interface between your applications and your printer. In the Administration tab, you can see your printer and the printing configuration file. I thought that maybe you had defined there that each printing job had to be done in duplicate. In that case, check your printer settings from System Tools > Printers or from the application you are using.

---

### Post by Luis_Rivas on 2014-04-07
The copies are already set to 1. When I print a Self Test Page it prints duplicates too. Don't see why this keeps happening. No other driver really works and sharp doesn't support Ubuntu :(

Do I have any other alternatives? I really appreciate your help!

---

### Post by bapoumba on 2014-04-07
Well, I guess I'll have to search further how to do this. Please have a look here :[https://www.openprinting.org/driver/Postscript-Sharp/](https://www.openprinting.org/driver/Postscript-Sharp/) and here : [https://www.openprinting.org/printer/Sharp/Sharp-MX-3501N_PS](https://www.openprinting.org/printer/Sharp/Sharp-MX-3501N_PS)

I year or so ago, I got a big network Xerox copier/printer to work at my univ by setting up the PPD file for it on my ubuntu laptop. I do not recall how I did it, because I had read a lot of different things and finally one worked (I think I got it from an Apple site and adapted to ubuntu).

---

### Post by Luis_Rivas on 2014-04-09
When I do a "Print Self-Test Page", it prints two (2) copies that say the following:

%!
userdict dup (\004) cvn{}put (\004\004) cvn{}put

%%%%If you can read this, you are using the wrong driver for your printer.%%%%

I tried doing the post script drivers but I need administrator privileges to the printer. Is that really necessary? Or do I just have to make changes to the client side and not printer?

I really appreciate your help!

Luis

---

### Post by bapoumba on 2014-04-09
[http://ubuntuforums.org/showthread.php?t=341621&page=79](http://ubuntuforums.org/showthread.php?t=341621&page=79)
It is suggested there reinstalling cups got this message cleared up.

What do you mean by "I need admin privilege to the printer" ?
Which ubuntu release are you using ?

Here is a related bu with HP printer that shows the error you get is related, as said in the error message, to the printer driver :  [https://bugs.launchpad.net/hplip/+bug/1000923](https://bugs.launchpad.net/hplip/+bug/1000923)

Going back to the openprinting page, I found another one maybe better related to your own printer : [https://www.openprinting.org/printer/Sharp/Sharp-MX-3501N](https://www.openprinting.org/printer/Sharp/Sharp-MX-3501N)
Sorry I cannot test this :)

---

### Post by Luis_Rivas on 2014-04-09
I'm using Ubuntu 12.04 LTS.

I believe the printer needs a Post Script Key in order to enable the post script capability. But this will cost money..

I ran the following command and issue remains: 
sudo dpkg-reconfigure cups

:(

---

### Post by bapoumba on 2014-04-09
> **Luis_Rivas said:**
> I'm using Ubuntu 12.04 LTS.

I believe the printer needs a Post Script Key in order to enable the post script capability. But this will cost money..

I ran the following command and issue remains: 
sudo dpkg-reconfigure cups

:(
Ah..

---

