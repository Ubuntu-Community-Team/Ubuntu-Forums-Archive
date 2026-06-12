---
title: "firestarter firewall"
date: 2005-10-15
forum: General Help
---

### Post by waldorf on 2005-10-15
Do people think its necessary to install firestarter or some other kind of firewall?

---

### Post by majikstreet on 2005-10-15
[QUOTE=waldorf]Do people think its necessary to install firestarter or some other kind of firewall?[/QUOTE]
I personally *don't* have a firewall, but I should. I really should. I run a server and when I couldn't log into it today, I was afraid it got hacked.

Run a firewall for safety and your own piece of mind. 
It's extra protection against hackers.
majikstreet

---

### Post by daschl on 2005-10-15
it depends on what you want to do :)

if you want to run services on your box, its not a bad idea to run a firewall (if you already dont have one)
But think about the "problem" that a firewall is not a virus-scanner.


if you use your box only as a desktop-system - in my opinion - there is no need for a firewall

regards,
mike

---

### Post by ToastedToad on 2005-10-15
Someone please correct me if I'm wrong here, but i believe that iptables is always running, and packages like Firestarter and Guarddog, are just frontends to iptables, They just make em easier to manipulate.

---

### Post by az on 2005-10-15
[QUOTE=ToastedToad]Someone please correct me if I'm wrong here, but i believe that iptables is always running, and packages like Firestarter and Guarddog, are just frontends to iptables, They just make em easier to manipulate.[/QUOTE]
Right, but that does not mean that there are any rules set up to drop packets you do not want.

I would not worry about installing a firewall for a linux desktop machine.  Really not.

---

### Post by CapnCook on 2005-10-15
Go to grc.com and click on the shields up link. You can do a port scan there. I have no firewall installed and I my system is completly stealthed. Breezy is GREAT!

---

### Post by ToastedToad on 2005-10-17
[QUOTE=azz]Right, but that does not mean that there are any rules set up to drop packets you do not want.

[/QUOTE]


Thanks for the clarification.

---

### Post by trigg on 2005-10-17
[QUOTE=waldorf]Do people think its necessary to install firestarter or some other kind of firewall?[/QUOTE]

Check to see what services you have running.  I think Ubuntu is default configured to be pretty secure, but that doesn't mean there aren't any vulnerabilities . . . if you are running anything that can act as a server - mysql, postgresql,  apache (webmin, usermin), CUPS (printing), etc . . . it isn't a bad idea to have one installed.  It could at least keep some curious folks from using your system as a playground (especially if you have an "always-on" connection)  Firestarter is pretty easy to configure (gui), so is Shorewall, if you don't mind the command-line - or at least a lack of a gui.
 What is that old adage? "An ounce of prevention . . ."

---

### Post by david_finlayson on 2005-10-17
Assuming you haven't installed a web server or sshd, or opened your machine to remote logins (VLC, FreeNX, etc), you probably don't need a firewall. If you have done one of these things, then you should have a firewall configured to limit access to trusted persons/computers only.

I use Firestarter. It's easy to configure and allows me to open a few ports to my machine so that I can log in from other places on the internet, without leaving the door open for intruders. If you need to get fancy, then other options might be needed (but then you wouldn't be posting this question would you?)

David

---

