---
title: "My printer is slow with Linux can I speed it up?"
date: 2008-01-10
forum: General Help
---

### Post by thenetduck on 2008-01-10
When I use my printer from my apple machine, paper prints much faster, but when I print off of my Linux machine, it's very very very slow printing. Does anyone know how to speed up the printer and make it print faster? 

Thanks 

P.S. using an Epson Stylus all in one printer 

The Net Duck

---

### Post by stchman on 2008-01-10
> **thenetduck said:**
> When I use my printer from my apple machine, paper prints much faster, but when I print off of my Linux machine, it's very very very slow printing. Does anyone know how to speed up the printer and make it print faster? 

Thanks 

P.S. using an Epson Stylus all in one printer 

The Net Duck

Can you give us an exact model number.  There are many Stylus printers.

---

### Post by kdwillia on 2008-01-10
The first thing you should check is the quality of the print.  Is it set on draft quality or on fine quality.

---

### Post by sleepingdragon on 2008-01-10
I had this problem initially with my Epson Stylus CX3600 All-In-One. Turned out to be a printing resolution problem; it was set too high. 

Depending on your menu layout (Gnome/KDE/XFCE/etc.), you will have to look in your System/Preferences/Settings menu for the CUPS printer settings, so to keep to a universal layout, try the CUPS server by using your web browser and going to 

**[http://localhost:631](http://localhost:631)**

You can use the "Set Printer Options" on that page to set the print resolution. It's usually set to "Automatic", but you can experiment with various settings, try 300dpi for plain text, 600dpi is OK for pictures. Anything above that is a luxury. The higher the resolution, the better it will look and the longer it will take to print. Also check the Print Quality is set to "Standard". Higher settings here will also slow down your printing. 

There are plenty of other options too, look out for the "Media Type" to ensure you're printing onto the right type of paper - it can save on those expensive ink costs!

These will be the default settings of the printer, so they will be the same for every print, unless specified within the "Print Options" of an application.

Hope all that helps. :)

---

### Post by thenetduck on 2008-01-11
> **sleepingdragon said:**
> I had this problem initially with my Epson Stylus CX3600 All-In-One. Turned out to be a printing resolution problem; it was set too high. 

Depending on your menu layout (Gnome/KDE/XFCE/etc.), you will have to look in your System/Preferences/Settings menu for the CUPS printer settings, so to keep to a universal layout, try the CUPS server by using your web browser and going to 

**[http://localhost:631](http://localhost:631)**

You can use the "Set Printer Options" on that page to set the print resolution. It's usually set to "Automatic", but you can experiment with various settings, try 300dpi for plain text, 600dpi is OK for pictures. Anything above that is a luxury. The higher the resolution, the better it will look and the longer it will take to print. Also check the Print Quality is set to "Standard". Higher settings here will also slow down your printing. 

There are plenty of other options too, look out for the "Media Type" to ensure you're printing onto the right type of paper - it can save on those expensive ink costs!

These will be the default settings of the printer, so they will be the same for every print, unless specified within the "Print Options" of an application.

Hope all that helps. :)

This was very helpful Thank you 

The net Duck

---

### Post by thenetduck on 2008-01-11
OH ti say says "Forbidden" I don't have access to change my printer settings. Anyone got a fix for that? 

The Net Duck

---

### Post by strabes on 2008-01-11
You'll need to log in using your ubuntu username and password.

---

### Post by sleepingdragon on 2008-01-12
Sorry, forgot to mention that! Yes, you'll need to log into CUPS to make changes. If you're using a normal user account on your computer that doesn't have admin rights (can't use sudo), then you might run into problems logging in.

You should check to see if you have installed *escputil* from the repos. This utility will allow you to clean the print heads and check for ink levels. Just use

*sudo apt-get install escputil*

on the command-line to install, it'll add itself to the printer settings on the locahost:631 pages.

---

### Post by cartisdm on 2008-02-20
I have that same page you posted a screenshot for but....I don't have a resolution option:( Now what?

---

### Post by thenetduck on 2008-02-20
I still can't  get pas the "Acess Forbidden" when I click the options. I tried login in as root and didn't work. Is there a way to do this? Thanks 

The Net Duck

---

### Post by sleepingdragon on 2008-05-12
add your username to the *admin* group (go to User and Group settings), you should then be able to alter the CUPS settings. As for the missing resolution problem is CUPS; sorry I can't help you with that. I've never seen that problem before!

---

