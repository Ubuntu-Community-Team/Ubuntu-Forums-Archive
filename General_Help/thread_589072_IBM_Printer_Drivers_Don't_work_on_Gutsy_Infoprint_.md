---
title: "IBM Printer Drivers Don't work on Gutsy Infoprint Changes to Print in Gutsy"
date: 2007-10-23
forum: General Help
---

### Post by mjziegle on 2007-10-23
Hello community.  We have IBM Infoprint 1145 printers at our office.  IBM provided a .deb installer for their printer drivers.  Everything worked fine on Feisty but now the drivers don't work.  I wanted to know if anyone knew what happened to printing in Gutsy.  How is it different?  What packages were changed, added, removed vs Feisty?  When I run IBMs install script I get an lpdadmin error file not found.  If I could figure out which packages got tossed I could start working on this problem.

---

### Post by hal736 on 2008-01-31
Same problem here, but some more info.  The actual error when trying to add a printer queue is:
*"Unable to copy interface script - No such file or directory!"*

I think it is referencing the interface scripts from CUPS which should be in /etc/cups/interfaces/, but on my system (Gutsy 7.10), that directory does not exist. I don't have access to a Fiesty system at the moment, but I am guessing this is where the problem might be.  

For an interim solution, I have created a generic postscript printer for the IBM 1145 and it prints fine, just without all the bells and whistles.

I also have contacted IBM about this, (about 5 hours of calling, being transferred, etc. etc.) and they are looking into it.  I actually ended up with a guy who sounded like he knew what I was talking about, and was genuinely interested in trying to help.  He is trying to contact the people who write the driver, and see if they know what the problem is.  (thanks Chris!)

If I get a call back, I will post it here.

---

### Post by damko on 2008-04-19
Hi all

the solution is very easy but it took 4 hours to solve it. :mad: :mad:

just : mkdir /etc/cups/interfaces/

enjoy
Dam

---

