---
title: "File/Printer Share with Win XP machines - How?"
date: 2006-10-23
forum: General Help
---

### Post by majortomm on 2006-10-23
I have been runnng Ubuntu for about a month now and I have been slowly moving away from the XP Pro on my dual boot desktop/file server machine.  The desktop has 4 hdd's, 1 dedicated xp pro, 1 dedicated ubuntu and 2 others that are partitioned into a few other various drives.  All partitions except the ubuntu are NTFS.  I have setup the NTFS access script thingy so I can access the files from ubuntu and all is working well that way.  The drives are shared throughout the network but when I am running ubuntu my other xp machines cannot access the files on the drives or the printer which is networked (usb hp printer that is shared).  

I am looking for a way to share the drives/files that are NTFS with the other xp machines when I am running ubuntu and for those same xp machines to be able to print using the shared printer.

I am a total *nix newbie so any and all recommendations are greatly appreciated :-D

---

### Post by progmanalpha on 2006-10-24
If you are running in KDE you can setup file sharing through Kmenu > System Settings then select sharing and set it up throgh that interface.  Make sure samba is active since that is what allows you to share with windows machines.  

If you are in Gnome then just go to the menu System > Administration > Shared Folders.  Here you can add the folders you want to share over the network and under general properties you can configure your windows share workgroup.

For sharing a printer:
In Gnome go System > Administration > Printing
Then when the Printers box appears click on Golbal Settings and select Share Printers. I think that should do it.

---

### Post by majortomm on 2006-10-24
Thanks for the great info!  With your help it looks like I have the files sharing between the computers!!  I never thought it would be that EASY! :D 

Unfortunately I do not see a "Share Printers" item anywhere in the printers section.  I have enven looked in the printer properties.  If I go into the Global Settings menu, th e only option is "Detect LAN Printers". (see screenshot)

---

### Post by kernalsanders on 2006-10-24
you have to sudo apt-get install smbfs and create smb users. You could use the guest option but this is what I consider bad practice. I also did sudo apt-get install cupsys* and the windows machine usually see the printer immediatly. I have to input the ip address most of the time for example in the Windows printer wizard looking for a network printer I put /192.168.x.x/printer_name. sometimes windows read it immediatly. Sharing folders is always easy but sharing a printer usually requires a little bit of work.

---

### Post by majortomm on 2006-10-24
Hmmm.. I guess I spoke to soon about the access to the files.  I thought it was working because I can go to Places->Network Servers->"WorkGroup Name" and see the other computers on the network.  However... when I go to one of the XP machines and view the computers on the network it is not seeing my Ubuntu machine :confused: 

I have done the System->Administration->Shared Folders and done the setup as listed in the previous post and setup the windows sharing option and workgroup name (see attached)

Until the XP machines can see me as part of the workgroup I cant get the printer to work :) 

Any thoughts on what I should try next?

---

### Post by fsman on 2006-11-02
> **progmanalpha said:**
> If you are running in KDE you can setup file sharing through Kmenu > System Settings then select sharing and set it up throgh that interface.  Make sure samba is active since that is what allows you to share with windows machines.  

If you are in Gnome then just go to the menu System > Administration > Shared Folders.  Here you can add the folders you want to share over the network and under general properties you can configure your windows share workgroup.

For sharing a printer:
In Gnome go System > Administration > Printing
Then when the Printers box appears click on Golbal Settings and select Share Printers. I think that should do it.

Any idea what Gnome System > Admin > printing - (Global settings - "share Printer"). What does the share printers do?

I only got print sharing with my windows box by editing manually the /etc/cups/cups.d/ports.conf file read like this:

#Listen 127.0.0.1:631
Listen *:631
Listen /var/run/cups/cups.sock

Then on the windows box

"In setting up the Windows computers on your network to access your Ubuntu machine's printer, the line given in the guide is:

[http://PRINTSERVERNAME:631/printers/PRINTERNAME](http://PRINTSERVERNAME:631/printers/PRINTERNAME)

"PRINTSERVERNAME" is the actual network ip address of your Ubuntu machine (e.g 192.168.0.2). "PRINTERNAME" is the name of your printer as it appears in the Printers folder in Ubuntu (in my case, it was Stylus-Color-900)."


Above works - but now the print share option in gnome is grayed out.

Anyone know what the print share option does in the gui - it would be good for moving desktop linux forward if we can get the gui working.

---

### Post by geekygreen on 2006-12-01
I tried to find Gnome > System>Admin>printing Global settings....all I get is a box to check for Detecting Network Printers.  IS there something else I  need to install?

I am tring to share a printer connected to the Ubuntu maching with my WIN XP laptop...without much success so far...

---

