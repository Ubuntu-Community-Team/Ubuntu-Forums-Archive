---
title: "Which driver for Brother MFC-7420"
date: 2007-02-07
forum: General Help
---

### Post by redskinsfan on 2007-02-07
Hi.  I'm trying to connect to a networked brother mfc-7420 that is on a d-link dpg-310 print server.  I use the add a printer dialog.  Select network printer, unix printer (lpd), and then enter the ip address of the printer and the queue name (from the print server's settings; i've also tried entering L1, LPT1, and leaving it blank).  None of this seems to work.  The closest I have gotten it to printing is that a message shows up on the printer saying receiving data, but nothing is ever printed.  I think this may have to do with the printer driver that I have selected.  Because the database doesn't include the 7420, I selected the MFC-8300.  Anyone know where I can get a driver for the 7420, or if there is a different drive that I should use, or whether there is some other problem other than the driver.  Any help would be greatly appreciated.

Thanks.

---

### Post by DagMan on 2007-02-09
It sounds like maybe you've already seen it, but this guide has helped a lot of people install drivers other than the one listed [http://ubuntuforums.org/showthread.php?t=105703](http://ubuntuforums.org/showthread.php?t=105703)
The additional link to the thread concerning edgy was necissary for me.

As for the driver's themselves, you want the debian ones here [http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html)
and here [http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html)
The .deb files not the red hat or whatever the other ones are.

and there are some instructions for your particular printer and the cups driver in the second link posted (and some printers as well so the name will need to be changed to your driver on this page as it's a general guide) here [http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install5.html](http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install5.html)

If you want to search the tutorial section over for Brother then that's a good idea too.  The last link on the brother page is not specific to Ubuntu but a general linux one so the results could very well vary from distro to distro and there might very well be other info applying to your printer or a similar one that's right here on the forum.

---

### Post by russell.h on 2007-02-09
I have a networked Brother printer (not on a print server), which there didn't seem to be a driver available for. I used a driver for a similar model number and at first it seemed like it wasn't working. Then I found that I had to go in and change some address, which it had set to a USB port for some reason (I specifically checked the network box) to the IP of the printer, then suddenly everything worked fine.

Not sure if that helps, but there it is.

---

### Post by DagMan on 2007-02-09
Yeah you select Unix printer (LPD)
I just noticed in the above post about the queue name.  I left mine blank because I didn't know what it meant and it still works, so if you have confusion over that aspect of it likely it will also work without it.

---

### Post by redskinsfan on 2007-02-09
> **DagMan said:**
> Yeah you select Unix printer (LPD)
I just noticed in the above post about the queue name.  I left mine blank because I didn't know what it meant and it still works, so if you have confusion over that aspect of it likely it will also work without it.

I think the queue setting is necessary if the printer is attached to a print server rather than directly to the computer, as mine is.  You can get the queue name from the print servers configuration page.  I found that selecting the MFC-9600 printer and choosing its recommended driver works.

---

### Post by DagMan on 2007-02-09
Is this something that is found in the printer itself or that you found through the computer's connection to the printer?  I don't really  understand what you've described and I am printing over a network and would like to get this part setup.  It could be the reason that I'm printing quite a bit slower than my wife's windows connection to it.

Any luck with the drivers?

---

### Post by redskinsfan on 2007-02-09
> **DagMan said:**
> Is this something that is found in the printer itself or that you found through the computer's connection to the printer?  I don't really  understand what you've described and I am printing over a network and would like to get this part setup.  It could be the reason that I'm printing quite a bit slower than my wife's windows connection to it.

Any luck with the drivers?

The driver works fine.  You need to get the queue name from the print server, not the printer.  So you have to go to your print servers IP (i.e. something like 192.168.0.10 or whatever you have it set to), and look at the configuration setting.  It is like configuring a router (it is done through a browser), but for the print server.  Once you get the queue name, you enter that in the printer configuration dialog.

---

### Post by DagMan on 2007-02-10
Thanks

---

