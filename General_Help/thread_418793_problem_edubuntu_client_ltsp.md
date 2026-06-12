---
title: "problem edubuntu client ltsp"
date: 2007-04-22
forum: General Help
---

### Post by miguelito on 2007-04-22
hi!

I installed edubuntu server 7.04, test de server booting for lan on my laptop and no problem. But try to the client and no have display.

client:
MB: asus SP97-V
cpu: pentium 200mmx
ram: 32mb
hdd:4gb
integrated video: chip sis 5597

i don't have idea who config the video on client. plz help! :( 

sorry for my english :lolflag:

---

### Post by peckman12 on 2007-04-28
I am having this problem as well.  I see the Ubuntu screen like it is working and then nothing just a cursor.

BTW, I am running this in VMWARE for both the client and the server and my lts.conf has XSERVER=vmware.

In addition to the VMWARE client problems I tried this on an HP and still the same issue.

---

### Post by ernierasta on 2007-04-28
I think it can be some problems with resolution of client screen, if I will find way how to change it, I will let you know.

And question: Can you see login screen?

---

### Post by peckman12 on 2007-04-28
No login screen just a cursor.

This also happens on many different computers and monitors.

---

### Post by peckman12 on 2007-04-29
YOU MUST CORRECT THE SETUP LTSP DOES NOT SUPPORT THE WAY OPTION 17 is in other messages.
JUST REMOVE THE IP LIKE BELOW!  I was having a video problem before this.

Identified, it was not a video problem it was looking for a none existent NFS mount.  Press <CTRL><ALT><F1> 
You will see it looking for the NFS mount.

Just add the following on your client reservations:

NOTE: You may be able to set some of these on the scope, but I know they work when you add all of them directly on the reservation.

NOTE: These must be placed at the client reservation level to work.

17 Root Path - /opt/ltsp/i386
66 Boot Server Host Name - 192.168.1.100
67 Bootfile Name- /ltsp/i386/pxelinux.0

---

### Post by smhickel on 2007-05-03
I see about four posts within the last 24 hours for this same problem, all discussing the ltsp client as not allowing a full boot for the client. Either the screen has a blinking cursor or the screen has just a text login that blanks in and out about every few seconds. Yet, you get the ubuntu splash screen during most of the boot up. Anybody have any ideas?

Here is our /etc/ltsp/dhcpd.conf file:

subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.150 192.168.1.155;
  option domain-name "yourdomainhere";
  option domain-name-servers 192.168.1.50;
  option broadcast-address 192.168.1.255;
  option routers 192.168.1.69;
  option subnet-mask 255.255.255.0;

 
  filename "ltsp/i386/pxelinux.0";
  option root-path "/opt/ltsp/i386";
}

---

### Post by ipguru99 on 2007-05-03
this is mine (/etc/ltsp/dhcpd.conf) from Xubuntu running ltsp:

authoritative;

subnet 192.168.15.0 netmask 255.255.255.0 {
  range 192.168.15.136 192.168.15.150;
  option domain-name "test-network.local";
  option domain-name-servers 192.168.15.4;
  option broadcast-address 192.168.15.255;
  option routers 192.168.15.1;
  option subnet-mask 255.255.255.0;
  if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
    filename "/ltsp/i386/pxelinux.0";
  }
  else{
    filename "/ltsp/i386/nbi.img";
  }
  option root-path "/opt/ltsp/i386";
}


I am using Virtualbox.  I have a guest running ltsp server (Xubuntu) and another guest running a PXE client from a .iso file over at rom-o-matic.net (life savers if you need to test pxe stuff!).  I made the mistake of trying to edit /etc/dhcp3/dhcpd.conf file for about 2 hours before realizing that this isn't the file to edit ;-)

smhickel, the only difference I see between our files is that your second to last line in the file doesn't have a leading slash before ltsp... but I don't know if that matters.

ipguru99

Oh yeah, it works ;-)

---

### Post by smhickel on 2007-05-03
Took me a while to figure that / thing was not needed. 

Glad you go it going. 

The issue I was having is not that LTSP client does not work. It does, just not on my notebook. I have it working on two machines but not the one I wanted it to work on.

---

