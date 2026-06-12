---
title: "reset usb persistant mode"
date: 2007-12-24
forum: General Help
---

### Post by johnnyz86 on 2007-12-24
so i am running ubuntu 7.10 from a usb drive in usb persistant mode, however the wireless wasn't working (e1505 intel 3945abg).  i ve tried tons of things and well i think i want to reset my install.  can i just delete the partition it is running off of (casper-rw) and it will act like new?

lastly, does my card work out of the box? running it as a live cd, it lists my network card under restricted driver manager with a check next to it, but it says not in use.  all the network stuff i have found does not list anything about wireless, there is no wireless network manager, nothing that even trys to search for a network.  

how do i get this working? i've tried various tutorials and probably messed up stuff which is why i want to restart.

im eyeing this one:
[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

and instead of downloading the dell driver, using the dell intel wireless driver.  or do i even need to do that because i shows up in restricted drivers and is reported to work out of the box.  edit: now in livecd mode it says in use, but still nothing to the effect of showing networks.  in network settings, there is only wired connection and modem connection.

it detects 2 ethernet adapters, eth0, and eth1

i've tried putting in network interfaces:

auto eth#
iface eth# inet dhcp

and restarting the network but they both time get nothing.

i've tried using iwconfig eth1 up, but up isnt even a command anymore?

i manually typed in the essid in, and now iwconfig shows that it is connectd but the internet still doesn't work

typing NetworkManager gives me nothing as root.

ok so i'm not sure what happened but now wireless shows up under networkmanager so it all works and now all i need to do is reset usb persistant mode.

---

### Post by DoctorMO on 2007-12-24
Most of the network restricted drivers are not drivers but firmware. Sometimes it's an ndis driver and that is where you need to install the windows version of the driver within ndis.

---

### Post by johnnyz86 on 2007-12-24
ok so i figured out the probably must've been ctrl+f2 (enabling wireless) because well i cant really tell if it is on before i get into ubuntu because the light stays off either way.

anyways, back to resetting usb persistant mode, how? 

ok well looking back at the tutorial [http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/) 

the only thing they do to the casper-rw drive is format it, so i think i can jut reformat it / delete it.  however, i have a couple of questions:

i want to use this as a flash drive still, and making casper-rw take up the rest wil just make it unreadable to windows machines.  can i format casper-rw as a fat16/32 drive and still have ubuntu use it as a peristan linux drive and write o it in windows as a regular flash drive? can , when using ubuntu in live cd usb pen drive mode, adjust the partition size of the livecd portion with gparted ? reason being, theres a couple mb's free on it right now, and if i can tmake casper-rw fat, then i'd want to make the livecd portion bigger because that is in fat and can be accessed on windows machines as well.  however, i fear that it will just make ubuntu crash because it is running livecd from that very same usb drive.

thanks.

---

### Post by johnnyz86 on 2007-12-24
any ideas?

---

