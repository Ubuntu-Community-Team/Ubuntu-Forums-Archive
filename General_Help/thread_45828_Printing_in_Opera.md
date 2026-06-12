---
title: "Printing in Opera?"
date: 2005-07-01
forum: General Help
---

### Post by ct_srvnt on 2005-07-01
I installed Opera 8 Ubuntu package using dpkg.  Everything seemed to go fine until I tried to print.  There was no printer listed in printer options:  Destination Tab > Printers was empty.  And it didn't print.  I went to the Printer Program tab and tried /usr/bin/lpr.  No luck.  Still wouldn't print.  Can anyone offer suggestions how to get Opera in Ubuntu Hoary to find my Brother HL-5040 at lp0?
I installed Opera in Mepis, Xandros, Debian Sarge, and Mandriva and the install set up the printer with no help from me.  Has anyone else had this problem in Ubuntu?
Thanks for any suggestions  :)

---

### Post by Xian on 2005-07-01
This [METHOD](http://my.opera.com/forums/showthread.php?s=&threadid=92208) worked for me.

---

### Post by ct_srvnt on 2005-07-02
[QUOTE=Xian]This [METHOD](http://my.opera.com/forums/showthread.php?s=&threadid=92208) worked for me.[/QUOTE]

Thanks for the lead.  For some reason the shell script does not do the trick for me; I followed directions and set executable permissions.  Also tried substituting lp for lpr, but no output.  Opera still prints to file fine, but what a pain.

---

### Post by ibanez88 on 2005-09-01
I'm having the same issue.  Exactly as you describe.  It's kind of vexing as Opera seems like such a great program in every other respect!  

It should be noted that I am almost always connected to multiple printers.

EDIT:
OK I installed gtklp as suggested in other threads, set Opera's print command to gtklp, AND set the parameter to -Pname_of_default_printer

It only works when I have the parameter set as above;  which is fine, of course.. since I can now choose which printer I want to use from the dropdown menu.  All network printers are detected! 

Printing in Opera works now!   \\:D/

---

### Post by Bob Ullet on 2005-09-21
Check out this link.  
[http://www.opera.com/support/search/supsearch.dml?index=481](http://www.opera.com/support/search/supsearch.dml?index=481)
I found the "printcap" file in /var/run/cups/, coppied and pasted it into /etc/.
I changed the printer program and parameter as shown and then using synaptic installed the package "libcups".  I now have printing working for the first time!!

---

### Post by desperado666 on 2005-12-27
Do this and printing should be very easy

Open Terminal

cd /usr/lib 
sudo ln -s libcups.so.2 libcups.so

Restart Opera und you should be fine.

---

### Post by eMuNiX on 2005-12-29
[QUOTE=desperado666]Do this and printing should be very easy

Open Terminal

cd /usr/lib 
sudo ln -s libcups.so.2 libcups.so

Restart Opera und you should be fine.[/QUOTE]That works a treat, the other solution didn't, thanks :)

---

