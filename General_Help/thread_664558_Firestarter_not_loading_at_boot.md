---
title: "Firestarter not loading at boot"
date: 2008-01-11
forum: General Help
---

### Post by GumbyX on 2008-01-11
I am having a problem with Firestarter not booting on my system. During the boot process, when its lists what is being loaded, I get a FAILED flag for Firestarter. I know its just a front end for the built in firewall, but does this just mean the GUI is not being loaded automatically, or is the firewall failing to load at all?

I can run the GUI once booted into GNOME, so I am pretty sure it (the firewall) is working. Just wanted to check in due to my paranoia that I am leaving myself unprotected.

---

### Post by Vixis on 2008-01-11
Maybe Firestarter tries to execute before GUI are loaded or before your login?

---

### Post by ajgreeny on 2008-01-11
You really don't need firestarter running unless you want to change something in the iptables set-up.  In all honesty you don't really need firestarter at all.  In my paranoia, which came from windows XP,  I used to install firestarter as soon as I had ubuntu up and running, along with clamav for virus scans, but with more knowledge of how linux and ubuntu work, and how safe they are from hackers getting into the box, I don't bother any more.

Don't worry, all will be OK.  By the way, the reason firestarter won't start at boot time is that it will only run as root, if I remember rightly, so it needs your password to start it.

---

### Post by mcduck on 2008-01-11
> **ajgreeny said:**
> You really don't need firestarter running unless you want to change something in the iptables set-up.  In all honesty you don't really need firestarter at all.  In my paranoia, which came from windows XP,  I used to install firestarter as soon as I had ubuntu up and running, along with clamav for virus scans, but with more knowledge of how linux and ubuntu work, and how safe they are from hackers getting into the box, I don't bother any more.

Don't worry, all will be OK.  By the way, the reason firestarter won't start at boot time is that it will only run as root, if I remember rightly, so it needs your password to start it.

No, this is wrong. People often seem to confuse Firestarter and the Firestarter configuration tool..

Firestarter includes two things, the Firestarter script that uses iptables to create a firewall, and the Firestarter GUI that is the configuration tool you'll find from the menu.

All iptables rules are lost at reboot, so you either need to create rules for the firewall at every boot, or have a script that creates the rules for you. So the firestarter script must be run at boot to activate the iptables firewall.

However you don't need to run the GUI configuration tool, all it does is that it configures the firestarter script.

Anyway, in this case the problem could be that GumbyX is using Network Manager to configure the network connection. This means that the network isn't configured until he logs to desktop, and because of this,a t boot time,Firestarter doesn't find any configured network interface and doesn't start.

Here's a HowTo that describes how the Firestarter script can be modified to make the firewall start even when there is no network connection around. This will make the firewall work even when using the Network Manager: [http://ubuntuforums.org/showthread.php?t=542756&highlight=firestarter]("http://ubuntuforums.org/showthread.php?t=542756&highlight=firestarter")

---

### Post by GumbyX on 2008-01-11
> **mcduck said:**
> No, this is wrong. People often seem to confuse Firestarter and the Firestarter configuration tool..

Firestarter includes two things, the Firestarter script that uses iptables to create a firewall, and the Firestarter GUI that is the configuration tool you'll find from the menu.

All iptables rules are lost at reboot, so you either need to create rules for the firewall at every boot, or have a script that creates the rules for you. So the firestarter script must be run at boot to activate the iptables firewall.

However you don't need to run the GUI configuration tool, all it does is that it configures the firestarter script.

Anyway, in this case the problem could be that GumbyX is using Network Manager to configure the network connection. This means that the connection isn't opened until he logs to desktop, and because of this,a t boot time, there is no network connection available and firestarter doesn't start.

Here's a HowTo that describes how the Firestarter script can be modified to make the firewall start even when there is no network connection around. This will make the firewall work even when using the Network Manager: [http://ubuntuforums.org/showthread.php?t=542756&highlight=firestarter]("http://ubuntuforums.org/showthread.php?t=542756&highlight=firestarter")

Right on the nail mcduck. I will have to try that tonight. I know its not a big deal, but I hate having to launch firestarter each time I boot up. Will repost my results.

---

### Post by ajgreeny on 2008-01-11
HELP!!  I was always of the opinion that firestarter was just the gui for iptables and iptables was running in a default install of ubuntu.
Surely for most users who run a normal desktop there is absolutely no need to run firestarter at boot and iptables will be running the default.  There are numerous posts suggesting that firestarter is not needed on a normal setup.

Who is right?

---

### Post by mcduck on 2008-01-11
> **ajgreeny said:**
> HELP!!  I was always of the opinion that firestarter was just the gui for iptables and iptables was running in a default install of ubuntu.
Surely for most users who run a normal desktop there is absolutely no need to run firestarter at boot and iptables will be running the default.  There are numerous posts suggesting that firestarter is not needed on a normal setup.

Who is right?
On normal setup you don't need a firewall. It's ok to have all ports open as there is no programs running that would respond to incoming connections.

Iptables is not running by default, it does absolutely nothing unless you give it some rules to work with, and this is what all Linux firewalls do. They are scripts that define the rules for iptables, and in case of more advanced firewalls, also change these rules on-the-fly in some situations.

If you wish to have a firewall, Firestarter is the easiest way to go. And like I said, it has 2 parts, the firewall script (that needs to be running all the time for the firewall to work) and the graphical configuration tool (that you only need for changing firewall settings, so the GUI doesn't need to run all the time).

---

### Post by jis on 2008-01-15
I ran Firestarter from the system menu (in Xubuntu), but I did not run any related script explicitly. I suppose Firestarter starts some firewall, if needed, as it shows some events in Events tab of its GUI. Or does it? Command ```
ps -A | grep ip
``` gave no output, so I suppose I don't have the iptables firewall running.

---

### Post by reler on 2008-01-16
> **mcduck said:**
> 
Anyway, in this case the problem could be that GumbyX is using Network Manager to configure the network connection. This means that the network isn't configured until he logs to desktop, and because of this,a t boot time,Firestarter doesn't find any configured network interface and doesn't start.

Here's a HowTo that describes how the Firestarter script can be modified to make the firewall start even when there is no network connection around. This will make the firewall work even when using the Network Manager: [http://ubuntuforums.org/showthread.php?t=542756&highlight=firestarter]("http://ubuntuforums.org/showthread.php?t=542756&highlight=firestarter")
I found this thread after noticing a similar problem to the one reported whilst one of my disks was being scanned at start up - this enabled me to note the error message, which was:
"Starting the Firestarter firewall ... fail ! run-parts: /etc/network/if-up.d/50firestarter exited with return code 2"

Looking at that, I'd suggest that this tends to corroborate mcduck's ideas about the network, though (being a Linux newb) I have no idea what GumbyX is. but when I get a chance, I will follow the link to the HowTo thread and see how I get on after following that.

BTW, anybody know what the return code 2 is ?

Reler

---

### Post by mcduck on 2008-01-16
> **jis said:**
> I ran Firestarter from the system menu (in Xubuntu), but I did not run any related script explicitly. I suppose Firestarter starts some firewall, if needed, as it shows some events in Events tab of its GUI. Or does it? Command ```
ps -A | grep ip
``` gave no output, so I suppose I don't have the iptables firewall running.

Try "sudo /etc/init.d/firestarter status" to check if Firestarter is running.

The other way would be to check if iptables has any rules restricting the network traffic:
"sudo iptables -nL" should print a fairly long list if you have a working firewall, while without a firewall you'll get only some simple rules that allow all traffic.

---

### Post by dage on 2008-04-25
> **mcduck said:**
> No, this is wrong. People often seem to confuse Firestarter and the Firestarter configuration tool..

Firestarter includes two things, the Firestarter script that uses iptables to create a firewall, and the Firestarter GUI that is the configuration tool you'll find from the menu.

All iptables rules are lost at reboot, so you either need to create rules for the firewall at every boot, or have a script that creates the rules for you. So the firestarter script must be run at boot to activate the iptables firewall.

However you don't need to run the GUI configuration tool, all it does is that it configures the firestarter script.

Anyway, in this case the problem could be that GumbyX is using Network Manager to configure the network connection. This means that the network isn't configured until he logs to desktop, and because of this,a t boot time,Firestarter doesn't find any configured network interface and doesn't start.

Here's a HowTo that describes how the Firestarter script can be modified to make the firewall start even when there is no network connection around. This will make the firewall work even when using the Network Manager: [http://ubuntuforums.org/showthread.php?t=542756&highlight=firestarter]("http://ubuntuforums.org/showthread.php?t=542756&highlight=firestarter")

Your explication is awesome, it opens my mind. Thank u :)

---

