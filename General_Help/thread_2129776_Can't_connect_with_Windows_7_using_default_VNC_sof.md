---
title: "Can't connect with Windows 7 using default VNC software?"
date: 2013-03-27
forum: General Help
---

### Post by uzumakifahim on 2013-03-27
Hi,
I'm facing problem with accessing Windows 7 from Ubuntu 12.04 using Remmina and Vino. I can connect Ubuntu to Ubuntu, Windows 7 to Ubuntu (using RealVNC), but when I'm trying to connect Windows 7 from Ubuntu 12.04. It's saying connection failed.

I can't understand what's happening. Experts please help.

Thanks in advance.

---

### Post by btindie on 2013-03-27
First thing to do is check to see that you can establish a TCP connection from your Linux box to Windows on port 3389 (RDP).

You'll need the telnet command to test the connection, this isn't always installed by default as it's obsolete but it's handy for testing TCP sockets.

Type 
```
which telnet
```
if it returns a path then you've already got it. If not you can install it with ```
sudo apt-get install telnet
```

Next to try the connection, type ```
telnet <windows_ip> 3389
``` If it comes back with output similar to the below then the connection is fine.
> Trying 192.168.1.76...
Connected to 192.168.1.76.Escape character is '^]'.

Then type "Ctrl+] quit" to close the connection.
If on the other hand you're unable to get a connection then the next place to look would be your windows 'firewall'. You'd need to tell it to allow RDP connections from the local subnet.

The other problem may be that you don't have the RDP plugin installed for Remmina, you can see if it's installed with
```
dpkg -l remmina-plugin-rdp
```
if it doesn't begin with 'ii' by the name like below then you'll need to install it
> Desired=Unknown/Install/Remove/Purge/Hold| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                        Version                     Description
+++-===========================-===========================-======================================================================
ii  remmina-plugin-rdp          1.0.0-1ubuntu6.1            RDP plugin for remmina remote desktop client
Install it with
```
sudo apt-get install remmina-plugin-rdp
```


Another client you may want to try is vinagre, install with ```
sudo apt-get install vinagre
```

---

### Post by uzumakifahim on 2013-03-27
> **btindie said:**
> First thing to do is check to see that you can establish a TCP connection from your Linux box to Windows on port 3389 (RDP).

You'll need the telnet command to test the connection, this isn't always installed by default as it's obsolete but it's handy for testing TCP sockets.

Type 
```
which telnet
```
if it returns a path then you've already got it. If not you can install it with ```
sudo apt-get install telnet
```

Next to try the connection, type ```
telnet <windows_ip> 3389
``` If it comes back with output similar to the below then the connection is fine.
Then type "Ctrl+] quit" to close the connection.
If on the other hand you're unable to get a connection then the next place to look would be your windows 'firewall'. You'd need to tell it to allow RDP connections from the local subnet.

The other problem may be that you don't have the RDP plugin installed for Remmina, you can see if it's installed with
```
dpkg -l remmina-plugin-rdp
```
if it doesn't begin with 'ii' by the name like below then you'll need to install it

Install it with
```
sudo apt-get install remmina-plugin-rdp
```


Another client you may want to try is vinagre, install with ```
sudo apt-get install vinagre
```

Thanks for your reply. As per your suggestion I've tested telnet and RDP pluging status of my system, good news is both of them are installed. I'll post any new update here ASAP.

---

### Post by uzumakifahim on 2013-03-28
@[**[COLOR=#000000]btindie[/COLOR]**]("http://ubuntuforums.org/member.php?u=876590"), the output of 

```
telnet <windows_ip> 3389
```

is 

```
telnet 192.168.0.1 3389
Trying 192.168.0.1...
telnet: Unable to connect to remote host: Connection timed out

```

Hope this will help you point out the main problem.

---

