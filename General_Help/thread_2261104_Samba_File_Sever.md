---
title: "Samba File Sever"
date: 2015-01-16
forum: General Help
---

### Post by Ali_Fairfax on 2015-01-16
[COLOR=#404040][FONT=Gudea]Hi there,[/FONT][/COLOR]
[COLOR=#404040][FONT=Gudea]Could anyone help, I have setup Samba on Ubuntu Sever 14 LTS, I can ping the server.[/FONT][/COLOR]
[COLOR=#404040][FONT=Gudea]The server shows in the network on both a Mac and windows operating system. However as soon as i click onto the server to view the shares it comes up that it was unable to connect.[/FONT][/COLOR]
[COLOR=#404040][FONT=Gudea]I have a feeling this is not to do with the configuration of samba rather something to do with network settings. I have also tried accessing the server by IP address with no success.[/FONT][/COLOR]
[COLOR=#404040][FONT=Gudea]If anyone could help that would be great.[/FONT][/COLOR]

---

### Post by TheFu on 2015-01-16
Welcome to the forums.

Can you please provide the networking setting for all 3 systems? Hard to help without **any** information.
Also, might be worth checking the firewall on Ubuntu - if you've enabled it.  If you haven't, then it isn't running by default.

---

### Post by Ali_Fairfax on 2015-01-16
Hi,

The Machine running ubuntu server is setup as per below
 This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


#iface eth0 inet dhcp
auto eth0
iface eth0 inet static
        address 192.168.0.51
        netmask 255.255.255.0
        gateway 192.168.0.1

Both the windows and mac machine are set to obtain an IP address dynamically.
I have not enabled the firewall within the server.

---

### Post by TheFu on 2015-01-16
What are the network settings for all 3 machines?

---

### Post by Ali_Fairfax on 2015-01-16
sorry could you be more specific on what network settings to provide please? sorry new to this.

---

### Post by TheFu on 2015-01-16
Sorry, didn't want to assume you didn't know these things - after all, most people setup samba using a GUI and it "just works" these days.  [http://www.howtogeek.com/74459/how-to-create-samba-windows-shares-in-linux-the-easy-way/](http://www.howtogeek.com/74459/how-to-create-samba-windows-shares-in-linux-the-easy-way/)

Output from commands that provide:
IP
gateway
netmask
DNS
route
(usually just 2 commands per platform - **ipconfig**/ifconfig and **route** are needed.  As long as I'm asking, please copy/paste the text and use "code tags" so things line up nice in the forums.

I'm also confused when you say IP addresses don't work - makes me think the machines are misconfigured, hence why all the network info is requested.

The output from pings from the clients-to the server would be helpful - by ip, then by name. This shows whether name resolution is working on the LAN or not. By IP should always work, unless the problem is lower level.

Lastly - samba settings would be good too - no comments, just the settings actually being used. Comments often mislead us. Best to never see them when troubleshooting, IMHO. And I find **smbtree** to be very helpful as well. Don't use any userid, unless you connect with one.  Would be nice if run from a Linux system that isn't the server, but still on the same subnet.

In short, we need the info that controls how the machines communicate between each other for CIFS connections - unless you want 1,000 guesses for what might be wrong without any facts to narrow it down. ;)   Facts and data can lead to resolutions.  Anything less leads to guesses - sometimes lucky, but usually not.

---

### Post by Ali_Fairfax on 2015-01-16
Thank you for coming back to me.
I have been a Windows Server Administrator for a couple of years however trying to move over to Linux to expand knowledge and take advantage of what it has to offer.
The network settings of the first machine (Windows)
IP 192.168.0.24
Gateway 192.168.0.1
Netmask 255.255.255.0
DNS 192.168.0.1

The network settings of the first machine (Mac)
IP 192.168.0.13
Gateway 192.168.0.1
Netmask 255.255.255.0
DNS 192.168.0.1

Sorry didn't explain that well, I have tried connecting to the server using the Net Bios name of \\lukedesign-svr1 and also the IP address of the server \\192.168.0.51
The PING from the client to the server is coming back as all packets received.
"[global]	public = yes
	server string = 
	netbios name = lukedesign-svr1
	printcap name = CUPS
	syslog only = yes
	syslog = 1
	socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
	winbind use default domain = yes
	wins support = true
	announce version = 5.0
	username map = /etc/samba/smbusers
	writeable = yes
	os level = 20
	security = user
	null passwords = yes
	encrypt passwords = yes
	winbind trusted domains only = yes
	name resolve order = hosts wins bcast
	workgroup = workgroup
	passdb backend = tdbsam
	printing = CUPS
    ; General server settings
[MyFiles]
    path = /media/samba/
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0755
    directory mask = 0755
  
Let me know if you need more details.
Thank you

---

### Post by TheFu on 2015-01-16
Generally, it is preferred to copy/paste data with the exact command, so we know how you got it. It is common for humans to make mistakes based on belief rather than fact. Does that make sense?

```
$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:23:55:3c:23:37  
          inet addr:172.22.22.13  Bcast:172.22.22.255  Mask:255.255.255.0
          inet6 addr: fe80::223:55ff:fe3c:2337/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4060886 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3225739 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4162768694 (4.1 GB)  TX bytes:2645798910 (2.6 GB)

$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         rt1             0.0.0.0         UG    0      0        0 eth0
172.22.22.0     *               255.255.255.0   U     0      0        0 eth0
192.168.122.0   *               255.255.255.0   U     0      0        0 virbr0

```
See how nice things line up?
The output from **testparms** would be good too.  We don't use "guest" accounts here, but here's a simple setup that works.
```

[global]
   workgroup = workgroup
   security = user
   unix extensions = no
   server string = %h server
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes 
   unix password sync = yes

   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssu
ccessfully* .
   pam password change = yes
   map to guest = bad user
   usershare allow guests = no

[homes]
  comment = Home Directories
  hosts allow = 127.0.0.1 172.22.22.0/24 172.22.22.27
  hosts deny = 0.0.0.0/0
  browseable = yes
  guest ok = no
  writable = yes
  create mask = 0644
  directory mask = 0755
  valid users = %S
  follow symlinks = no
  wide links = no

```
The key is that every userid must have a samba password set manually the first time with the **smbpasswd** tool.

---

### Post by Ali_Fairfax on 2015-01-16
How do I put into these code boxes?

---

### Post by Ali_Fairfax on 2015-01-16
Also I have changed my smb.conf to the above settings, when running smbpasswd I get the following error after typing the password in: -
Unable to connect to SMB server on machine 127.0.0.1. Error was : NT_STATUS_CONNECTION_REFUSED.

---

