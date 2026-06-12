---
title: "Hplip error."
date: 2017-07-09
forum: General Help
---

### Post by 1askman on 2017-07-09
Hello! I've got some bad news.

I tried installing hplip-3.17.6, and guess what!? I didn't succeed it said: "Package install command failed with error code 100".

Can any of you hardcore nurdz help a fellow out?

---

### Post by ajgreeny on 2017-07-09
How did you install hplip?  Was it done from the usual repos or  did you download the **hplip-3.17.6.run** file from hplip direct?

---

### Post by 1askman on 2017-07-09
> **ajgreeny said:**
> How did you install hplip?  Was it done from the usual repos or  did you download the **hplip-3.17.6.run** file from hplip direct?

Yes, I did download it from the hplip, and ran it on terminal.


Additional info: I am trying to run it on Ubuntu 16.04.

---

### Post by ajgreeny on 2017-07-09
Do you have the universe and multiverse repositories enabled as they are necessary for some of the dependencies of hplip?

---

### Post by Ralph L on 2017-07-09
Here are my notes from my recent installation of an hp printer under Xubuntu 17.04:
35 Install hplip.  Hplip was already installed on xubunutu 16.04 so I used:
hp-setup -i 10.0.0.15 (note that 10.0.0.15 is the ip address of my printer)
35.1 This resulted in a torrent of errors.
35.2 However, the printer and the fax both seemed to have been installed.
35.3 Reverse Order Printing.  In System Settings, select Printers. Then right-click on the individual printer you want to change and go to Properties. Select Job Options from the right hand side, then under Common Options click the arrow next to More. Finally there will be a setting Output order, which can be changed to Reverse.

Note the use, under Terminal, of hp-setup -i ipaddress
Hope this helps.

---

### Post by 1askman on 2017-07-10
> **ajgreeny said:**
> Do you have the universe and multiverse repositories enabled as they are necessary for some of the dependencies of hplip?

Sorry, I don't know. How can I know that? :(

---

### Post by 1askman on 2017-07-10
> **Ralph L said:**
> Here are my notes from my recent installation of an hp printer under Xubuntu 17.04:
35 Install hplip.  Hplip was already installed on xubunutu 16.04 so I used:
hp-setup -i 10.0.0.15 (note that 10.0.0.15 is the ip address of my printer)
35.1 This resulted in a torrent of errors.
35.2 However, the printer and the fax both seemed to have been installed.
35.3 Reverse Order Printing.  In System Settings, select Printers. Then right-click on the individual printer you want to change and go to Properties. Select Job Options from the right hand side, then under Common Options click the arrow next to More. Finally there will be a setting Output order, which can be changed to Reverse.

Note the use, under Terminal, of hp-setup -i ipaddress
Hope this helps.

This is the result of sudo apt install hplip on my system: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 hplip : Depends: cups (>= 1.1.20)
         Depends: printer-driver-hpcups (= 3.16.3+repack0-1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

:(

---

### Post by Ralph L on 2017-07-10
I installed my hp printer on a test xubuntu 17.04 OS on which I hadn't installed the printer on previously.  All I did was enter the command "hp-setup -i 10.0.0.15" (no sudo), answer the questions, and it installed.  There were a ton of errors, but the printer still installed and I printed a page with mousepad.  hplip was already in the downloaded OS so I didn't install anything else.  Maybe you can do an uninstall of hplip and reinstall it.  In fact synaptic has a reinstall option on its right-click menu.  I don't know if this reinstalls all the dependencies.  However, by right-clicking on hplip in synaptic, selecting properties, and selecting the dependencies tab, you can view all the dependencies.  One of the dependencies is cups (>= 1.1.20).  Another is printer-driver-hpcups (= 3.16.3+repack0-1).  Maybe check in synaptic to see if those are installed, and install them if they are not.  I checked in synaptic on my system and they were already installed on the release system.

---

