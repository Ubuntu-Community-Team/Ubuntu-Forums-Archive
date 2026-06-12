---
title: "Installing Network Printer"
date: 2008-06-19
forum: General Help
---

### Post by Nitewalker on 2008-06-19
I have a printer attached to a tower computer via usb cable and I want to be able to print from it from my wireless laptop.  I can ping both directions, and the printer is marked to share.  When I go to system/admin/printing and try and install a new printer it does not show.  If I mark to install using "ipp" and make the "host=ipp://192.168.0.111:631 and then make the "queue=/printers/HP Photosmart D7100 series [same as listed on tower] and then click to verify I get an error saying "print share not accessible".  Both computers are using Ubuntu 8.04:confused:

---

### Post by plucky on 2008-06-20
On your laptop, go to server settings and tick the box that says **Show printers shared by other systems**.Exit from the GUI and restart the GUI.
It should then go out and look for printers on your network that are shared.


That is all you need to do.

Also make sure you can see your desktop go to **Places > Network** to see if you can see your desktop machine.


Good Luck

---

### Post by Nitewalker on 2008-06-20
Did not do anygood when restarting GUI still did not find it, and when I went to "places/network" it brought up a GUI for "Windows Network" and when clicked went nowhere:confused:

---

### Post by plucky on 2008-06-20
> **Nitewalker said:**
> Did not do anygood when restarting GUI still did not find it, and when I went to "places/network" it brought up a GUI for "Windows Network" and when clicked went nowhere:confused:

Can you at least see your laptop network name?

From a terminal post output of ```
cat /etc/hosts
```

Open your browser and input ```
http://127.0.0.1:631/
``` into the address bar.This will open the CUPS home page.See if you can find new printers from the ADMIN tab.


Good Luck

---

### Post by Nitewalker on 2008-06-20
The printer is attached to 192.168.0.111;
1st etc/hosts is from my laptop, the one I want to add the printer to, the 2nd etc/hosts is from my desktop that the printer is attached to.

nitewalker@smj:/etc$ cat hosts
127.0.0.1 localhost
127.0.0.1.1 smj
192.168.0.110 smj.homeip.net smj
192.168.0.111 smj2.homeip.net smj2

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
192.168.0.100 smj.home.net smj
nitewalker@smj:/etc$ 
______________________________________________________________

nitewalker@smj2:~$ cd /etc
nitewalker@smj2:/etc$ cat hosts
127.0.0.1 localhost
127.0.0.1.1 smj2
192.168.0.110 smj.homeip.net smj
192.168.0.111 smj2.homeip.net smj2

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
192.168.0.111 smj2.homeip.net smj2
nitewalker@smj2:/etc$ 
______________________________________________________________
When I went to cups page and tried to locate a printer from admin tab it said no printers found

---

### Post by avtolle on 2008-06-20
Stupid question here, but are you trying to add the printer as a network printer, and not a local printer, on the laptop?

---

### Post by plucky on 2008-06-20
> 127.0.0.1 localhost
127.0.0.1.1 smj2
192.168.0.110 smj.homeip.net smj
192.168.0.111 smj2.homeip.net smj2

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
192.168.0.111 smj2.homeip.net smj2


I have never see a host file that looks like yours.

My host file looks like 
> 127.0.0.1	localhost
127.0.1.1	Ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

How did you set up your network?

Did you setup those IP addresses?

Are you using Static IP addressing?

---

### Post by Nitewalker on 2008-06-20
Yes I am trying to add it as a network printer, as it is on my desktop upstairs:

My network does have static addresses assigned to the 2 computers, they are set up for use with my Apache2 Server which is on the desktop.  I chose the addresses based on knowing that with only 2 computers attached to the router that the Dynamic addressing will never reach 110 or 111.

---

### Post by plucky on 2008-06-21
> **Nitewalker said:**
> Yes I am trying to add it as a network printer, as it is on my desktop upstairs:

My network does have static addresses assigned to the 2 computers, they are set up for use with my Apache2 Server which is on the desktop.  I chose the addresses based on knowing that with only 2 computers attached to the router that the Dynamic addressing will never reach 110 or 111.

Open your Internet browser and in the address bar put ```
http://localhost:631
```.
This should open the cups interface on your laptop.

If that works then put ```
http://192.168.0.111:631/
``` and see if it opens the cups interface on your desktop.

If that works,then you know the two systems are at least communicating and can see each other.


Good Luck

---

### Post by doug1212 on 2008-06-21
Hi,
Do you have samba server installed and set up for printing from windows?

Doug.

---

### Post by Nitewalker on 2008-06-21
Yes I can reach both localhost:631 on my laptop and 192.168.0.111:631 from my laptop, and get the cups page.  Tried to add printer from there but not luck.

Yes I do have Samba installed and it does show the printer as being on the desktop computer, and when I try to verify it in the system/admin/printers set up using Windows printer via Samba and then try and veriy it I get an error saying it cant communicate. The printer uri is smb://MSHOME/SMJ/HPPhotos7100:confused:

---

### Post by plucky on 2008-06-22
> The printer uri is smb://MSHOME/SMJ/HPPhotos7100



Shouldn't that be > smb://MSHOME/[color=red]SMJ2[/color]/HPPhotos7100


As the two systems are communicating,I would delete the printer you added and try to add it again,but this time,let cups try to add the printer.This might not succeed the first time so just keep trying again.

Could there be something like a firewall on the desktop that is preventing the printer being seen on the network?
Did you enable network sharing on the printer?
Very fast running out of ideas here.

Good Luck

---

