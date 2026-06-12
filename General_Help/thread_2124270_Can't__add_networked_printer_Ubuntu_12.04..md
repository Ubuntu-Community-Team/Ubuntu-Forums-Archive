---
title: "Can't  add networked printer Ubuntu 12.04."
date: 2013-03-10
forum: General Help
---

### Post by daldude on 2013-03-10
I can't add my Konica Minolta Magi Color 2300dl Network printer in Ubuntu 12.04, when I try to add it Ifirst in the add printer box it displays a message                       

   **FirewallD is not running. Network printer detection needs services mdns, ipp, ipp-client and samba-client enabled on firewall.**

and then when I select Network and then click Add I get this error 

**Unknown Error, please report bug. More infomation is avalible in the detailed report. Query type 'postscript' is not supported**.

Where do I find this** "detailed report"** and where and how do I report the bug and / or how do I fix this problem?

This seems to be the first time I had this problem with 12.04 because I do not remember having this problem when I installed 12.04 before.
I got a new hard drive and had to reinstall 12.04 on it and that is why I reinstalled.

---

### Post by Easy Limits on 2013-03-10
Try from the terminal, system-config-printer.  This worked for me when adding a networked printer in 12.04.

---

### Post by SeijiSensei on 2013-03-10
I find it's often easier simply to use the CUPS web interface.  Try opening [http://localhost:631/](http://localhost:631/) on the Ubuntu client.  You'll be prompted for your password information if you choose an action like adding a printer that requires root privileges.  Enter your username and password just like you would to run something with "sudo".

---

### Post by Morbius1 on 2013-03-10
> **Easy Limits said:**
> Try from the terminal, system-config-printer.  This worked for me when adding a networked printer in 12.04.
That's the gui fix since system-config-printer is a Gnome2 utility. The FirewallD error is a Gnome3 bug. FYI: FirewallD is a RedHat daemon that has nothing to do with Debian or any of it's derivatives so it shouldn't be a surprise it couldn't find it.

---

### Post by daldude on 2013-03-10
That worked Thanks:D
That is exactly the same as it was in 10.04 and what I thought was in 12.04 when I had it installed on my old hard drive.

Is there a way to access this from the system settings via clicking on a icon like in 10.04 or was I just not looking hard enough in system settings to find the icon to add a printer other then the printer icon in "**All Settings**" (see attached image)


> **Easy Limits said:**
> Try from the terminal, system-config-printer.  This worked for me when adding a networked printer in 12.04.

---

### Post by daldude on 2013-03-10
Now that I've solved the problem how do I mark this posting Solved?:confused:

---

### Post by Gink on 2013-03-10
Why does this problem happen? I've had my network printer working with Gnome desktop in 12.04 since I first installed 9 months ago, then all of a sudden it is gone, undetected with the FirewallD error. I'm guessing some update or the other broke it?

---

### Post by kurt18947 on 2013-03-10
"system-config-printer" is in the repositories and works fine in 13.04 and 12.10.  The 'printers' app that is native is too crippled to be of any use IMO.

---

