---
title: "Scanning in Ubuntu"
date: 2007-08-07
forum: General Help
---

### Post by logreeval on 2007-08-07
I have an all-in-one HP 5610 officejet and I know that Xsane is the scanner.

But I was wondering, is that the best one?, are there any different scanning software I could try out?

Also, in Xsane, when I close it, and error pops up 3 times...like Failed to create file, Permission denied, or someting like that.

Thanks

---

### Post by phidia on 2007-08-07
You need to be sure you have the correct driver for that all-in-one printer.
HP's are generally well supported. Check out your [printer]("http://openprinting.org/show_printer.cgi?recnum=HP-OfficeJet_5610")<the linuxprinting.org database.

---

### Post by logreeval on 2007-08-07
I have already installed all the correct drivers, HPLIP, and done the hp-setup

I just want to know if their is another program for scanning, besides Xsane.

---

### Post by david_2001 on 2007-08-07
KDE has kooka, which I've never really got on with and wasn't being actively developed when I last checked.  I have [COLOR="DarkOrange"][VueScan]("http://www.hamrick.com/vsm.html")[/COLOR], which costs money but is very versatile.  The GIMP and OpenOffice can both use the sane backends to acquire scans.  For day to day scanning, however, XSane does everything I need.  A Google search for "linux software graphics scanning" will find a few other alternatives.

---

### Post by logreeval on 2007-08-08
Thanks, i will check all of them out.

---

### Post by LinuxBob on 2007-08-12
I posted this problem before with no responses.

Xsane sees my internal  TV tuner as the scanning device.  I have loaded Fiesty on an HP P4 Media Center PC.  My scanning device is a networked HP 6110 All in One printer with its own IP address on my home network.  How do I change my scanning device from the TV tuner to the All in One on the network?

Xsane provides no option to switch from TV tuner at all, much less an option to use my networked printer.  Any help?

---

### Post by gobbles414 on 2007-08-12
Hi logreeval,

Can you actually complete a scan-and-save of an image using Xsane? If so, then I would just ignore the warnings. If not, please post the EXACT error message(s) you are getting.

The program that I prefer for scanning is called [gscan2pdf]("http://gscan2pdf.sourceforge.net"). The user interface is simple but powerful. And the method for scanning multi-page documents is much more intuitive than in Xsane. The Ubuntu OS doesn't know about gscan2pdf, so you can either download the .deb package and double-left-click to install. Or, you can add the program to Ubuntu's list of software sources using the directions given on the gscan2pdf website under Debian systems. The second option should provide the ability to update the program automatically when a new version is released. When you launch the app, you may get a message saying so-and-so isn't installed. I suggest that your write a list of the package names it gives you. Then go to the Synaptic Package Manager and install the optional packages that you might use in the future (like text recognition, for example).

P.S. LinuxBob, I know how frustrating it is to not to get a reply to a post (look at my post history if you don't believe me). I have found that it is an issue of timing -- especially in the busier parts of the forum. If your post is not on the first page of results when browsing new posts, chances are that nobody will ever see it. My recommendation would be to either post a reply to your original question (that will send it to the top of the list of new posts) or create a new post in a different category than your original.

---

### Post by david_2001 on 2007-08-13
> **LinuxBob said:**
> I posted this problem before with no responses.

Xsane sees my internal  TV tuner as the scanning device.  I have loaded Fiesty on an HP P4 Media Center PC.  My scanning device is a networked HP 6110 All in One printer with its own IP address on my home network.  How do I change my scanning device from the TV tuner to the All in One on the network?

Xsane provides no option to switch from TV tuner at all, much less an option to use my networked printer.  Any help?
I can do the first part.  To stop sane confusing a TV tuner for a scanning device edit /etc/sane.d/dll.conf and comment out "v4l" (it should be the last line).

EDIT: Not that I have any experience with networked scanners but does a "man sane-net" help?

---

