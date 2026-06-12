---
title: "Sagem F@st 800 with Ubuntu 7.10, how do I install it?"
date: 2007-11-09
forum: General Help
---

### Post by El Muelio on 2007-11-09
I need to get this to work, I have looked about but can't find any definitive answers, has a proper method been defined yet?

Thanks for any help.

---

### Post by El Muelio on 2007-11-09
Come on guys, I want to move over to Linux! This is the only thing holding me back on windows!

---

### Post by Maestro23 on 2007-11-09
Have you tried installing the Linux driver from the site yet? And if so, what errors did you get and how did you try to install it?

[http://www.sagem.com/support/site/modele_fax.php?page=driver](http://www.sagem.com/support/site/modele_fax.php?page=driver)

I believe your modem uses the eagle driver.  Here's a How-To for Ubuntu: [https://help.ubuntu.com/community/UsbAdslModem/EagleUsb?highlight=%28modem%29](https://help.ubuntu.com/community/UsbAdslModem/EagleUsb?highlight=%28modem%29)

Here's another support site for EagleUSB in Linux: [http://atm.eagle-usb.org/wakka.php?wiki=PagePrincipaleEn](http://atm.eagle-usb.org/wakka.php?wiki=PagePrincipaleEn)

---

### Post by Greasyfingers on 2007-11-09
I've not tried the F@st800 on 7.10, but here are some notes I made from using it on 7.04:

> To install Sagem F@st800:.

Download and copy the file ueagle-data-1.1.tar.gz from [http://eagle-usb.org/ueagle-atm/non-free/ueagle-data-1.1.tar.gz](http://eagle-usb.org/ueagle-atm/non-free/ueagle-data-1.1.tar.gz) into the home directory. 

Then, in a terminal:

$ tar -xvzf ueagle-data-1.1.tar.gz
$ sudo mkdir /lib/firmware/ueagle-atm
$ cd ueagle-data-1.1/
$ sudo cp -a * /lib/firmware/ueagle-atm

This extracts the firmware files and copies them to the appropriate location.

It may be necessary to unplug the modem and re-plug it. Wait for the light to stay on (if they don't restart the computer).

Configure the connection:

Open the file

$ gksudo gedit /etc/ppp/peers/ueagle-atm

and put the following text into it:

user "username"
plugin pppoatm.so 0.38
noipdefault
usepeerdns
defaultroute
persist
noauth

Save and Close

Note - the 0.38 number is probably specific to Tiscali in the UK, and represents the <VP> and <VC> numbers. You may need to find out these numbers for your own connection.

Now, enter this single line of text

"username" "*" "password" "*"

into both

/etc/ppp/chap-secrets and /etc/ppp/pap-secrets

Save and close each.

Turn on the connection:
$ pon ueagle-atm

Turn off the connection with:
$ poff

To make buttons to connect and disconnect:

Right click on panel or desktop and select Create Launcher. Title it 'Connect', Comment 'to internet', with the command pon ueagle-atm.

Make another one to disconnect in a similar way using the command poff -a (the -a option closes all incidences of a connection).

Panel applet Network Monitor will indicate whether the connection in on or off - set its properties to monitor ppp0 (restart may be necessary to bring this option up).

---

### Post by El Muelio on 2007-11-10
Hi, I havn't tried that method. According to my package installer (?) I have got eagle-usb installed, but when I run eagle config, I enter my Usernamer and password, then there are two other options for encrypted server [y/n] and whether to connect on startup [y/n] when i go past these, I get the error /usr/sbin/eagle config: illegal operation.

I shall try that method, thanks.

---

### Post by El Muelio on 2007-11-13
Tried that method, when I get to the bit where I have to enter my username and password into those two files, its says access denied.

Any ideas about how I can make it grant me access?

---

### Post by plucky on 2007-11-13
> Any ideas about how I can make it grant me access? 

Those files are owned by root so you need to give yourself root privilege

Try

```
 gksudo gedit /etc/ppp/chap-secrets
```

and 

```
 gksudo gedit /etc/ppp/pap-secrets 
```

---

### Post by myle on 2007-11-18
> To install Sagem F@st800:.

Download and copy the file ueagle-data-1.1.tar.gz from [http://eagle-usb.org/ueagle-atm/non-...ata-1.1.tar.gz](http://eagle-usb.org/ueagle-atm/non-...ata-1.1.tar.gz) into the home directory.

Then, in a terminal:

$ tar -xvzf ueagle-data-1.1.tar.gz
$ sudo mkdir /lib/firmware/ueagle-atm
$ cd ueagle-data-1.1/
$ sudo cp -a * /lib/firmware/ueagle-atm

This extracts the firmware files and copies them to the appropriate location.

It may be necessary to unplug the modem and re-plug it. Wait for the light to stay on (if they don't restart the computer).

Configure the connection:

Open the file

$ gksudo gedit /etc/ppp/peers/ueagle-atm

and put the following text into it:

user "username"
plugin pppoatm.so 0.38
noipdefault
usepeerdns
defaultroute
persist
noauth

Save and Close

Note - the 0.38 number is probably specific to Tiscali in the UK, and represents the <VP> and <VC> numbers. You may need to find out these numbers for your own connection.

Now, enter this single line of text

"username" "*" "password" "*"

into both

/etc/ppp/chap-secrets and /etc/ppp/pap-secrets

Save and close each.

Turn on the connection:
$ pon ueagle-atm

Turn off the connection with:
$ poff

To make buttons to connect and disconnect:

Right click on panel or desktop and select Create Launcher. Title it 'Connect', Comment 'to internet', with the command pon ueagle-atm.

Make another one to disconnect in a similar way using the command poff -a (the -a option closes all incidences of a connection).

Panel applet Network Monitor will indicate whether the connection in on or off - set its properties to monitor ppp0 (restart may be necessary to bring this option up).

I have tried it and it worked but there is problem. To be connected to the internet, I have to try many times, by plugging and unplugging the modem till the execution of the
```
pon ueagle-atm
```
stops output
> Plugin pppoatm.so loaded.
Using interface ppp0
Connect: ppp0 <--> 8.35
LCP: timeout sending Config-Requests
Connection terminated.
Modem hangup


and connect to the internet.

How can I solve it?

---

