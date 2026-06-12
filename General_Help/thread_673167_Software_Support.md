---
title: "Software Support?"
date: 2008-01-20
forum: General Help
---

### Post by Rwild on 2008-01-20
Not exactly sure of where to post this so please forgive me if I'm wrong...

So, I need Microsoft office for a class this semester and am wondering what would work better.  I have Office '07 for Vista which I don't use anymore or I can use my roommates  Office '08 for Mac.  Will the Mac version install easier than the Windows version?

---

### Post by Eck on 2008-01-20
Well, if you don't want to use a dual-boot setup with Windows/Linux, an easy way is to install virtualbox-ose from Ubuntu's repositories.  Read up on it on the virtualbox website, download and read the manual from there, and read the Ubuntu wiki on forum threads and print out some nice guides linked to from searching the forums here for virtualbox.

You can install any Windows version you have a cd/dvd and license for (you do need to activate for versions that require that like XP/Vista).  Your USB won't work with the OSE version, but you can use the Virtualbox additions to enable a shared folder so you can print up what you save there from Linux the normal way.  Just save the documents to either odf or the 2000/XP .doc format and you can open them in OpenOffice.org and print them out.

Another option is purchasing (they offer a free trial) CrossoverLinux and install Office 2000 or OfficeXP, but they don't install Office2007 yet so maybe that's not for you.  Installing with the free Wine (the older Office versions anyway) is possible, but CrossoverLinux makes it a lot easier.

Or, you can just use OpenOffice.org and save to Office formats if you think you can get away with it.  They're not 100% compatible so you could run into trouble.  Virtualbox or a dual-boot Windows/Linux seems the best options for you.

You can install the full version of Virtualbox downloaded from them, read about the Ubuntu Gutsy work-arounds for USB, and have full USB printer support in your Windows guest too.   Probably easier to manage with virtualbox-ose from the Ubuntu repo as this is Ubuntu specific and less work-arounds will be needed.

---

### Post by Rwild on 2008-01-20
Thanks for the great reply.  I will look into it for sure. :)

---

