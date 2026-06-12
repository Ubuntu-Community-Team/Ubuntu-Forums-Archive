---
title: "Install Canon PIXMA MP970 on ubuntu 14.04"
date: 2014-06-18
forum: General Help
---

### Post by jimack327 on 2014-06-18
I just installed ubuntu 14.04 and am trying to set up my printer - a Canon PIXMA MP970 all-in-one. The printer is set up on the network rather than via USB.  I used the printer driver that comes with 14.04.  The printer appears to install okay, but I cannot print a test page.  The printer job starts, but then goes into a "held" state.  I can release it, but it goes right back into "held."  If I look at the printer in CUPS it shows "bjnp_backchannel: (recv) could not read response header, received 4 bytes!"  The URI that I used for the printer is bjnp://192.168.0.248:8611.  The scanner works fine with Simple Scan.  This printer works on 10.04 using TurboPrint.  Any suggestions?

---

### Post by pdc on 2014-06-18
If you click on this [http://localhost:631/admin](http://localhost:631/admin) and then click on the Add Printer button, you will be asked for username and password; username is usually > root and password is your sudo password;

if you follow the clicks, does  CUPS find your printer? Choose a new name that stands out from what exists after the first config; and if things work, delete the first config that doesn't work?

---

### Post by Bucky Ball on 2014-06-19
Like pdc said. 

You can also go to 'Printing>Add Printer>Network Printer'. Give it a second to look and it should show your printer. Follow your nose from there.

You will be asked to select a driver and the one you downloaded should be there (for your model under the Canon heading). 

As scanning is working and printing is not I'm wondering if you have the correct driver installed. But I presume this is the driver you were using in 10.04 LTS where everything was working fine. :-k

PS: In cups, my username/pw are the same as my login username/password. Never used 'root'.

---

### Post by jimack327 on 2014-06-19
When I click the Add Printer button CUPS shows my printer as Canon MP970 series 192.168.0.248 (Canon MP970 series).  I added a new printer with a different name, but I get the same error message - "bjnp_backchannel: (recv) could not read response header, received 4 bytes!"

---

### Post by jimack327 on 2014-06-19
I also tried using  'Printing>Add Printer>Network Printer' but the results were the same.  The printer driver is not the same one that I used with 10.04.  The printer database in 10.04 did not have an entry for my printer. So I purchased a third-party printer program - TurboPrint.  The printer database for 14.04 does have an MP970 driver, so I decided to use it, and hopefully save myself some money. I wonder if I have uncovered a bug.  I'd like to hear from anyone who has managed to get this printer working under 14.04.

---

### Post by Bucky Ball on 2014-06-19
So you did Printing>Add Printer>Network Printer. Did it find the printer? 

You used the correct driver from the database after that. Then what?

---

### Post by jimack327 on 2014-06-20
I found on bugs.launchpad.net/ubuntu Bug #1193094             [cups-backend-bjnp not working]("https://bugs.launchpad.net/ubuntu/+source/cups-bjnp/+bug/1193094")         .  So I installed the printer via USB - works fine.  I guess I'll have to wait for the bug to get fixed before I can use it over the network :(

---

### Post by Bucky Ball on 2014-06-20
> **jimack327 said:**
> When I click the Add Printer button CUPS shows my printer as Canon MP970 series 192.168.0.248 (Canon MP970 series).

This means your IP for the printer is changing everytime you switch either the printer or the computer off and on. You say CUPS can see the printer on the network. The main thing that's changing would be the IP. 

With my Brother, I had to set an IP address in the printer manually so devices on the network knew where it was every time. This can be a bit tricky. My router is set up to serve IPs via DHCP only in a certain range, then I can set static IPs outside of that range on each individual device. If you don't limit the range of the router's DHCP server with the static IPs outside of that it can get problematic. 

Just some thoughts ... :-k

---

### Post by jimack327 on 2014-06-20
No, the printer's IP is not changing.  It's set to a static IP of 192.168.0.248, which is outside the router's DHCP range.

---

### Post by jimack327 on 2014-08-13
I finally got the printer to work. I installed the version of TurboPrint that I bought many years ago (the latest version doesn't work with this printer). I ignored the message about it being poor quality software. The printer installed and is working just like it's supposed to.  I then uninstalled TurboPrint. Printer still works! I don't understand it, but I'm not going to argue with success.

---

### Post by Bucky Ball on 2014-08-15
> **jimack327 said:**
>  I don't understand it, but I'm not going to argue with success.

Good plan and good work!

Hopefully this will help future travellers. ;)

---

