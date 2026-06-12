---
title: "New to Linux, Help..!  Printing on Networkd Laser"
date: 2007-05-05
forum: General Help
---

### Post by p0ker123@Safe-mail.net on 2007-05-05
Printing on my Networked 'Brother HL-2040' on Draytek 2600VG Router, (built in USB Print Server)

Hi, English is not my first language so if i make mistake, sorry..

Ok, i just move from Windows to Ubuntu 704. I used the Print Server on my Draytek with out hassel.

This is the setting guide for Windows:
[http://www.support.draytek.co.uk/kb_vigor_lpr_setup.html](http://www.support.draytek.co.uk/kb_vigor_lpr_setup.html)

At the bottom of that link.. it has the linux parameters.
" Using the Vigor's printer port from Linux

Linux is not officially supported for printing facilities, however it may be possible to access the printer port LPR facility by configuring CUPS using the parameter: lpd://192.168.1.1/p1.  "

Now, i try very basically to set it up and my printer is not working. I am using HL2060 Driver as reccomended by linuxprinting.   Setting i used are -
Networked Printer.. Unix LPD.. 
Host: lpd://192.168.1.1/   
Que:  p1
..  i have tryed certain variations.. no help.

Please if some can help me to use my network printer i would be greatful..  I dont under stand what is cups .. and i have only used linux for 3 days now.. If i cant use my networked printer i will have to go back to windows..   :( 

I have read the HL2040 works well with Linux, just setting it up with my print server is hurdle.. Linux Printing with the Draytek Print server (any printer) is also ment to work well!

Thanks

---

### Post by doncristobal on 2007-07-08
Maybe this can help: [http://ubuntuforums.org/showthread.php?t=369972](http://ubuntuforums.org/showthread.php?t=369972)
it's how i solved a very similar problem with my siemens router and hp printer

Good luck!

---

### Post by phansiizwe on 2007-07-08
You might try setting it up using a raw connection, it's just a long shot and works for me (but with different hardware)...

Under: System->Printing
Right click on your printer and select "properties", the click the connection tab and try:

Printer Type: Network Printer               TCP/Socket, HP JetDirect, Raw connection
Host :            192.168.1.1
Port:              9100

---

### Post by wislon32 on 2007-08-12
The LPT1: trick as the printer name worked for my HP5940 and Draytek 2600VG

---

