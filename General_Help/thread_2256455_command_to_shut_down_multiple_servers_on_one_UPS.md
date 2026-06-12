---
title: "command to shut down multiple servers on one UPS"
date: 2014-12-12
forum: General Help
---

### Post by bphillips2 on 2014-12-12
I have one UPS powering two Ubuntu servers. The UPS has a USB connection to one server but does not have a second USB connection and no network connection.  Is there someway for me to have the server connected to the UPS send a shutdown command to the other server when it receives a shutdown command from the UPS?

I'm using a Cyber Power 1500AVR UPS and their Power Panel software

---

### Post by tgalati4 on 2014-12-12
*apcupsd* has a Master-Slave setup.  Set the server with the USB connection as Master.  When it is instructed to go down, it will send out a network broadcast and any server designated as Slave will shutdown.  This is convenient as you can have one smart UPS and a bunch of dumb UPS's and use the smart UPS to signal the master and the rest of the servers will shut down after a configured time period (typically 2 minutes).

An alternative is to write script to shut the second server down and call that script whenever the UPS is tripped.  That detection could be handled through a dbus query, or though some notification facility in the Power Panel software.

---

### Post by bphillips2 on 2014-12-12
I assume that apcupsd program will not work with my CyberPower UPS, correct?

---

### Post by tgalati4 on 2014-12-12
It depends.  Try installing and configuring it.  If the CyberPower uses a small subset of APC commands via USB then it should work.

---

### Post by HermanAB on 2014-12-13
There are umpteen different ways to do this.  You could Tee the UPS port and send the data to both.  You could set up SSH and execute a remote command when needed. If your LAN is secure then you could do the same with FTP or Telnet.  You could send a command over Netcat or do port knocking...

---

### Post by markosjal on 2014-12-13
You can also use NUT. I have one UPS with a UPS port that connects to an Apple TV (via USB) running ubuntu (variant) . That apple TV is a NUT server. When the UPS is on battery the UPS Sends appropriate messages to the Apple TV, which in turn sends shutdown messages to all systems on "dumb" UPSs to shutdown.

---

