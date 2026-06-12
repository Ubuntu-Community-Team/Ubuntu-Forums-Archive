---
title: "Remote (ssh) shutdown fails"
date: 2006-10-23
forum: General Help
---

### Post by delphinen on 2006-10-23
I have been using Ubuntu Dapper flight half a year, and im impressed with the stability and usability.

So far I have been able to do everything I want with my computer, except 
one thing: shutdown it remotely, through ssh.

When I log in to my computer and use "shutdown now" in shell, it says "the system is going down NOW", it halts some things, but no real shutdown.
If I do "shutdown now" in front of my computer, it works ok. 
Is there something I could do to solve this?

also, totally offtopic, is there ANY chance I could "wake up" my computer with an ADSL connection?

---

### Post by dbott67 on 2006-10-23
What about trying [B]sudo shutdown -h now
[/B]
> **delphinen said:**
> also, totally offtopic, is there ANY chance I could "wake up" my computer with an ADSL connection?

Depends if your motherboard/NIC supports '[Wake-on-LAN]("http://www.ezlan.net/WOL.html")'.  If it does, you'll need to do the following:

1. Static IP or Dynamic DNS for your external internet IP address.
2. Port-forward port # to internal IP of PC you want to wake on your router/firewall (if applicable).
3. Get MAC address of host machine (use **ifconfig**)
```
dbott@dapper:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr [COLOR="Red"]00:15:C5:0C:AB:07[/COLOR]
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217
```
4. Install a "[Wake-on-LAN]("http://www.ezlan.net/WOL.html")" (Windows) client on remote computer (or **sudo apt-get install wakeonlan** in Ubuntu).
5. Open a terminal and type:
```
wakeonlan -i 123.123.123.123 -p 9 0015C50CAB07
``` where *-i 123.123.123.123* is your public IP address or dynamic DNS hostname; *-p 9* is the port number; and *0015C50CAB07* is the MAC address of the computer to be woken-up.


-Dave

---

### Post by matthewstory on 2006-10-25
out of curiosity . . . will it restart if you issue:

shutdown -r now

I had similar issues with debian sarge, but the shutdown -r now command worked where the shutdown now argument didn't.

---

### Post by stomakmonkee on 2008-04-01
Using shutdown now also requires that you tell the system what to do after it shuts down.  If you want the computer to then turn off, the command would be "sudo shutdown -h -P now".  The "-P" is for powerdown, and the -h (halt) is required for a -P.

---

### Post by IceKold0 on 2008-06-28
Did anyone get any response whether this worked?!

I am using Debian as a DRBL/CloneZila server to multicast an XP image to a rack of laptops through a high-speed NetGear switch.

I can wakeonlan any of my machines (singularly and multiple machines) and the CloneZilla cloning works perfectly. For a first-timer I have surprised myself!

The only thing I can't get to work is a batch remote shutdown.

CloneZilla provides this and I have tried it but the machines don't shut down completely. They reach a full halt and just before the ACPI turns the machine off it stays powered on and just stops - as a result we have to manually power down the laptops by holding the power button... slghtly irritating when I know they all support ACPI poweroff from a software command...

Any ideas?

---

