---
title: "printer keeps disconnecting"
date: 2008-04-17
forum: General Help
---

### Post by strattonbrazil on 2008-04-17
I have a Brother MFC-5460CN that keeps disconnecting.  It makes printing hard, but even worse is the constant repeating message bubble "Printer 'MFC-5460CN' may not be connected.  Has anyone been able to resolve this with this printer or a similar system?

---

### Post by Diabolis on 2008-04-19
I had a similar problem when I tried to connect a computer with a router through a usb to serial cable.

> Often, problems with USB to Serial are associated with a package that is loaded by default called Brltty.

Brltty is a package for the blind and is used with Braille readers.

If you remove this package, hopefully, things should work.

sudo apt-get remove brltty
sudo apt-get remove brltty-x11

[original post]("http://ubuntuforums.org/showthread.php?t=539258")

---

### Post by allenbrimmer on 2008-05-29
I have had a similar problem with Hardy Heron with Brother HL-1440, connected as local printer through USB connection.  Typically, I can print one document normally, but then get error message the "the printer may be disconnected."  When this happens the printer configuration>polices shows the enabled box under State not checked.  Rechecking the enabled box does not fix the problem.  The Brother Printer Linux site only deals with printers that do not print at all under Linux.  I tried a different UBS port without improving the problem.  I also cannot print to a network Brother printer, so wonder if it a problem with Brother printers. 

One print job that did not print during my last session, remained in the print queue and did print as soon as I restarted the computer.  

Since it is an intermittent problem, I do not know what to do.  Any suggestions? 

Thanks

---

