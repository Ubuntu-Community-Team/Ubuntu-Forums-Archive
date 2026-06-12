---
title: "new problem with adding a new printer"
date: 2005-10-18
forum: General Help
---

### Post by bsun on 2005-10-18
Basically I had done the following

Select   System->Administration->Printing, then left click on the New Printer icon and click "Add", 

then I got a popup window saying:

The Application "gnome-cups-add" has quit unexpectedly.

You can inform the developers of what happened to help them fix it.  Or you can restart the application right now.
 
 [ Restart Application] [Close] [Inform Developers]
. 

Does anyone know how to fix this problem?  thanks.

---

### Post by ecobuntu on 2005-10-18
have you run:

sudo gnome-cups-add

at the terminal?  
If not maybe it's a bug

---

### Post by bsun on 2005-10-18
I tryied that  and got lots of information in the terminal at first and then a window poped up saying the same thing.  Is it a bug??  What can I do then? Just report and wait?

---

### Post by The Headhunter on 2005-10-19
I'm getting the same problem.

When I run it on the terminal, the output is something like the following except much longer:

```
** (gnome-cups-add:3602): WARNING **: Two ppds have driver == 'hpijs (recommended)'
        ->hplip/HP-PSC_2175-hpijs.ppd (HP PSC 2175 Foomatic/hpijs[1]) and
        ->foomatic-ppds/hplip/HP-PSC_2175-hpijs.ppd (HP PSC 2175 Foomatic/hpijs)[1]

** (gnome-cups-add:3602): WARNING **: Two ppds have driver == 'hpijs (recommended)'
        ->hplip/HP-PSC_2210-hpijs.ppd (HP PSC 2210 Foomatic/hpijs[1]) and
        ->foomatic-ppds/hplip/HP-PSC_2210-hpijs.ppd (HP PSC 2210 Foomatic/hpijs)[1]

** (gnome-cups-add:3602): WARNING **: Two ppds have driver == 'hpijs (recommended)'
        ->hplip/HP-PSC_2300-hpijs.ppd (HP PSC 2300 Foomatic/hpijs[1]) and
        ->foomatic-ppds/hplip/HP-PSC_2300-hpijs.ppd (HP PSC 2300 Foomatic/hpijs)[1]

** (gnome-cups-add:3602): WARNING **: Two ppds have driver == 'hpijs (recommended)'
        ->hplip/HP-PSC_2350-hpijs.ppd (HP PSC 2350 Foomatic/hpijs[1]) and
        ->foomatic-ppds/hplip/HP-PSC_2350-hpijs.ppd (HP PSC 2350 Foomatic/hpijs)[1]

** (gnome-cups-add:3602): WARNING **: Two ppds have driver == 'hpijs (recommended)'
        ->hplip/HP-PSC_2400-hpijs.ppd (HP PSC 2400 Foomatic/hpijs[1]) and
        ->foomatic-ppds/hplip/HP-PSC_2400-hpijs.ppd (HP PSC 2400 Foomatic/hpijs)[1]

** (gnome-cups-add:3602): WARNING **: Two ppds have driver == 'hpijs (recommended)'
        ->hplip/HP-PSC_2500-hpijs.ppd (HP PSC 2500 Foomatic/hpijs[1]) and
        ->foomatic-ppds/hplip/HP-PSC_2500-hpijs.ppd (HP PSC 2500 Foomatic/hpijs)[1]

```

---

### Post by GeorgeD on 2005-10-26
I have the same problem. What's bothersome is that I was able to define a new printer the first time I tried but inadvertently removed it. All I wanted to do was add it again. Here are my comments to Bug Buddy.

Description of the crash:
I had an epson stylus printer added in Printers window and indadvertently removed it and can no longer Add a printer.
When selecting Add printer I get an Error window as follows: The Application "gnome-cups-add" has quit unexpectedly

Steps to reproduce the crash:
1. System->Administration->Printing
2. Select Print->Add Printer
3. Error window as shown above

Expected Results:
I expect to get a list of printers to install which is what I did to define and attach the printer originally

How often does this happen?
Every time I try it.

Additional Information:
From Synaptic Package Manager  I reinstalled all previously installed cups packages, rebooted and continue to get the error.
At this time I do not have access to a printer
The printer is on a USB port.

---

### Post by ok67 on 2005-12-09
I have the same error, trying to install a ppd file for my Oki 14i. Is it posible to add the ppd file manualy without using the gnome-cups-add program ?

---

### Post by ok67 on 2005-12-09
[QUOTE=ok67]I have the same error, trying to install a ppd file for my Oki 14i. Is it posible to add the ppd file manualy without using the gnome-cups-add program ?[/QUOTE]
Found the solution to my problem, just ignore the error-message and not closing the message box.

---

