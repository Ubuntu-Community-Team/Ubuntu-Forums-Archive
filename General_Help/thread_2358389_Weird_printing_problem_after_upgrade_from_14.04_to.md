---
title: "Weird printing problem after upgrade from 14.04 to 16.04"
date: 2017-04-12
forum: General Help
---

### Post by garyed on 2017-04-12
My all in one HP printer actually prints fine but the software will not work since I upgraded so i can't use the scanner. When I try to the HP Device manager it won't even open up. It always worked fine before my upgrade.   What's really strange is if I go to system & click on printers that won't open up either so I can't even get to the add printer place. Any ides?

---

### Post by Irihapeti on 2017-04-12
If you have CUPS installed, you should be able to configure your printer by using the CUPS web interface. Enter the address _localhost:631_ in your browser and it should take you there.

Another option is to run 
```
hp-toolbox
```

in a terminal, though I'm not sure if that gives you the necessary permissions to configure a printer.

---

### Post by garyed on 2017-04-12
I tried that & got this:
> error: HPLIP is not installed properly or is installed without graphical support. Please reinstall HPLIP
warning: Qt/PyQt 4 initialization failed.
error: hp-toolbox requires GUI support. Exiting.


Even if it's not installed correctly I should still be able to get to my printers in system administration.  I can't even get to where I can add a printer.  The funny thing is that it still prints fine in Ubuntu 16.04, its just that the software doesn't work.

---

### Post by efflandt on 2017-04-14
I have a similar problem with Lexmark network sane drivers. Adding the printers to print was no problem because they do standard postscript besides HP PCL printer languages.

It might have something to do with the change to systemd to start daemons when booting 16.04 and 16.10, but I have not solved why it does not work. A fall back solution for me is to run 64-bit 14.04 with 64-bit scanning driver in virtualbox when I want to scan on a 64-bit 16.10 host. The 32-bit scanner driver also seems to work in 32-bit 16.04 in virtualbox (which I installed to use 32-bit only WebEx with 32-bit Java and browser). But the 64-bit Lexmark sane driver that works in 64-bit 14.04 fails to work in 64-bit 16.04 or 16.10.

---

