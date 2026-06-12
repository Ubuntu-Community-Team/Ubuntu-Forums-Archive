---
title: "Need Help sharing Ubuntu Printer with OSX Tiger"
date: 2006-07-20
forum: General Help
---

### Post by kapkorn on 2006-07-20
I have an Ubuntu machine running 6.06 the printer is an HP Laserjet 1020 (which was a challenge to get working anyhow) which I am trying to share with my Mac OS X 10.4 Macbook. I changed the CUPS file to allow from the correct network range.


However either it isnt working or I am misunderstanding as it does NOT show up as a network printer for the list on my Mac.


Is there anything special I need to do on the Mac side of things to get this to connect VIA CUPS?

---

### Post by andy_cowman on 2006-07-20
WIth CUPS if the printer works then it should share it easily. Have you reverted to the web interface for CUPS? I updated my CUPs to the latest from the website when I did it due to sharing issues ( i have 1.2.1 not sure what the latest is now!) and then somewhere found this config file which I made a few additions to! Tailor it to your network settings and hopefully you will be ok!! Then you need to set up printer to point to something like this on the othe machine (i was on XP). I think its an HTTP printer where 10.0.0.4 is the host machines IP addy and Photo4x6 is the printer name.

[http://10.0.0.4:631/printers/Photo4x6](http://10.0.0.4:631/printers/Photo4x6)


Here is my cupsd.conf file. Its ripped partly from another post or site somewhere but my apolagies as i cant remember where it came from!



 # /etc/cups/cupsd.conf
    # Simple CUPS configuration file for a print server
    # which serves printers within a private local area network.
    # - There is no need for additional security within the print server, ie only authorises people can access the machine.
    
    # This setup also allows access to the CUPS "Administrative tasks" system
    # via your web browser to [http://localhost:631](http://localhost:631)
    # File based on Ubuntu 5.10 (Breezy Badger) (Linux version 2.6.12-10-386)
    # Server Directives are explained in [http://localhost:631/sam.html](http://localhost:631/sam.html)
    
    # 25/04/2006
    # [email]DavidTangye@netscape.net[/email]
    
    ConfigFilePerm 0600
    LogLevel info
    Printcap /var/run/cups/printcap
    RunAsUser Yes
    Port 631
    Include cupsd-browsing.conf
    BrowseAddress @LOCAL
    BrowseAddress 10.0.0.0/8
    BrowseAddress 172.16.0.0/12
    BrowseAddress 192.168.0.0/16
     
    <Location />
    AuthType None
    Order Deny,Allow
    Deny From All
    Allow From @LOCAL
    Allow From 10.0.0.0/8
    Allow From 172.16.0.0/12
    Allow From 192.168.0.0/16
    </Location>
    
    <Location /jobs>
    AuthType None
    Order Deny,Allow
    Deny From All
    Allow From @LOCAL
    Allow From 10.0.0.0/8
    Allow From 172.16.0.0/12
    Allow From 192.168.0.0/16
    </Location>
    
    <Location /printers>
    AuthType None
    Order Deny,Allow
    Deny From All
    Allow From @LOCAL
    Allow From 10.0.0.0/8
    Allow From 172.16.0.0/12
    Allow From 192.168.0.0/16
    </Location>
    
    <Location /admin>
    AuthType None
    Order Deny,Allow
    Deny From All
    Allow From @LOCAL
    Allow From 10.0.0.0/8
    Allow From 172.16.0.0/12
    Allow From 192.168.0.0/16
    </Location>



Also I set SAMBA to share printers aswell. Here is my SMB.conf file which might be useful to you to ensure the printers are being broadcast. Not sure this is technically needed but I have it.



[global]
guest ok = yes
security = share
workgroup = MSHOME
smb passwd file = /etc/smbpasswd
#logon script should go in netlogon directory
#below you will find a example of this
server string = Samba Server
load printers = no
printcap name = /etc/printcap

# Un-comment the following to provide a specific roving profile share
# the default is to use the user's home directory
wins support = no
[Photos]
    path = /home/john/
    browseable = yes
    guest ok = yes
# NOTE: If you have a BSD-style print system there is no need to
# specifically define each individual printer
#[printers]
    ;comment = All Printers
    ;path = /var/spool/samba
    ;browseable = yes
# Set public = yes to allow user 'guest account' to print
    guest ok = yes
   writable = yes
   printable = yes

[MyDocuments]
path = /home/john
available = yes
browseable = yes
public = yes
writable = yes
guest ok = yes



Hope this is of some use to you. This setup will work for VMPlayer aswell but its a bit slower to spool the data. Its basically immediate from my other linux box on my network.

Andy

---

### Post by kapkorn on 2006-07-24
That helped a lot, I got it working now finally, but it just seems really slow to print and respond printing from my Macbook to the Ubuntu desktop. It is only slow this way, if you print on the ubuntu machine directly it is very fast.

---

### Post by andy_cowman on 2006-07-25
interesting, there must be a way of speeding it up but i am not sure what it is. If you work it out let me know because it will speed up printing from my virtual machine. I am gonna have another play with it aswell and see if i can work out what it is.

Andy

---

### Post by edm00se on 2006-08-24
Is there an update for this to use with Dapper? I tried just plugging it in and didn't work out, so I restored my backups of the files. I do have cupsd and samba installed.
  I'm looking to do exactly the same thing, share my printer from my ubuntu box to a PowerBook running OS X Tiger. Only thing that seems different to me is that this was written for Breezy and I'm running Dapper.

---

### Post by stmiller on 2006-09-15
No changes for Dapper. Thanks for the cupsd.conf file, Andy. It works great for me!

---

### Post by Regina on 2007-02-12
Ok.. looks like my problem is a bit more complicated than this...  I did the change on the cups.conf like is written down in the previous post and tried this option too:

[http://linuxprinting.org/~till/printing-tutorial/tut.html](http://linuxprinting.org/~till/printing-tutorial/tut.html)

However, whenever I do that change, the printer stops working on Ubuntu, and of course then it is not recognized by the Mac.   That happens irrespectivly whether I restart the CUPS daemon or not.

Anyway, with the original cups.conf it works just fine for the ubuntu... But I'm not able to see it on the Mac.  I'm totally clueless and in the edge to throw the Mac through the window.... so any suggestion will be appreciated!

thanks!

---

### Post by VanHammersly on 2007-02-17
Hey.  It may not be that tricky.  Tiger hides SMB print options.  

To connect to a SMB printer from your Mac do the following:

    * From System Preferences, select "Print & Fax"
    * Click the + sign to add a printer
    * While holding down the Option key, click "More Printers..."
    * Select "Advanced" from the drop-down menu
    * Select "Windows Printer via SAMBA" in the "Device" menu
    * For "Device Name" enter a name to identify the printer
    * For "Device URI" enter: smb://username:password@physics.harvard.edu/printername
      (For mine, it is my linux box's IP address/HomePrinter For example: smb://192.168.1.5/HomePrinter)
    * Select the printer model (if not found, select 'Generic' or the printer model if available)
    * Click "Add"

---

