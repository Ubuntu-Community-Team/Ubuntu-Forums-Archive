---
title: "Printer problems with Brother HL-5250DN"
date: 2007-07-28
forum: General Help
---

### Post by Surkow on 2007-07-28
After succesfully installing the Brother HL-5250DN printer over the network on Ubuntu Feisty Fawn I encountered the following problems.

Often the queues won't come through and the printer needs to be reset to be able to print. I gave the printer a fixed IP in the printer itself and the router to prevent conflicts with other network devices. When working with a different PC with a HL-1430 attached to it via USB the problem with queues can occur as well (cutting of the power of the printer helps).

A different problem is that a lot of programs no longer send correct information to the printer. The only program that can print images correctly is OpenOffice.Org. All other programs like image viewers and the GIMP only cause the printer to fabricate a printed paper with a warning. The warning consists of the following:

> ERROR NAME;
   ioerror
COMMAND;
   fill
OPERAND STACK;

Some information about "ioerror":

> **[ioerror](http://dspace.dial.pipex.com/quite/errors.htm#ioerror)**

A real I/O error may have occured (e.g. a disk fault, or problem controlling a printer). In level 2 PostScript this can also be bad information for a filter, so this could mean corruption.

According to the [open printing website]("http://openprinting.org/show_printer.cgi?recnum=Brother-HL-5250DN") the printer should work perfectly (and it does support 1200 dpi HQ - at the open printing page they are unsure if it supports 600> dpi). I use the driver that was included with the printer on CD. A different printer, a Deskjet 895Cxi, that is connected directly to the pc with a USB cable has no difficulties with printing anything from any program.

Edit: to clarify myself...the error has to do with printing images. Other things like pdf files can be printed normally.

---

### Post by Surkow on 2007-07-29
Bump

---

### Post by Naci Sey on 2007-07-31
Warning: Absolute beginner.

I've also a got a Brother HL 5250DN printer, but am not on a network; it's just me using one machine with ubuntu 6.06 LTS installed. 

In System -> Admin -> Printing, the printer was not detected. It's on LPT1, so I specified that. However, there is no driver in the list for Brother printers indicated for the 5250DN.

How do I get the driver and install the printer? The instructions for installing a network printer don't seem to apply to my situation as far as I'm able to tell.

---

### Post by Surkow on 2007-08-01
I needed to install the driver from the CD that came with the printer. People who use Xubuntu are lucky because the driver is included in the printer list.

I was able to solve the problem. The only thing I had to do was start the KDE session (somehow KDE reset itself to system standard...). There really is no explanation why printing suddenly works again. On a different pc I have a variation of the printing problem; I can't print images with the eye of gnome because they end up like an empty page. Other programs work without problems.

---

### Post by Naci Sey on 2007-08-02
Surkow: "I needed to install the driver from the CD that came with the printer."

Thank you for this. My Brother laser printer now works! Not that I've tried printing beyond a single test page, but it's great to see the printer recognized now.

---

### Post by Surkow on 2007-08-17
A last try to get this solved. Why can't I print normally? Even though I solved the problems stated above printing is still not normal. Margins are always wrong - always. When I change the margins or scale down pdf's/images/documents they are still cut off even with more space. I have this with every computer and printer I use that runs Ubuntu (a HP deskjet and a Brother HL1430 are connected to them as well). Isn't there a normal way to print pages that fit within the margin?

---

### Post by Surkow on 2007-08-18
Maybe rephrasing my question will help... How can a page be scaled to fit within the margins of a printed paper? At the moment it does not scale to fit the page and if I do it by hand the margins are still cutoff. So a scaled down page that fits the page will not be printed with the borders that were previously in the margin area (even now there is space).

---

### Post by gridsleep on 2007-08-18
My HL-5250DN originally installed perfectly.  Feisty found the printer over wireless on my network, installed the printer and I had no problem until a day ago.  I was getting the "ERROR NAME; / ioerror / COMMAND; / fill / OPERAND STACK;" in a pale rectangle on the left side of the paper when trying the print an image from Eye of Gnome.  I reinstalled all the CUPS files and the printer driver, both from discovery and using the DEB file from the Brother Linux download page.  Eye of Gnome still is printing improperly.  It is not the printer driver, though.  Gimp prints the image properly.  The problem has to be with Eye of Gnome and possibly other viewers in relation to the CUPS facility.  Don't bother reinstalling the printer driver.  The problem is not there.  For now, I am looking for some other viewer to use to print images.  The Gimp is a bit too troublesome just to call up for printing.

---

### Post by Surkow on 2007-08-19
> **gridsleep said:**
> My HL-5250DN originally installed perfectly.  Feisty found the printer over wireless on my network, installed the printer and I had no problem until a day ago.  I was getting the "ERROR NAME; / ioerror / COMMAND; / fill / OPERAND STACK;" in a pale rectangle on the left side of the paper when trying the print an image from Eye of Gnome.  I reinstalled all the CUPS files and the printer driver, both from discovery and using the DEB file from the Brother Linux download page.  Eye of Gnome still is printing improperly.  It is not the printer driver, though.  Gimp prints the image properly.  The problem has to be with Eye of Gnome and possibly other viewers in relation to the CUPS facility.  Don't bother reinstalling the printer driver.  The problem is not there.  For now, I am looking for some other viewer to use to print images.  The Gimp is a bit too troublesome just to call up for printing.
Good to know I'm not the only one who is having problems with the Eye of Gnome. But I'm now talking about multiple printers. I got my HL-5250DN to work most of the time (sometimes the network disconnects because of inactivity from the printer - weird). But I was having problems with a different printer from Brother, a HL-1430. I tried an HP driver and it seems the margin/scale problem is because of the brother driver (but the quality with the HP driver is lower). I will check the brother site for official drivers to see if that will solve my problems.

---

### Post by lsackette on 2007-09-05
As you said, it just started happening a day ago.  I have the same printer and it has been working flawlessly for months now.  Unfortunately, I updated my Gusty Gibbon today and that is when i noticed it stopped working.  I have been updating GG every few days or so, but up to last week i didn't have a problem and I haven't printed since last week.  Today, printing doesn't work from evince and OO-presentation.  I tired printing one simple slide and it gave me an out of memory eorr.  trying to print more pages from evince gave the ioerror; command; fill crap.  I have verified that printing works well from my Mac Mini.  So the problem was introduced in some driver along the way.

---

### Post by Surkow on 2007-10-24
It seems the scaling problem of my Brother HL-1430 printer has been solved in Gutsy. The new printing config has an option for scaling which seems to do the trick. But both of the Brother printers disconnect after a printing a few times. Turning off the power of the printers solves the problem.

---

### Post by pidgas on 2007-11-06
I haven't taken the time to _really_ explore this issue, but my wife complains about it a lot.  "I hate printing from your computer, it never works."

I regularly get the "ERROR NAME; ioerror COMMAND; fill OPERAND STACK;" error when printing.  Especially when printing pdfs from evince.  When I use KGhostView to print a pdf - no error.

Has anyone in this thread discovered where the problem lies and what can be done about it?  We have the 5250-DN, and we used the PPD file that came with the printer.  Don't have the version off the top of my head.
 
Thanks,
Pid

---

### Post by dcstar on 2007-11-06
> **pidgas said:**
> I haven't taken the time to _really_ explore this issue, but my wife complains about it a lot.  "I hate printing from your computer, it never works."

I regularly get the "ERROR NAME; ioerror COMMAND; fill OPERAND STACK;" error when printing.  Especially when printing pdfs from evince.  When I use KGhostView to print a pdf - no error.

Has anyone in this thread discovered where the problem lies and what can be done about it?  We have the 5250-DN, and we used the PPD file that came with the printer.  Don't have the version off the top of my head.
 
Thanks,
Pid

The Brother website has a whole section with Linux printer drivers (including .deb packages), why not go there, have a read of the instructions and use the particular packages for your printer?

My HL-2040 works far better with the Brother packages than with the ones in Gutsy.

---

### Post by grackleflint on 2007-11-16
I encountered the same problem with a newly installed HL5250 printer.  As recommended by Brother at [http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html#1](http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html#1), I am using the Windows PPD file from the driver CD.

Overall the printer works fine, including all of the advanced features, but some pages cause the fill Operand Command error when printing a document from evince.  I can however print the document by using pdf2ps to convert it to PS and then lp to send it directly to the printer.

---

### Post by froy02 on 2007-11-16
There's a website for Brother Linux printers and some instructions for installing the lpr then the cups driver.
Install the lpr driver first then the cups driver.  Then open your browser and type "http://localhost:631" and configure your printer from there. Use ipp protocol then socket://xxx.xxx.xxx.xxx which is your ip adrress for the printer.


Download your lpr and cups driver from this site.  Then install them with the Gdebi package installer. Make sure you install the lpr driver first.
[http://solutions.brother.com/linux/en_us/index.html](http://solutions.brother.com/linux/en_us/index.html)

Hope it helps.  I installed my MFC665cw with no problem.

---

### Post by drfox on 2007-12-10
I was having this problem too:

ERROR NAME;
ioerror
COMMAND;
fill
OPERAND STACK; 


I've solved at least my pdf printing problems on my Brother MFC 7820N by removing evince and eog and installing KPDF. Now my pdf's print fine, but I can't print from the web.

HTH.  Larry

---

### Post by najames on 2008-01-23
I had installed the 5250DN in Mint 4 (Gutsy)  as a 5170DN.  It worked mostly ok, duplexed well with the "duplex no tumble" options.  However, I had some problems with it printing PDFs, giving the same **ioerror** others are seeing.   I deleted the 5170DN printer in the [http://localhost:631application](http://localhost:631application).  I tried to install the 5250DN, but it would not print.  I created a new printer and used the defaults with their "suggested driver" as seen below and it prints the evil PDFs now which only generated the ioerrors before, but I've lost duplexing with this setup.  This is a work in progress, but the settings below might help others get it going, and help with the angry wife factors. :)

 I have it set to a static 192.168.1.200 address and limit DHCP for computers starting at 192.168.1.100 to 110.

Brother_HL-5250DN_192.168.1.200 (Default Printer)
	Description: Brother HL-5250DN series
Location: Local Printer
Printer Driver: Brother HL-5030 Foomatic/hl1250 (recommended)
Printer State: idle, accepting jobs, published.
Device URI: socket://192.168.1.200

---

### Post by Smika on 2008-02-02
I was having this problem too:

ERROR NAME;
ioerror
COMMAND;
fill
OPERAND STACK;

Is there any solution for printing PDF and images? I am using Ubuntu and Kubuntu, but both doesn't work.

Smika

---

### Post by Smika on 2008-02-02
I found out that I can print PDF with Acrobat reader under Ubuntu and Kubuntu. But how can I print Images in Ubuntu and Kubuntu (Kubuntu more important).

Smika

---

### Post by DavidFromCanada on 2008-06-01
> **froy02 said:**
> There's a website for Brother Linux printers and some instructions for installing the lpr then the cups driver.
Install the lpr driver first then the cups driver.  Then open your browser and type "http://localhost:631" and configure your printer from there. Use ipp protocol then socket://xxx.xxx.xxx.xxx which is your ip adrress for the printer.


Download your lpr and cups driver from this site.  Then install them with the Gdebi package installer. Make sure you install the lpr driver first.
[http://solutions.brother.com/linux/en_us/index.html](http://solutions.brother.com/linux/en_us/index.html)

Hope it helps.  I installed my MFC665cw with no problem.

I installed the CUPS wrapper first and the lpr doesn't install with the .deb package!
I uninstalled the wrapper but the lpr .deb won't install and says the .deb is corrupt. I've downloaded it three times with no success.
As well this has also destroyed the update manager. I get this error when I run it.
```
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package mfc8420lpr needs to be reinstalled, but I can't find an archive for it.'
```

```
E: The package mfc8420lpr needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

```

---

