---
title: "connecting and disconnecting from my internet connection"
date: 2007-05-18
forum: General Help
---

### Post by rickycodie on 2007-05-18
so that's the problem i have a intel dv945pvs motherboard with a built in ethernet card and about every 15-30 min it disconnects and then reconnects. not a huge problem but annoying especally when trying to move large folders over my network. there is no error that i have found it just does it . any help?

---

### Post by n8bounds on 2007-05-18
anything weird in /var/log/messages or /var/log/syslog ?

are u using network-manager (nm-applet)?

---

### Post by rickycodie on 2007-05-18
no and no

---

### Post by rickycodie on 2007-05-19
wait how do i get to /var/log/messages and the other?

---

### Post by n8bounds on 2007-05-19
open gedit and the click file > open and browse to the root of your file system the double click on the var directory and then on the log directory, and the open the messages file, for instance

if you like the terminal, you can say:

less /var/log/messages

---

### Post by rickycodie on 2007-05-19
here's what it said
May 19 16:29:51 ricky-desktop kernel: [23331.893568]   next_to_watch        <ca>
May 19 16:29:51 ricky-desktop kernel: [23331.893569]   jiffies              <57e
459>
May 19 16:29:51 ricky-desktop kernel: [23331.893570]   next_to_watch.status <0>
May 19 16:29:52 ricky-desktop kernel: [23332.866925] NETDEV WATCHDOG: eth0: tran
smit timed out
May 19 16:29:53 ricky-desktop kernel: [23334.604628] e1000: eth0: e1000_watchdog
: NIC Link is Up 100 Mbps Full Duplex
May 19 16:29:53 ricky-desktop kernel: [23334.604634] e1000: eth0: e1000_watchdog
: 10/100 speed: disabling TSO
May 19 16:29:53 ricky-desktop kernel: [23334.606188] ADDRCONF(NETDEV_CHANGE): et
h0: link becomes ready
May 19 16:30:04 ricky-desktop dhcdbd: message_handler: message handler not found
 under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
May 19 16:30:04 ricky-desktop dhcdbd: message_handler: message handler not found
 under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
May 19 16:30:04 ricky-desktop dhcdbd: message_handler: message handler not found
 under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
(END) 

and that's for the hour or so that i've been on

---

### Post by n8bounds on 2007-05-22
do this:

sudo gedit /etc/rc.local

put this line in there before the line "exit 0" on its own line

/sbin/mii-tool -F 100baseTx-FD

save, close, reboot, watch for same old problem (look to the log file again)

if that doesn't work, re-edit that file and exchange 100baseTx-FD with one of its alternates

The possible arguments are: 100baseT4, 100baseTx-FD, 100baseTx-HD, 10baseT-FD, 10baseT-HD

One of those should work

---

### Post by rickycodie on 2007-05-24
hey thanks it's all fixed!

---

### Post by n8bounds on 2007-05-24
Awesome, good work!

---

