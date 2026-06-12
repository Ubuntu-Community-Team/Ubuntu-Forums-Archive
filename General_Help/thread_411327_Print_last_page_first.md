---
title: "Print last page first"
date: 2007-04-16
forum: General Help
---

### Post by ar1stotle on 2007-04-16
OK, I hooked up a HP Deskjet 5150 connected to another windows PC on my network and got it working over the network in Ubuntu 6.10 Edgy. It was incredibly easy to set up. However, I don't see an option to print the last page first. Is such an option available? It's just inconvenient to have to go reorder everything I print.

Thanks!

---

### Post by kostkon on 2007-04-16
You can enable printing of  the last pages first with the *HPLIP Toolbox* app that you can find at System->Preferences. Can you check if your printer is recognised by this app? If not, try to add your printer and then you will be given the option to enable to print the last pages first.

---

### Post by ar1stotle on 2007-04-16
Hmmm.... don't see that app. I checked Synaptic and supposedly it's installed, but I tried to use tab completion to find a command to open it in the terminal but came up empty. Any ideas?

edit: OK, I found hp-toolbox and installed the necessary packages. Now when I run it, it says it can't find a HP device and that I need to run hp-setup. When I do that, I get:

```
aristotle@Tsunami:~$ sudo hp-setup
Password:

HP Linux Imaging and Printing System (ver. 1.6.9)
Printer/Fax Setup Utility ver. 2.2

Copyright (c) 2003-6 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

error: No devices found.
error: Error occured during interactive mode. Exiting.
```
My printer is connected to a Windows machine on the network. Any clues on what I need to run to get it set up properly?

I tried :
sudo hp-setup 192.168.1.100 
but it just says that it couldn't find any devices.

---

### Post by 11hjpphty76lkjj on 2007-04-17
HPLIP does not currently support connecting to a printer shared from a windows system.

There may be other ways to configure the printer however.

A

---

### Post by WW on 2007-04-17
You could also try **gtklp**; you can install it from Synaptic. It provides a nice GUI for printing.  It has an option for printing the pages in reverse order.

---

### Post by ar1stotle on 2007-04-17
> **WW said:**
> You could also try **gtklp**; you can install it from Synaptic. It provides a nice GUI for printing.  It has an option for printing the pages in reverse order.

That's just what I needed. Thanks a lot!

---

