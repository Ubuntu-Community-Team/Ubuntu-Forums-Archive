---
title: "Need help! Network Download Problem"
date: 2008-05-10
forum: General Help
---

### Post by quickwitt on 2008-05-10
I live in a rural area with no broadband but we do have a strong 3G signal from AT&T. As a result we tether cell phones for internet connectivity. Using wvdial and a USB cable I got my connection set up to my Motorola Razr V3xx with no problem using standard AT commands. The connection is much faster under Ubuntu 8.4 than XP or Vista. The problem is every download stalls after just a few hundred kilobytes. It isn't the connection because I can download fast and furious under Windows. I am posting from this connection. The problem is specific to the Linux environment. Any ideas?

here are the contents of wvdial.conf

Init1 = ATZ
Init2 = AT+CGDCONT=1, "IP", "WAP.CINGULAR"
Init3 = AT+CGATT=1
Init4 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem = /dev/ttyACM0
Modem Type = USB Modem
ISDN = 0
Baud = 921600
Stupid mode = 1
New PPPD = yes
Phone = *99#
Password = test
Username = test

Again, there are no connectivity issues. I can browse and even stream content at a pretty good speed. The problem is only with downloads.

Thanks in advance!

---

### Post by wrgb2 on 2008-05-10
You might try changing your download location - I had a lot of trouble downloading anything until I did this.  Go into System>Administration>Software Sources, click on the "Download from" listbox, choose "Other", then click on "Select Best Server".  This will run tests on all the possible download mirrors and pick the best one.  This might also give some indication what's wrong if it's something else.

---

