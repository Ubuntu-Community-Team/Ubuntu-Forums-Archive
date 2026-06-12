---
title: "Printing PDF files"
date: 2007-11-17
forum: General Help
---

### Post by bkline on 2007-11-17
I'm running Gutsy on i386, and Evince is the app installed by default for PDF files.  Problem is, it won't print.  It acts like it's going to print (it brings up the standard Print dialog window, it lets you choose a printer, the OK button is enabled, the dialog closes when you press it), but nothing ever gets sent to the print queue.  All the other apps seem to print just fine.  I could convert everything to PostScript and send it to the printer by hand, but I'd rather have a PDF reader that works correctly.  Any recommendations for an open-source alternate under Gnome?  Or should I just install Adobe's reader?

Thanks!

Bob Kline

---

### Post by prince_niceguy on 2007-11-19
you can use kpdf... it is kde app though. synaptic listed lot of pdf viewer you can install one of them and see if they work for you.

---

### Post by avik on 2007-11-19
Can you print from other applications?

---

### Post by prince_niceguy on 2007-11-19
yes i can. even from evince i can print... can you reinstall your printer/evince.

---

### Post by bkline on 2007-11-19
> **avik said:**
> Can you print from other applications?

Yes.  Sorry - I thought I had mentioned that in my original post.

Bob

---

### Post by bkline on 2007-11-19
> **prince_niceguy said:**
> you can use kpdf... it is kde app though. synaptic listed lot of pdf viewer you can install one of them and see if they work for you.

Thanks for the reply.  As I mentioned in my original post, I'm running Gnome.  Will I need to drag in a lot of modules from KDE to run kpdf?

Bob

---

### Post by bkline on 2007-11-19
> **prince_niceguy said:**
> yes i can. even from evince i can print... can you reinstall your printer/evince.

Well, I was not optimistic that this would work, as this was a fresh install of Gutsy, not an upgrade, but I tried it anyway.  Since the original order had evince installed before the printer (since evince is installed by default when Ubuntu is installed), I decided to reverse the order and install evince after the printer was installed.  To my surprise, this solved the problem.  So it appears that evince doesn't really know how to print correctly unless it's installed **after** the printer is installed.  Is this a known problem?

Another odd thing I noticed when removing evince was a bunch of XML parse error messages complaining about malformed XML (closing delimiter missing on a bunch of start tags, for example, "/var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml:3875: parser error : Couldn't find end of Start Tag tocsect2 line 3875
<tocsect2 link</tocsect1>").  Anyone seen this problem?

Thanks for the tip, Prince.

Bob

---

### Post by jjalocha on 2007-11-22
Sadly, this didn't work for me:

[LIST=1]
[*]uninstall evince-gtk
[*]remove printer from CUPS
[*]plug-in printer again, and wait for CUPS to re-install
[*]install evince again
[/LIST]

As far I remember, evince never printed PDFs for me. It's usually not a big deal for me, since I almost don' t use this feature, and really like the application besides this. But still, quite amazing that such a basic feature is not fixed...

---

### Post by bob12564 on 2008-02-24
I had been able to print PDFs with Evince until yesterday.  It printed 2 one-page documents nicely and then mysteriously stopped printing altogether.  The printer dialog comes up but after hitting OK nothing happens.  No signs of life from the printer.  Other utilitiies print just fine so the problem is with Evince.

Thanks to a suggestion I received about another printing problem a while back, I had already installed GTKLP and I was successfully able to print the PDF using it. 

I'm using Gutsy 7.10.

---

