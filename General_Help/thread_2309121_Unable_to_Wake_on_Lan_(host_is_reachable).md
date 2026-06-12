---
title: "Unable to Wake on Lan (host is reachable)"
date: 2016-01-07
forum: General Help
---

### Post by robo731 on 2016-01-07
I'm trying to set up Wake on Lan for my Dell Inspiron 15r 5521 running Ubuntu Server. I've used ethtool to ensure that the NIC is WOL capable. It returned "g" upon testing. Also, the program on the windows computer I am using shows that the computer I am trying to reach is on when it is indeed on. However, the program cannot successfully turn the computer on when it is off. There is no setting in the BIOS for Wake on Lan, but Dell has assured me that all Inspiron laptops, this one included are WOL capable and that it should work. I tired to use wireshark to check if the laptop was receiving the magic packets, but I am relatively new to Ubuntu and could not get it to work properly. I continually got a "Gtk-WARNING Cannot Open Display" error.

---

### Post by deadflowr on 2016-01-07
Are you certain the MAC address is correct?

---

### Post by robo731 on 2016-01-08
I believe so. I'm using the "hardware address" from ```
ifconfig
``` for the MAC Address.

I followed the steps someone suggested in an old post. I ran: ```
sudo   tcpdump -i eth0 port 9 -vvvv -s0 -n
``` which returned output that   was similar to that of this [post]("http://ubuntuforums.org/showthread.php?t=1807768&p=11064495#post11064495").   According to the person in that thread, this indicates that the   computer is receiving the packets. I'm assuming that person is correct   and that the machine is at least receiving the packets, but I don't know   what I should do now.

[COLOR=#0000ff]Edit: I am  able to wake the machine when it is in sleep (suspend) mode. I still  cannot wake it after putting it in hibernate mode or shutting down with  the command: ```
sudo shutdown -h now
``` The device is labeled as  "p2p1" in ifconfig, suggesting that it is a PCI device. Maybe it is not  maintaining power after the system shuts down. Also, in windows there  are a lot of options such as "shutdown wakeup" and "Allow the computer  to turn off this device to save power." Are there options like these in  ubuntu?[/COLOR]

I called Dell to find out if this was possible. It seems there's no way  to set the laptop to keep power to the network card after an S5  shutdown. Such functionality is only available in their enterprise  systems. The fact that you can wake from sleep mode is the best work  around I can find.

---

