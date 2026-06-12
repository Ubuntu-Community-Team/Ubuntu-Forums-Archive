---
title: "Print Server with Ubuntu 7.10, Samba &amp; CUPS"
date: 2007-12-17
forum: General Help
---

### Post by Stryker_31415 on 2007-12-17
I have Gutsy Gibbon installed. Also have a local printer (Brother HL-1230) connected to the box. Printer works as expected as local from Ubuntu 7.10. 

I wish to share the printer over my peer to peer network with several MS Windows boxes. Have attempted to achieve this using SWAT & direct editing of smb.conf to configure. Although the Windows boxes can see and access the Samaba disk shares, they cannot see the printer.

How can I share the Ubuntu printer over the network with Windows boxes?

Any suggestions gratefully received.

Stryker

---

### Post by bristleburger on 2007-12-17
The printer section of my smb.conf file looks like this:

[printers]
   comment = All Printers
   browseable = yes
   path = /tmp
   printable = yes
   public = yes
   writable = no
   create mode = 0700


BB

---

### Post by Stryker_31415 on 2007-12-17
Thanks, Bristleburger.

I modified smb.conf per your suggestion and restarted both samba and cupsysd. Regretfully no improvement. 

Any other suggestions?

Stryker

---

### Post by bristleburger on 2007-12-17
Sorry it didn't work.

This is everything that appears to be related to printing in my smb.conf file:

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
   printing = cups
   printcap name = cups

# When using [print$], root is implicitly a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
;   printer admin = @lpadmin

[printers]
   comment = All Printers
   browseable = yes
   path = /tmp
   printable = yes
   public = yes
   writable = no
   create mode = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = yes
   public = yes
   printable = yes

Before being able to print from a windows host, I first have to connect to a Samba file share (entering my Samba user name and password).

BB

---

### Post by Stryker_31415 on 2007-12-18
BB

Thanks for your expanded reply. I'll get your suggestions banged in this afternoon and let you know how they work out.

Stryker

---

