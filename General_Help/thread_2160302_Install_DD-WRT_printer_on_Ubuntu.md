---
title: "Install DD-WRT printer on Ubuntu?"
date: 2013-07-06
forum: General Help
---

### Post by Nikolai D. on 2013-07-06
Hi there,

So i just connected the wr703n router with DD-WRT v24-sp2. To the old LaserJet 2100 HP printer. (Via USB to Parallel cable). So in this newer DD-WRT version like the guy here in the video explains u dont have to install some USB packages via Commad Line. U just go to the web gui and enable USB support. So i did it. [http://www.youtube.com/watch?v=b9xB144KqgA](http://www.youtube.com/watch?v=b9xB144KqgA)
But what now? The guy says the DD-WRT doesnt use Cups. But i always used Cups web Gui on my Ubuntu Laptop when i want to add a printer. But how do i add this DD WRT printer now?

Thanks in advance,
Nikolai

---

### Post by Nikolai D. on 2013-07-06
ok watching a video somewhat further actually helped to discover that i can use cups here to.
But still which driver do i use? And it says printer is not responding.

---

### Post by Nikolai D. on 2013-07-06
says this 


HP (Processing, Accepting Jobs, Not Shared)
Description:	LJ
Location:	2100
Driver:	HP LaserJet 2100 Series Postscript (recommended) (grayscale, 2-sided printing)
Connection:	socket://192.168.1.32:9100
Defaults:	job-sheets=none, none media=na_letter_8.5x11in sides=one-sided
Jobs

Search in HP:

Showing 1 of 1 active job.
&#9660; ID &#9660;	Name	User	Size	Pages	State	Control
HP-6  	Unknown  	Withheld  	1k  	Unknown  	processing since
Sat 06 Jul 2013 04:49:19 PM CEST 
"The printer is not responding."

---

### Post by Nikolai D. on 2013-07-07
ok i see here [http://www.dd-wrt.com/wiki/index.php/Printer_Sharing#Notes_For_v24_Stable](http://www.dd-wrt.com/wiki/index.php/Printer_Sharing#Notes_For_v24_Stable) something about enabling jffs but mine says not mounted. ill go check dd wrt forums on this

---

### Post by gordintoronto on 2013-07-07
What version of Ubuntu? If I were you, I would get rid of everything you have done on the computer regarding this printer, and begin again.

Run Printing or Printers or whatever shows up when you type "print" in the dash or the programs menu. Click on Add or "+" then on "network printer," and wait a few seconds for the printer to appear. Select it, then "OK" "Yes" "Continue" or whatever it takes until the printer is properly installed.

This has worked for me about 30 times with different versions/distros over the past three years.

---

