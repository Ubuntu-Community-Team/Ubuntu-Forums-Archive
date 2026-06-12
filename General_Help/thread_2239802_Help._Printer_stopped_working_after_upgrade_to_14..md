---
title: "Help. Printer stopped working after upgrade to 14.04"
date: 2014-08-15
forum: General Help
---

### Post by Nuitblanche on 2014-08-15
Hello, 

I upgraded from 12.04 to 14.04 yesterday. And now I cant print anymore.

My printer is Brother MFC 9600 . When I open up the Print window in the status tab there is the message below: 

"usr/lib/cups/filter/foomati-rip" not available:No such file or directory

i tried "sudo service cups start" (as suggested on another forum) and it says "Job is already running"

Can anyone help?

Thanks a bunch.

---

### Post by mike225 on 2014-08-16
[https://help.ubuntu.com/12.04/serverguide/cups.html](https://help.ubuntu.com/12.04/serverguide/cups.html)

---

### Post by em3raldxiii on 2014-08-16
In the past, I have simply had to remove the existing printer, and add the printer again as a new one.  I know this is a little disingenuous, but it's a simple fix that only takes about 2 minutes.  It could save you some pain.  Then I would visit that page that Mike225 recommends.  Sorry, here's the basic version of the process:  go to the dash, type _Print_ and select Printers.  In the resulting window, remove your current printer, and then add it again, following all the automagic prompts.

---

### Post by Nuitblanche on 2014-08-16
@em3raldxiii @ mike225

On the advice of someone on another forum I did this:

 I did :

sudo apt-get update

sudo apt-get install cups-filters apsfilter

Then downloaded the hl1250 driver from [https://www.openprinting.org/printer/Brother/Brother-MFC-9600](https://www.openprinting.org/printer/Brother/Brother-MFC-9600) onto my desktop.

I didn't know how to install a the driver so I deleted the MFC Printer and then went through the process of "Add" new printer and I guess it just found the right driver it needed. It is using the hl1250 driver now and it is working fine!!!

----------------------------------------

Maybe had I read your response first, em3raldxiii, I may not have needed to do all the other steps. Either way it WORKS NOW. Thanks for your help!

---

### Post by em3raldxiii on 2014-08-16
Booya!  Sometimes it's the easy methods that are best, eh?  If you haven't already, mark the thread as Solved using the Thread Tools menu near the top of the screen.

It's possible that the driver you downloaded might have newer features than the one from the repository, but this way you know you've got one that has some support.

---

