---
title: "How do I print to printer, not to file"
date: 2013-08-21
forum: General Help
---

### Post by philw41 on 2013-08-21
Hello, Ubuntu world!  I've been using (trying to use) Ubuntu for a couple of years now.  Then, recently, my computer went on strike.  No amount of negotiatiion would restore it to its previous self, so I purchased a new machine, without an OS.  Loaded the current release of Ubuntu, went to print a document, and the silly thing printed .... TO FILE!  At that time, I decided that this was a good time to "join the mainstream" of Ubuntu, meet some of you fine people, and ask for help.  How do I change "print to file" to "print to printer"?

I've been using Ubuntu for a few years, and using the printer with no problems.  (HP Laserjet 1200) I've never had to load drivers that I can recall.  I've used the printer with a couple of boxes, through a few releases of Ubuntu and had no problems printing.

---

### Post by TheFu on 2013-08-21
You probably already found this [https://help.ubuntu.com/community/Printers](https://help.ubuntu.com/community/Printers) and tried to get it working that way.  
Where did you have issues?

The overview is:
* Ensure you have a supported printer.
* Connect the printer to your ubuntu box.
* Different GUIs work differently, but look for "Add Printer" in your GUI.
* More and more often, printer drivers will install and work.
* If your printer is not directly supported by Ubuntu, check the vendor sites for Linux drivers, install instructions, etc.  Just because the EU or US sites don't have any Linux driver links, doesn't mean the Asia or worldwide sites do not. Check those too.
* CUPS is the normal printer service ... after that is installed, which should happen with the driver install, you can setup printer sharing through a web GUI at [http://localhost:631/](http://localhost:631/)  (or insert the hostname of the Linux PC where the printer is attached).

If your printer is supported, it sorta just works.
If your printer is not supported, you aren't necessarily out of options, but with cheap printers available these days, the effort will probably be more than the cost of getting a well-supported, new, printer.

Clear as mud?

---

### Post by SeijiSensei on 2013-08-21
I find the web-based interface that ships with the standard Linux printing system, CUPS, makes printer management quite easy.  Open a browser and point to [http://localhost:631/](http://localhost:631/).  That will display the CUPS administration interface. Some tasks like installing a printer require root privileges.  When the authentication box appears, just use your ordinary username and password.  By default the first user created during installation can use [sudo]("https://help.ubuntu.com/community/RootSudo") to execute administrative tasks.  

You'll see a wide variety of methods to connect to the printer especially if it is networked.  You'll also be able to select a printer driver from the hundreds of drivers that CUPS includes by default.

---

