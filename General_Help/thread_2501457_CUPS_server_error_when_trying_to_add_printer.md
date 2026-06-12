---
title: "CUPS server error when trying to add printer"
date: 2024-10-08
forum: General Help
---

### Post by ozark_hillbilly on 2024-10-08
I am trying to print out a pdf file image I received to make a shipping label.
The issue is that evidently my system has never been set up with a destination printer.
I can print out images from my LibreCad app to the printer with no problems.

But when I try to print the pdf file it does not allow me to send it to the printer, only output as a file.

Using terminal and trying to print it out with 'lp' has not worked because I do not have a default printer destination.
I am receiving a CUPS server error when trying to add the Brother HL-L2360Dseries printer to the system
through Settings > Printers > Add printer.

Is there any easy way through terminal to accomplish this. Or is their a way to convert the pdf file so that I can 
print it out like other non pdf files?

Running Ubuntu 22.04 LTS

edit-

terminal output:

ed@ed-G41MT-S2PT:~/Returns$ lpstat -e
Brother_HL_L2360D_series
ed@ed-G41MT-S2PT:~/Returns$ lp -d "Brother_HL_L2360D_series" "Aliexpress shipping label.pdf"
lp: The printer or class does not exist.
ed@ed-G41MT-S2PT:~/Returns$

---

### Post by TheFu on 2024-10-09
Since 2016, printing has been really easy for supported printers.  I haven't needed to even choose a driver on my circa-2008 laser and Brother all-in-one devices.

In 2020, I noticed that printers would be "found" either locally connected or on the network and configured automatically.  The default CUPS and avahi is all that is needed.  When I run 
```
$ system-config-printer  # <---- that's the printer setup GUI
```
after a new install, the printers would already be there.  Not sure when they are populated - must be at the first run, since I usually don't have any printers powered on.

Neither of my printers are network aware. No wifi. No ethernet either.  I do have a 20.04 printer server that announces via mDNS (avahi) that there are printers connected to it for any client on the LAN.

So, if your printer supports "Driverless Printing", I'd say to use that. [https://openprinting.github.io/driverless/](https://openprinting.github.io/driverless/) has more, but basically, the URL begins with IPP:// ... 
> **Importance-:**
Driverless printing is especially important for Linux and similar operating systems as they are often not explicitly supported by the manufacturers supplying drivers for them. Originally the driverless printing standards were created to allow smartphones, tablets, and similar mobile devices to print, as these come with several different and new operating systems. Even very cheap printers do driverless printing (people want to print from phones), so it is easy to get a printer for Linux nowadays.

I looked up your model - seems there are 3 submodels that support "Airprint" as the protocol.  That's Avahi. 

The 2nd answer here, shows how to do it through the CUPS web interface using driverless printing. [https://askubuntu.com/questions/1484939/driverless-printing-w-ipp-on-brother-hl-l2350dw-from-22-04](https://askubuntu.com/questions/1484939/driverless-printing-w-ipp-on-brother-hl-l2350dw-from-22-04)  This link is provided because I assume the **system-config-printer** method didn't work for you.

---

### Post by ozark_hillbilly on 2024-10-09
Thank you. Your lead gives me a direction to head into.

update:

issue resolved....i was able to assign the printer as the default network printer through printers localhost....

---

