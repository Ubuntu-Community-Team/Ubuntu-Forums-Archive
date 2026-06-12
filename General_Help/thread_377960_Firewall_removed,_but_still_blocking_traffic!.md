---
title: "Firewall removed, but still blocking traffic!"
date: 2007-03-06
forum: General Help
---

### Post by Sjoram on 2007-03-06
Hi,

I've been trying out various firewalls to see which works best for me.  I was having problems getting guarddog correctly configured, and since I didn't have the time, I removed it.  However, it still seems to be blocking ports, so I'm wondering if some configs/settings are still lurking causing me problems.

Any ideas??? :( :( :(

---

### Post by fragos on 2007-03-06
Guardog and Firestarter amongst others aren't firewalls.  They provide a GUI interface to setting iptables which is the firewall.  When you used Guardog, iptables rules were created but they remained after you removed Guardog.

---

### Post by Sjoram on 2007-03-06
Right, I thought this may be the case, but wasn't sure! (New to Linux!) So how do I modify the iptables?

---

### Post by yabbadabbadont on 2007-03-06
Reboot and the default settings should be restored.

---

### Post by Sjoram on 2007-03-06
I have rebooted twice since the iptables were changed, it is still blocking :(

---

### Post by yabbadabbadont on 2007-03-06
If you didn't include the "--purge" option when you removed the firewalls, there probably are still config files being read at startup that are causing the trouble.  Even though you have removed them, try running "sudo apt-get --purge remove guarddog" or firestarter or whatever package name you had installed.  I think that will delete any left over config files.

---

### Post by Sjoram on 2007-03-07
suoramstua@PCWIZADMIN01:~$ sudo apt-get -purge remove guarddog
Password:
E: Command line option &#8216;p&#8217; [from -purge] is not known.

---

### Post by Sjoram on 2007-03-07
I added back the guarddog package and tried to select to "Disable Firewall"

This is the output in Terminal from my guarddog session. It seems to still be blocking traffic.

oramstua@PCWIZADMIN01:~$ sudo guarddog
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Link points to "/tmp/ksocket-root"
Link points to "/tmp/kde-root"
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kbuildsycoca running...
Reusing existing ksycoca
kio (KService*): WARNING: The desktop entry file /usr/share/applications/DefaultPlugins.desktop has Type=Link instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/DefaultPlugins.desktop
kio (KSycoca): ERROR: No database available!
ICE default IO error handler doing an exit(), pid = 24844, errno = 0
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
Launched ok, pid = 24914
PATH=/bin:/sbin:/usr/bin:/usr/sbin:/usr/local/sbin
FILTERSYS=0
if [ -e /sbin/ipchains ]; then
FILTERSYS=1
fi;
if [ -e /usr/sbin/ipchains ]; then
FILTERSYS=1
fi;
if [ -e /usr/local/sbin/ipchains ]; then
FILTERSYS=1
fi;
# Check for iptables support.
if [ -e /proc/sys/kernel/osrelease ]; then
  KERNEL_VERSION=`sed "s/^\([0-9][0-9]*\.[0-9][0-9]*\).*\$/\1/" < /proc/sys/kernel/osrelease`
  if [ $KERNEL_VERSION == "2.6" ]; then
    KERNEL_VERSION="2.4"
  fi;
  if [ $KERNEL_VERSION == "2.5" ]; then
    KERNEL_VERSION="2.4"
  fi;
  if [ $KERNEL_VERSION == "2.4" ]; then
    if [ -e /sbin/iptables ]; then
      FILTERSYS=2
    fi;
    if [ -e /usr/sbin/iptables ]; then
      FILTERSYS=2
    fi;
    if [ -e /usr/local/sbin/iptables ]; then
      FILTERSYS=2
    fi;
  fi;
fi;
if [ $FILTERSYS -eq 0 ]; then
  echo "ERROR Can't determine the firewall command! (Is ipchains or iptables installed?)"
fi;
if [ $FILTERSYS -eq 1 ]; then
echo "Using ipchains."
echo "Resetting firewall rules."
ipchains -P output ACCEPT
ipchains -P input ACCEPT
ipchains -P forward ACCEPT
ipchains -F forward
ipchains -F input
ipchains -F output
fi
if [ $FILTERSYS -eq 2 ]; then
echo "Using iptables."
echo "Resetting firewall rules."
iptables -P OUTPUT ACCEPT
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -F FORWARD
iptables -F INPUT
iptables -F OUTPUT
fi;
echo "Finished."
oramstua@PCWIZADMIN01:~$ ICE default IO error handler doing an exit(), pid = 24910, errno = 0

---

### Post by moore.bryan on 2007-03-07
[I]how about:
```
sudo aptitiude remove --purge guarddog firestarter && sudo reboot
```
[/I]

---

### Post by k1n6 on 2007-03-07
iptables -F 

will completely flush your ip tables, but may not prevent any thing from resetting them next time you boot.

---

### Post by frodon on 2007-03-07
Instant fix :

Paste in a terminal these commands, it just delete all iptables rules so after this you will be ok. I know it's a bit long but i don't know what rules you have so it's better to just erase all ipatbles rules :
```
sudo iptables -P INPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -t nat -P PREROUTING ACCEPT
sudo iptables -t nat -P POSTROUTING ACCEPT
sudo iptables -t nat -P OUTPUT ACCEPT
sudo iptables -F
sudo iptables -t nat -F
sudo iptables -X
sudo iptables -t nat -X
```

Now that you're bmck to normal i hope you don't have a remaining rc script which set the firewall each time on boot, so reboot and see ;)

---

### Post by yabbadabbadont on 2007-03-07
> **Sjoram said:**
> suoramstua@PCWIZADMIN01:~$ sudo apt-get -purge remove guarddog
Password:
E: Command line option ‘p’ [from -purge] is not known.

You should have cut and pasted the command.  As was pointed out above, there are two dashes before the word purge in that command.  :)

---

### Post by Sjoram on 2007-03-08
> **frodon said:**
> Instant fix :

Paste in a terminal these commands, it just delete all iptables rules so after this you will be ok. I know it's a bit long but i don't know what rules you have so it's better to just erase all ipatbles rules :
```
sudo iptables -P INPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -t nat -P PREROUTING ACCEPT
sudo iptables -t nat -P POSTROUTING ACCEPT
sudo iptables -t nat -P OUTPUT ACCEPT
sudo iptables -F
sudo iptables -t nat -F
sudo iptables -X
sudo iptables -t nat -X
```

Now that you're bmck to normal i hope you don't have a remaining rc script which set the firewall each time on boot, so reboot and see ;)

After following this, as well as correctly removing and purging guarddog, I still cannot connect to port 80  or VNC from a remote machine to this one.

---

### Post by frodon on 2007-03-08
Then it's not related to the ubuntu firewall, check the rules you have with "sudo iptables -L" and you should this that the INPUT, OUTPUT and FORWARD chain are in the ACCEPT state.

---

### Post by fragos on 2007-03-08
To connect to your box from another you must be running apache web server.  As to VNC, do System-> Preferences-> Remote Desktop and make sure the Sharing box is checked.  Have to set a unique hostname?  My hostname is "Geo" and to VNC from another box on my LAN I use "vncviewer Geo:0".

---

### Post by Sjoram on 2007-03-08
Both Apache and VNC have been working fine, until I installed firewall. I installed one, had problems, removed it, was able to access fine, its only guarddog I've had trouble with. I'll check the iptables and post the result.

---

### Post by Sjoram on 2007-03-09
Here's the contents of my iptables:
(How do I modify these to whatever the 'default' is?)

oramstua@PCWIZADMIN01:~$ sudo iptables -L
Password:
Chain INPUT (policy DROP)
target     prot opt source               destination         
DROP       all  --  127.0.0.0/8          anywhere            
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP      !udp  --  anywhere             BASE-ADDRESS.MCAST.NET/4 
DROP       icmp -f  anywhere             192.168.1.2         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             192.168.1.255       
ACCEPT     all  --  anywhere             255.255.255.255     
ACCEPT     all  --  anywhere             192.168.1.2         state RELATED,ESTABLISHED 
ACCEPT     icmp --  anywhere             192.168.1.2         icmp echo-request limit: avg 1/sec burst 3 
ACCEPT     tcp  --  anywhere             192.168.1.2         tcp dpt:ftp flags:FIN,SYN,RST,ACK/SYN state NEW 
ACCEPT     tcp  --  anywhere             192.168.1.2         tcp dpt:ftp-data flags:!FIN,SYN,RST,ACK/SYN state NEW 
REJECT     tcp  --  anywhere             192.168.1.2         tcp dpt:auth reject-with tcp-reset 
LOG        all  --  anywhere             anywhere            LOG level warning prefix `Fell off input chain: ' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  192.168.1.2          anywhere            state NEW,RELATED,ESTABLISHED 
LOG        all  --  anywhere             anywhere            LOG level warning prefix `Fell off output chain: ' 
oramstua@PCWIZADMIN01:~$

---

### Post by Sjoram on 2007-03-09
I managed to clear my iptables, but I still could not get inbound traffic to Apache or VNC, and after a reboot, they reset themselves to the above.

---

### Post by jms830 on 2007-05-01
there is a button in guarddog on the advanced tab called "restore to factory defaults". maybe that will work

---

