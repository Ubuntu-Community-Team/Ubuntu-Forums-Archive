---
title: "Network Printing in Gutsy"
date: 2007-10-22
forum: General Help
---

### Post by madcow72 on 2007-10-22
This is just documentation for how I got my network printer working in Gutsy using LPR.  I didn't have this problem in Feisty, but since Gutsy has the new Printer GUI going, I was having a hell of a time trying to add my networked printer.  

The Problem:  
Opening System -> Administration -> Printing  I choose New Printer and go through the dialog to add my network printer with the following settings as a LPD/LPR Printer:
Hostname:  192.168.0.5 (The static IP address to our print server)
Printername: lpt1  (The queue for the printer)
I choose the correct printer make and model and then get the request for a password for my username on "localhost".  Unfortunately, none of my passwords work.

The Solution:
Very simple.  I right click on the menu bar and choose "Edit Menus".  Navigate to Administration->Printing.  Right click, choose "Properties."  Add "gksu" in front of /usr/bin/system-config-printer so that it opens as root by default.  This allowed me to add my network printer using the settings described above.

I fully admit I may be doing something stupid.  But if anyone else has this same problem, this works!

---

### Post by Macchi on 2007-10-23
The solution that you propose works, but the actual source of the problem is in the user management module. Printer administration works only for the first user created for the system, other users with administrator privileges are not added to the lpadmin group. I believe that a bug report has already been filed on this.

---

### Post by madcow72 on 2007-10-23
Thanks for your input!  You're correct, my present username was not the one I installed Gutsy with, I created it after the fact.  So, another workaround to this problem would be to add whichever username that is having the problem to the Ipadmin group, yeah?

---

### Post by olafant on 2007-11-18
Unfortunately this does not always fix the problem

In my case I had to substitute the IP address (fixed in my case) for the server name in the address string i.e. workgroup/IP/printer name as the samba workgroup/server could not be detected in the browse function

---

