---
title: "Weird error when printing - printing stops working"
date: 2007-09-07
forum: General Help
---

### Post by rax_m on 2007-09-07
Hi 

I have an HP Deskjet 850C connected to an XP machine. I am trying to print to it from Ubuntu. Now printing the first document (a pdf from eVince) works fine. However, when I then try and print subsequent documents I get the following error in the print dialog. "/usr/lib/cups/filter/foomatic-rip failed"

Now if restart the printer I can then print another document. However printing works fine if I print from the XP machine. 

The following is the output from /var/log/cups/error_log: 

```

E [06/Sep/2007:16:42:48 +0200] Creating missing directory "/var/run/cups/certs"
E [07/Sep/2007:08:43:39 +0200] Creating missing directory "/var/run/cups/certs"
E [07/Sep/2007:08:54:52 +0200] [Job 9] /undefined in &#65533;&#1912;
E [07/Sep/2007:08:54:52 +0200] PID 6578 (/usr/lib/cups/filter/foomatic-rip) stop
ped with status 3!
E [07/Sep/2007:08:59:54 +0200] [Job 11] /undefined in &#65533;&#1912;
E [07/Sep/2007:08:59:54 +0200] PID 6939 (/usr/lib/cups/filter/foomatic-rip) stop
ped with status 3!
E [07/Sep/2007:09:03:06 +0200] [Job 12] /undefined in &#65533;&#1912;
E [07/Sep/2007:09:03:06 +0200] PID 7082 (/usr/lib/cups/filter/foomatic-rip) stop
ped with status 3!


```

Anyone have any ideas?

Thanks
Rax

EDIT:
Even though I get that error in eVince, I can still print from OpenOffice fine. So looks like it might be an eVince bug.

---

### Post by firmit on 2008-07-08
I have had some trouble with this myself. Different PDF behave differently. Some print - others don't. It seemed as it had something to do with pagenumbers(!) and locales. I have written some .tex docs and created pdf's. These have been written nb_NO.UTF-8 - not in en_US or en_GB. But I did not have that language configured in my locales... So I ran **sudo dpkp-reconfigure locales** and added the wanted languages... And I am starting to think that my problem is solved!

---

