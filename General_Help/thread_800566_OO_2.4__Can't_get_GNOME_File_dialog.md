---
title: "OO 2.4:  Can't get GNOME File dialog"
date: 2008-05-19
forum: General Help
---

### Post by cal-lito on 2008-05-19
On Ubuntu 8.04  (with its default OpenOffice 2.4), I can't get the 
GNOME File dialog  (File/Open, File/Save As).

I go to the menu Tools / Options, and in the section "General", there 
is the checkbox "Use OpenOffice.org dialogs" --- it was unchecked by 
default, however, no matter what I put in there, I get the incredibly 
ugly (and useless) Windows98-like Open/Save dialog  (I mean, seriously: 
*what on earth* are the OO team thinking!!)

Anyway, even with OO 3.0-beta, downloaded from [www.openoffice.org](www.openoffice.org), I 
can configure it to use the GNOME dialogs, and it works as expected; 
the version that ships with Ubuntu 8.04 does not seem to work... 

Am I missing something?

Thanks,

Carlos
--

---

### Post by FuturePilot on 2008-05-20
Do you have openoffice.org-gtk and openoffice.org-gnome-support installed?

---

### Post by cal-lito on 2008-05-20
Ok, problem solved  (BTW, it's actually openoffice.org-gnome, and not 
-gnome-support ...  minor detail)

However, I wonder if a defect report should be filed --- I mean, the 
behaviour is what I described on an out-of-the-box installation, through 
the Live CD, so it's not even an option that I selected during installation.

It simply installs that way and the behaviour is, well, *arguably* 
defective --- actually, without the "arguably":  it *is* defective in that 
the option, as it is selected in OpenOffice's preferences, is not honoured.

So, the "actual" defect would be that the packages openoffice.org-gnome 
and openoffice.org-gtk are not installed by default.

Putting that aside, thanks for pointing out the solution to what I was 
trying to do!

Carlos
--

---

