---
title: "How do I use my HP printer with ubuntu ??"
date: 2007-10-09
forum: General Help
---

### Post by hilfer on 2007-10-09
Hi all:

I have ubuntu on virtualbox.

How can I use my HP printer from inside ubuntu ??

Everytime I try to print a document it gives me an error.

Do I have to install my printer in ubuntu ??

PLease explain.

---

### Post by FuturePilot on 2007-10-09
Go System>Administration>Printing. Click Add New Printer and follow what it tells you.:)

---

### Post by AlanRogers on 2007-10-09
Even easier, use the HPLIP Toolbox.

---

### Post by FuturePilot on 2007-10-09
Not all HP printers seem to work with HPLIP

---

### Post by hilfer on 2007-10-09
Please all this is new to me.

What's HPLIP toolbox ?? where is it ??? is it on the synaptic package manager ??

tks.

---

### Post by Sef on 2007-10-10
> What's HPLIP toolbox ?? where is it ???

>  HPLIP Toolbox
HP Linux Printing and Imaging System (HPLIP) 
The HP Linux Printing and Imaging System provides full support for printing on most HP SFP (single function peripheral) inkjets and many LaserJets, and for scanning, sending faxes and for photo-card access on most HP MFP (multi-function peripheral) printers.
HPLIP is composed of:
&#8226; System services to handle communications with the printers
&#8226; HP CUPS backend driver (hp:) with bi-directional communication with HP printers (provides printer status feedback to CUPS and enhanced HPIJS functionality such as 4-side full-bleed printing support)
&#8226; HP CUPS backend driver for sending faxes (hpfax:)
&#8226; HPIJS Ghostscript IJS driver to rasterize output from PostScript(tm) files or from any other input format supported by Ghostscript, and also for PostScript(tm) to fax conversion support (HPIJS is shipped in a separate package)
&#8226; Command line utilities to perform printer maintenance, such as ink-level monitoring or pen cleaning and calibration
&#8226; GUI and command line utility to download data from the photo card interfaces in MFP devices
&#8226; GUI and command line utilities to interface with the fax functions
&#8226; A GUI toolbox to access all these functions in a friendly way
&#8226; HPAIO SANE backend (hpaio) for flatbed and Automatic Document Feeder (ADF) scanning using MFP devices
USB, JetDirect (network) and parallel-port devices are supported.
Homepage: [http://hplip.sourceforge.net/](http://hplip.sourceforge.net/)
Version: 1.7.3-0ubuntu1 (hplip)

It is installed by default (at least if you use the alternate cd.)   To see it, go to System > Preferences > Main Menu > Click on HPLIP Toolbox.   Then go to System > Preferences > HPLIP Toolbox to bring it up.   If you get this message, just follow the directions:

> PyQt not installed. GUI not available. Install "python-qt3" with the Synaptic Package Manager (Menu: System -> Administration -> Synaptic Package Manager) or run the command "sudo apt-get install python-qt3" in a terminal window.

After installing python-qt3, it should come up.

---

### Post by hilfer on 2007-10-10
Tks for yr kind support.

---

