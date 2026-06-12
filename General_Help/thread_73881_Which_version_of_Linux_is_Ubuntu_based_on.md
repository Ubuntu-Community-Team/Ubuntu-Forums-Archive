---
title: "Which version of Linux is Ubuntu based on?"
date: 2005-10-10
forum: General Help
---

### Post by sweeneysmsm on 2005-10-10
We have a Dell latitude cp laptop. Ubuntu is running on it. The person using it is going to Jamaica and we want to know if and how it can be connected to a printer.

We want to test-drive the process by setting up a connection our current printer - and HP Deskjet 930C.

We sought advice from HP and got to this webpage:
[http://hpinkjet.sourceforge.net/install.php](http://hpinkjet.sourceforge.net/install.php)

It says:

"Follow the steps for the Linux distribution you are using:

Redhat Fedora 
Mandrake 10 
SUSE 9.2 
SUSE 9.0 
Debian "

No Ubuntu.

Does that mean we can't do it or is it based upon one of these?

Any advice greatly appreciated.

Mary

---

### Post by mlomker on 2005-10-10
Ubuntu is based on Debian.

---

### Post by ounas on 2005-10-10
Ubuntu is based on Debian

-Ounas :razz:

---

### Post by philipacamaniac on 2005-10-10
But - you probably don't need to follow the directions on that page or install anything funky.

I'm not sure about Gnome/Ubuntu (maybe someone else can post that), but in KDE/Kubuntu, all you have to do is go the Control Center, go to Printers, and then add a printer.

The HP Deskjet 930C is already available as an option. Simply follow the KDE Printer Wizard and you'll be ready to go. Hassle free!

Again, if someone could the post the Gnome instructions, that'd be great.

---

### Post by mtron on 2005-10-10
Ubuntu is based on debian "sid" , then frozen, bugfixed and enhanched with the ubuntu specific stuff and released, after this it gets the new updates sid has in it's repos and the cycle starts again.

---

### Post by mlomker on 2005-10-10
> Again, if someone could the post the Gnome instructions, that'd be great.

You just go into System, Administration, Printing, and then click on 'add printer'.  You'll see the driver for the HP 930C on the list.

---

### Post by sweeneysmsm on 2005-10-10
Thank you to all those who replied.

I followed the instructions of Philipacamaniac.

I went to System/Administration/Printing/New Printer. I chose Local Printer. I was unable to use Detected Printer as it didn’t seem to find one. I chose Use Another Printer by Specifying a Port. I should add tht Parallel Port 1 already had 2 entries – Canon and Epson. I chose Parallel Port 1 without a name. I then chose HP Deskjet 930C. It recommended hpijs as the driver. I clicked on Install.

A window entitled Select a PPD file opened, but there were no PPD files listed – Under Name there was just Desktop but no files. I cancelled that window and then chose Apply from the Add a Printer window. This got me the apparent installation of the driver in that the 930C appeared in the Printer window as ready, but when I endeavor to print something – a document or a test page – it says it is printing but nothing happens.

I feel that the actual install did not take place and wonder how I can accomplish fixing this.

Any ideas gratefully appreciated.

Mary

---

### Post by xyzzyman on 2005-10-10
Not sure if it's any help, but I have a DeskJet 930C, and I have it hooked up via USB and when I went to 'Add printer' it was automatically detected. The 930C is dual parallel & USB.

Is the printer on when you start the computer? Maybe if you power everything completely down. Turn on the printer, then power on the laptop (Power it down first, not just put it in sleep/hibernate). As long as you're using an IEEE1284 printer cable it should be able to detect it. If you have a USB port and a spare USB cable around just go with that. 

Once you get it going, here's a tip: Not all programs let you adjust to color/b&w settings, so unless you like paying for color all the time, go to 'System' - 'Admin' - 'Printers', then right-click on the printer that's working, and go into it's properties and set the paper to letter, the resolution to '300dpi, Grayscale, Black Cartridge', and the printout mode to 'Draft Grayscale'. It still seems to print out at a higher rate than the base draft mode in windows (Which I believe is 150dpi), but it's still better than wasting cartridges 'cept for the times you need to do a higher-quality print. Either way it's still a really nice printer, and I've had good luck with generic cartridges from walmart actually.

---

### Post by sweeneysmsm on 2005-10-10
Dear xyzzyman,

Thank you so much. The suggestion about the USB cable worked like a charm. I tested it with one I had on hand, so now will go out and get one to go with the laptop. The user promises you many prayers from Jamaica...

Thank you also for the tip about the color printing. We will print it out to go with the laptop.

Thanks for your help.

Mary

---

