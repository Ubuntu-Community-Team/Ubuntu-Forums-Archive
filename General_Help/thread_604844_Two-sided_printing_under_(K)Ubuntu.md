---
title: "Two-sided printing under (K)Ubuntu"
date: 2007-11-06
forum: General Help
---

### Post by stukov on 2007-11-06
Hello,

    Is it possible to tell all applications installed under Ubuntu to print on the two sides of the sheet? gEdit works fine by default, but it is not the case with other applications like Kwrite.

    I do not see any option for duplex printing in the printing dialogs.

Any ideas?


Thanks for your help.

---

### Post by leonidas666 on 2007-11-06
What kind of printer do you have?
I have a proper Postscript printer, and somewhere in the postscript settings of this printer there is the option for duplex-printing. It's possible to set a default value for this option in the kde-printer settings. 
Maybe it also depends on which command you are using for printing, kprinter, gprinter or straight through cups? Possibly there is a different set of default values for each method.

---

### Post by stukov on 2007-11-06
> **leonidas666 said:**
> What kind of printer do you have?
I have two Dell 5100cn printers. They support two-sided printing by default I think. We also have a machine running a dedicated CUPS server that serves for printing.
> **leonidas666 said:**
> I have a proper Postscript printer, and somewhere in the postscript settings of this printer there is the option for duplex-printing. It's possible to set a default value for this option in the kde-printer settings.
I'll try to check out if I can change something like that in my printer's options. I'll let you know if I find something.
> **leonidas666 said:**
> Maybe it also depends on which command you are using for printing, kprinter, gprinter or straight through cups? Possibly there is a different set of default values for each method.
I use the dialogs from each application. I'm not sure what each of them are using as their backend. What is strange is that gEdit works fine by default, but not KDE applications like KWrite of KGhostView. Very very strange.

I hope this clarifies the situation. Thanks for your reply!

---

### Post by leonidas666 on 2007-11-07
> **stukov said:**
> I have two Dell 5100cn printers. They support two-sided printing by default I think. We also have a machine running a dedicated CUPS server that serves for printing.

Actually i wanted to know through what kind of driver you are printing... So are you printing through this deidcated cups server? That means that for your local machine the printer acts just like a normal postscript printer, right?

> **stukov said:**
> 
I use the dialogs from each application. I'm not sure what each of them are using as their backend. What is strange is that gEdit works fine by default, but not KDE applications like KWrite of KGhostView. Very very strange.

Naturally, Gnome applications use gprinter, and kde applications use kprinter (but there's probably some way to re-configure this). Are you actually running kubuntu or ubuntu?

---

### Post by stukov on 2007-11-07
> **leonidas666 said:**
> Actually i wanted to know through what kind of driver you are printing... So are you printing through this deidcated cups server? That means that for your local machine the printer acts just like a normal postscript printer, right?
Yes. My local workstation only detects the printers from my server's broadcast. I have not had to install any drivers on the workstations.
> **leonidas666 said:**
> Naturally, Gnome applications use gprinter, and kde applications use kprinter (but there's probably some way to re-configure this). Are you actually running kubuntu or ubuntu?
OK. I have kprinter installed but not gprinter. In kprinter, the duplex printing options are greyed out. How can I enable this menu?

I have a few machines running kubuntu but were installed with ubuntu (just installed packages from ubuntu) and others only kubuntu.

Thanks again for your help!

---

### Post by leonidas666 on 2007-11-07
Are we talking about the same options? KPrinter has many dialogs accesible from the "tabs" at the top. The first few tabs are "nicely layouted" dialogs, but the last (or second-last) tab are the bare postscript options. I usually set the duplex setting for my printer from there.
How does kprinter know which options to display there? This is done with a .ppd file. Even with my proper postscript printer i had to find a special .ppd file to access all the functions of the printer. Maybe you have to install a specific .ppd file, probably at your printer server.
More information about .ppd files is available at [www.linuxprinting.org](www.linuxprinting.org)

---

### Post by stukov on 2007-11-07
Thanks a lot leonidas!!!

You were right, when I transfered the cups server from one machine to another I kept the config files but forgot to move the ppd files!

It works now. Thank you again!

---

