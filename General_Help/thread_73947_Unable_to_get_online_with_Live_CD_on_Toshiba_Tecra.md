---
title: "Unable to get online with Live CD on Toshiba Tecra A3"
date: 2005-10-10
forum: General Help
---

### Post by NeilSch on 2005-10-10
Bootup is OK, but it won't get on the internet. Laptop (notebook) is:

[http://www.toshiba.ca/web/product.grp?lg=en&section=1&group=1&product=4131&category=](http://www.toshiba.ca/web/product.grp?lg=en&section=1&group=1&product=4131&category=)

Connection is to box marked
  Speedstream 5360 CableModem
  Efficient Networks
  Ethernet ADSL modem

In Network settings, I see
  Modem connection is assoc'd with ppp0
  Wireless is assoc'd with eth0

(Is Ubuntu is trying to use the wireless link instead of ethernet?)

Interface properties of eth0:
  wireless: blank
  config: DHCP (so, no IP addr, etc)

From looking at other posts, I tried 
  ifconfig -a
That didn't do it.
ifconfig reports: eth0, lo, sit0

sudo dhclient output (just the jist, not literal):
 - sit0: unknown h/w addr type 776
 - a bunch of Listening, Sending, DHCPDISCOVER messages
 - No working leases in persistent database

I will supply more detail as needed.

Thanks in advance. I'm new to linux, and excited about getting going. I want to get my confidence up before trying a real install (later, I'll send a post about risk of rendering a laptop with XP pro preinstalled unbootable).

Regards,
Neil

---

### Post by Zelut on 2005-10-10
Let me clarify if I'm reading this correctly.  You've got a high-speed connection and you're trying to connect to that via your wireless card?  I know the Live CD generally doesn't do very well with that and installing the drivers you DO need can't be done unless you do a real installation.

If you can tell me the make/model of your wireless card I can probably tell you if its going to work or not.  But, again, you will need to do a real installation for that to happen.  (If you're concerned about losing your current setup you can do a dual-boot installation--windows & Ubuntu).

---

### Post by NeilSch on 2005-10-10
[QUOTE=kuyaedz]Let me clarify if I'm reading this correctly.  You've got a high-speed connection and you're trying to connect to that via your wireless card?[/QUOTE]

Sorry for not making this clear: although the machine has built-in wireless, I'm _not_ trying to use it. I wish to use the built in NIC with a standard ethernet cable to the cable modem (this link is reliable: I'm using it for this post under WinXP Pro).

---

### Post by Zelut on 2005-10-10
Hmm.. mine worked out of the box.  You could try to manually get a connection using these commands at the terminal:

ifdown eth0
ifup eth0

If not, can you post the results of typing 'ifconfig'?

---

### Post by NeilSch on 2005-10-11
Still no luck..

[QUOTE=kuyaedz]mine worked out of the box.[/QUOTE]
Do you mean a Toshiba Tecra A3? If so, then (assuming boot from ubuntu 5.04 live cd):
 - are you also using ethernet to cable modem?
 - does the (normal) button (not tiny emergency release) to open the cd drive operate for you (under ubuntu live cd)?
 - can you power down without needing to hold down the power button
(note: all is normal under win xp) 

Gory details..

I learned I couldn't run ifdown(up) unless I launch 'Root Terminal' (with 'Terminal', there was some kind of fsys privilege violation). Output:
  ifdown: unknown h/w address 776
  ifup: output similar to that of 'sudo dhclient' (original post)
(eth0 uses a zero, right?)

As before, I tried using the NetwConn dlg to chg from lo to eth0, which takes me to the NetwSettgs dlg, from which I set the wless/eth0 for dhcp, and activate (and use the name eth0 as default gateway device).

ifconfig reports (I'm taking notes by hand, so forgive the abbrev'g and snipping):

   eth0: Link encap:Ethernet HWadd:<all 0's>
           inet6 addr: fe80:200:ff:fe00:0/64 Scope:Link
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
           Rx (Tx) packets, etc ==> all 0's
           colli:0  txql:1000
           rx & tx by ==> 0
           Interr: 22 Base addr 0x2000  Mem:b8006000 - b8006fff

  lo: (I'm guessing this isn't too interesting)

Also, I looked at the (a?) syslog (using the cmd 
  sudo gedit /var/log/syslog
I found on another post). At what seems like a point that's pretty early during boot, these kernel msgs show up:
  IPv6 over IPv4 tunneling driver
  eth0: no IPv6 routers present

I hope this info gives you experienced folks something to chew on.

---

### Post by NeilSch on 2005-10-12
Does the info in my prior post not suggest anything else to try?

Is it an accepted fact that on certain machines, Live CD ubuntu won't get on-line?

---

### Post by NeilSch on 2005-10-24
Does info in earlier posts suggest anything else to try?

Is it an accepted fact that on certain machines, Live CD ubuntu won't get on-line?

---

