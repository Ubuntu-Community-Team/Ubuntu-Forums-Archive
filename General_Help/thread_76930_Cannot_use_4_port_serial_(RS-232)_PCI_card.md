---
title: "Cannot use 4 port serial (RS-232) PCI card"
date: 2005-10-15
forum: General Help
---

### Post by nemik on 2005-10-15
Hello,

I did a fresh base install of Breezy on a celeron box with one built-in serial port and this PCI port attached to the motherboard: [http://cgi.ebay.com/NEW-SYBA-PCI-32-Bit-Quad-9-pin-4-Port-Serial-Card_W0QQitemZ5792562374QQcategoryZ64458QQssPageNameZWD1VQQrdZ1QQcmdZViewItem](http://cgi.ebay.com/NEW-SYBA-PCI-32-Bit-Quad-9-pin-4-Port-Serial-Card_W0QQitemZ5792562374QQcategoryZ64458QQssPageNameZWD1VQQrdZ1QQcmdZViewItem)

it is a 4 serial port PCI card. trying an app that uses the port on the built-in serial port /dev/ttyS0 works fine. but trying /dev/ttyS1, /dev/ttyS2...and so on does nothing, they just don't work.

How can get them to be detected?

Thank you very much!
-nemik

---

### Post by nemik on 2005-10-16
well i managed to figure it out. turns out the PCI card was detected and i just wasn't watching the startup log output as much as i should have. it assigned the ports to ttyS14, ttyS15, ttyS50, and ttyS51. using those ports then worked perfectly!

hope this helps anyone who was having a similar problem.

---

### Post by sylvester_0 on 2005-10-16
Good for you! I'm curious as to what you even use serial ports for, and why so many? I haven't touched a serial device forever and many computers don't even have legacy (serial, parallel) ports anymore. Maybe it's time to upgrade?

---

### Post by nemik on 2005-10-17
well they are running on an old computer and i use them to communicate with mobile phones that act as a cluster together in a sense to send and recieve data and text messages.

---

