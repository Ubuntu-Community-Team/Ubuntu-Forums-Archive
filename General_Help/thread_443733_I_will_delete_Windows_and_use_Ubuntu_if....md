---
title: "I will delete Windows and use Ubuntu if..."
date: 2007-05-14
forum: General Help
---

### Post by nerdman978 on 2007-05-14
Ok I have used Ubuntu, preferably over my Windows partition, and I love it. There are a few remaining things I want to fix; however, before I permanently delete my Windows partition. 
Here they are:

Get this wireless card to work: Broadcom Corporation BCM4306 802.11b/g Wireless LAN 
Get 3D acceleration for this card: ATI mobility Radeon 9000:
Configure Evolution mail for my gmail account.

My computer is the Dell Latitude D600 if that helps.

---

### Post by floke on 2007-05-14
For the wireless try this

[http://ubuntuforums.org/showthread.php?t=405990&highlight=4306](http://ubuntuforums.org/showthread.php?t=405990&highlight=4306)

pure genius!

The third I know can definitely be done (since I've done it), but I can't remember off the top of my head and I'm tired, so will post it sometime tomorrow if no-one else has done it by then.

---

### Post by Espreon on 2007-05-14
For the Wireless card try Ndiswrapper:

open Syntapic and search ndiswrapper and select to install ndiswrappergtk, ndiswrapper common and ndiswrapper utilities 1.9

hit apply, then find the driver over the Internet, it should be an .ini file, then download it
after that goto System>Administration>Windows Wireless Drivers
then hit install driver. then goto where you stowed the driver, hit it. Then hit ok
reboot and (maybe) enjoy

For the graphics card
open Synaptic and search 4 fglrx and select xorg-driver-fglrx
and hit apply
reboot and enjoy

as 4 the gmail account:

create a new account in Evolution
fill all the info in until you get to the part where it asks 4 POP
type in pop.gmail.com
get 2 the section where it asks 4 SMPT
type in smtp.gmail.com

or try Thunderbird +Lightning

to make it simple get automatix
google it

then install it
then click Thunderbird 2.0
then hit start
wait it to install Thunderbird
then open Thunderbird
when it asks 4 your account info hit Gmail,  next
enter your info til you reach where it asks for POP
enter pop.gmail.com
next
4 SMPT hit smtp.gmail.com
next until it gits out of account setup
then hit Edit>Account Settings>Server Info
hit SSL
then goto SMTP and click the SMTP and edit change the port to 587 and hit TLS and hit OK.

and you are good 2 go

---

