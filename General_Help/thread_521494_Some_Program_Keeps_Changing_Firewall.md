---
title: "Some Program Keeps Changing Firewall"
date: 2007-08-09
forum: General Help
---

### Post by Glake on 2007-08-09
I have everything set up on my computer for Stealth and True Stealth. Several days ago I tried tor and privox. I noticed a problem after that, which I am not really sure if it is related. My ports would show closed now when I ran a test but not stealth or true stealth. I thought this had to do with Tor, etc, so I un-installed it. But I just checked and the same things is happening.

So I want to figure out why this is doing that. I want to keep everything True Stealth, etc. 

How can I trouble shoot this to find out what the problem is?
Or
Was there something Tor, or another program for that matter, has changed that is still active even though Tor and privoxy are not installed anymore.

Thanks in advance

---

### Post by ruibernardo on 2007-08-09
> **Glake said:**
> I have everything set up on my computer for Stealth and True Stealth. Several days ago I tried tor and privox. I noticed a problem after that, which I am not really sure if it is related. My ports would show closed now when I ran a test but not stealth or true stealth. I thought this had to do with Tor, etc, so I un-installed it. But I just checked and the same things is happening.

So I want to figure out why this is doing that. I want to keep everything True Stealth, etc. 

How can I trouble shoot this to find out what the problem is?
Or
Was there something Tor, or another program for that matter, has changed that is still active even though Tor and privoxy are not installed anymore.

Thanks in advance

Hi Glake.

to check if there is any firewall (iptables definitions/rules) on your computer, run "sudo iptables-save" or "sudo iptables -L" and check if it is what you have set it for. I guess that, if you did have "set up on my computer for Stealth and True Stealth" and it shows as closed, it isn't running right.

An easy way to set a firewall is to install firestarter, an iptables frontend, and to run its "Wizard" to start it.

Cheers.

---

### Post by Glake on 2007-08-10
Sorry, I should have added that. I do have Firestarter installed. I have to open it each time I boot or reboot my computer.

I go to Shields up and scan the ports after boot/reboot. They show as closed and only a few are stealth. Nothing is true stealth. So I start the Firestarter GUI and unclick the icmp in the prefences. I click accept. Then I check it again, accept and go to shields up. All ports are then stealthed and everything is true stealth.  Something on my computer is resetting it every time I boot/reboot. I am not sure where to look or where to even start.

---

### Post by ruibernardo on 2007-08-10
I think you have to run the Firestarter Wizard (on the "Firewall" menu), and set the interfaces and in the end click "Save".

Until you do that, it isn't really setup. If you already did, maybe those settings were lost, try it again.

---

### Post by Glake on 2007-08-10
I ran the wizard after I made sure the preferences where set the way I wanted. I rebooted then checked shields up. IT works fine now. There was no setting in Firestarter the changed anything like ICMP, etc. So I guess just running it after it was all set was enough. I hope it stays this way, lol.


Thanks for the help.

---

### Post by ruibernardo on 2007-08-10
No problem. Glad it worked.

---

### Post by Glake on 2007-08-11
I don't reboot my computer much. Maybe every day or two. So I didn't notice this right away.

But it is still doing it.

I have to open Firestarter and un-check the ICMP filtering in preferences, accept, then check it and accept. Then it works fine.

Something is changing the setting most of the times it reboots, but not all the time (strange huh.)

I uninstalled Apache, Mysql, webmin, phpmyadmin, etc. Still the same thing. 

I have no idea what is going on or why.


.

---

### Post by ruibernardo on 2007-08-11
What kind of connection you have? Is the network interface up when you start the computer? Do you need to start it?

---

### Post by Glake on 2007-08-11
I have one computer connected to a cable modem. Everything starts fine at boot. Firestarter is on the boot manager and checked (Only the GUI doesn't start unless I click on it.) I don't have to do anything special or extra to connect to the internet.

---

### Post by ruibernardo on 2007-08-11
When you ran the Firestarter Wizard, did you click "Save" at the end? (there is another option like "End" or something like that, I'm in Portuguese language here)

Also check your log files for any Firestarter and/or iptables and/or network issue when Ubuntu starts.

---

### Post by Glake on 2007-08-11
> **epimeteo said:**
> When you ran the Firestarter Wizard, did you click "Save" at the end? (there is another option like "End" or something like that, I'm in Portuguese language here)

Also check your log files for any Firestarter and/or iptables and/or network issue when Ubuntu starts.

Yes. I did click save.

I have to head out for a few. When I get back I will start searching through log files and see if I can find anything. 

Thanks, hopefully I will find something.

---

