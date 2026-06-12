---
title: "Samba Shares Across Subnets"
date: 2015-05-07
forum: General Help
---

### Post by aaron91 on 2015-05-07
Hello,

I have a Ubuntu Server 14.04 set up in a small office environment, I am trying to use Samba 4.1.6 to share a network drive to the whole office across 2 different subnets. The Ubuntu Server is setup on a 10.58.150.XX subnet, while I need to access it from that network as well as a 10.58.130.XX subnet. The 10.58.130 subnet will not even see the shared drive, while the 10.58.150 see the drive but says that I don't have permissions to access it. I have tried many different variations of "interfaces", "hosts allow", and "WINS Server" in my smb.conf file but I have had no luck. It seems that when I make any of these changes nothing really happens as far as recognizing the specified subnet zones.  I will post a dump of testparm of my "smb.conf" file. Any help or general pushes in the right direction would be greatly appreciated. 

```
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[storage]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions


[global]
    server string = %h server (Samba, Ubuntu)
    interfaces = 10.58.150.34/255.255.255.0
    bind interfaces only = Yes
    server role = standalone server
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    name resolve order = bcast, host, lmhosts, wins
    preferred master = Yes
    domain master = Yes
    dns proxy = No
    wins support = Yes
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb
    read only = No
    hosts allow = 10.58.130, 10.58.150


[printers]
    comment = All Printers
    path = /var/spool/samba
    read only = Yes
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No


[storage]
    comment = NCCORP STORAGE
    path = /media/nccorp/396016c1-ed13-48a2-ab58-941c4ef7edd3
    guest ok = Yes


[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
    read only = Yes 
```

---

### Post by TheFu on 2015-05-07
I don't think "browsing" works across subnets. However, if you can "ping" the samba server from the clients, then accessing it by DNS/IP should work.  If every client can ping by ip - then just use the IP address for now, until the name resolution (DNS) is fixed.

I didn't check the "hosts allow" setting in your [global] section. Mine has a network specified and doesn't use commas  - 
127.0.0.1 172.22.22.0/24
Don't know if commas are prohibited or not either. I'd have to rtfm to check.

I think interfaces are to force samba to listen only on specific NICs, should the server have multiple. Empty should listen on all NICs I would think.

Don't know if any of this will help - perhaps not.

---

### Post by SeijiSensei on 2015-05-07
Is there a router that handles the two networks?  Routers for each of the two subnets?  Can we see the results of running "route -n" on the server?  Is there a reason why you aren't using 10.58.0.0/16 for all network specifications?  Some of these symptoms may come from problems with routing rather than Samba.

If you are configuring the interface manually in /etc/network/interfaces, use "netmask 255.255.0.0" instead of "255.255.255.0" if that is what you have.  What netmask does the gateway router use?

If you get the address from DHCP, and DHCP distributes a mask of 255.255.255.0, I'd configure the interface manually and specify the full "class-B" subnet instead.

If none of that works, then the problem may be upstream.  Does each subnet have its own router, or is there one system-wide upstream router that manages all of 10.58?  

Can you access a share from a client on the 10.58.150.0/24 network by entering its UNC name into Windows Explorer?  Try \\servername\storage or \\10.58.150.34\storage.  Are you prompted with a login dialog?  

If you're not able to authenticate, try adding yourself to the Samba password system with the command
```
sudo smbpasswd -a username
```
then connecting to the share.

If you have smbclient installed on the server, what shares do you see running the command "smbclient -L localhost"? Can you connect with "smbclient -U username //localhost/storage"? 

What do you see in /var/log/samba/log.*?  The server's logs are log.smbd and log.nmbd.  There should also be logs with IP addresses or hostnames recording sessions with the clients.

In /etc/samba/smb.conf, it is recommended to use interfaces:
```

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

```
but also allows CIDR network addresses.

---

### Post by aaron91 on 2015-05-08
Thank you both for your responses. I am currently trying all of the suggestions. Just to clarify on a couple of your questions and maybe somethings I left out. The subnets are on VLANS coming from the same router. I can ping the clients and the server both ways. I am using DHCP for my address, I will try changing to static and manually configuring. Whenever I try to connect from outside the xx.xx.150 network whether it be from IP address or server name/user name it says cannot connect.

Route &#8211;n shows:
```
Kernel IP routing table
Destination     Gateway       Genmask      Flags     Metric    Ref    Use    Iface
0.0.0.0       10.58.150.1  0.0.0.0          UG       0           0    0       eth0
10.58.150.0  0.0.0.0       255.255.255.0  U       0           0     0       eth0
169.254.0.0  0.0.0.0       255.255.0.0      U      1           0     0       eth2
```

When I try to access the shared folder from within the xx.xx.150 network I get the message that I do not have permission to access the folder, but it is promising that it does see it. Now I think I just have to configure my accessability with passwords. 

But as far as my smb.conf files, do you guys see anything that stands out that may be hurting or helping specifically? Can I trim it down any to make it more efficient?

---

### Post by SeijiSensei on 2015-05-08
If you have resolved the authentication problem and can connect from 10.150, try putting an Ubuntu box on the 10.130 network with smbclient installed.  Make sure the server's hostname is resolvable via DNS or the client's host file.  Then run "smbclient -L -U username servername".  What happens?

Also try "interfaces = eth0".  Otherwise your configuration file is pretty vanilla.

Also just to be sure, you're not using Active Directory or any other Microsoft service that assumes it will manage all the servers, right?  Your smb.conf makes the Ubuntu box the "domain master".  That won't work correctly if there is another machine on the network handling that responsibility.  If you run authentication through AD, then Samba should be using that for authentication as well.  I don't use MS networking technologies, so I can't help with how to configure things in an AD environment.

---

### Post by TheFu on 2015-05-08
The lack of permissions could be because the samba passwds haven't been initialized.[B]
smbpasswd  username[/B]  Only needed once.

Also - please use "code tags" for cmd output posts. Things line up better that way. "Go Advanced" has a button for it. Would be helpful if you edited the prior posts with code-tags. Thanks.

Can the machines "ping" each other?  No use in trying any other connectivity if ping doesn't work.

---

### Post by aaron91 on 2015-05-08
My apologies on the coding, this is my first post. It should be fixed now. 

The machines can ping across the subnets. I'm still having some issues with the passwords and connectivity on the same subnet as well.  


When I issue the **smbpasswd nccorp **I get this response:

```
root@ubuntu:/home/nccorp# smbpasswd nccorp
New SMB password: test
Retype new SMB password: test
Failed to find entry for user nccorp. 
```

Not sure whats going on there.

We are using active directory as our system is Windows based for the most part. I changed the smb.conf to show "no" on domain master, local master, and preferred master.

---

### Post by TheFu on 2015-05-08
Thanks for the code tags. Much easier to read.

**sudo smbpasswd -a nccorp**

My fault - left off the '-a' - **man smbpasswd** corrected me. manpages are amazing. ;)

---

### Post by aaron91 on 2015-05-08
Yes they are! what do you guys know about the create / directory masks?? Do you believe this may have something to do with the issue?

---

### Post by TheFu on 2015-05-08
> **aaron91 said:**
> Yes they are! what do you guys know about the create / directory masks?? Do you believe this may have something to do with the issue?

Nope. They only specify the permissions on newly created files or directories - not the connections.
Did you fix these lines?
```

  interfaces = 10.58.150.34/255.255.255.0
  hosts allow = 10.58.130, 10.58.150
```
Already?

---

### Post by aaron91 on 2015-05-08
I did fix the lines to look just like what you have there...still no luck, should the hosts allow be put in the global section?

```
interfaces = 10.58.150.34/255.255.255.0
hosts allow = 10.58.130, 10.58.150
```

---

### Post by TheFu on 2015-05-08
I showed what you had - not the corrections.  I think both of those look wrong to me. I could be wrong. Explained the issues above - I believe.
[https://www.samba.org/samba/docs/using_samba/ch06.html](https://www.samba.org/samba/docs/using_samba/ch06.html) - no comma and missing the trailing (dot)

The interface line seem to be ok according to that link - I've just never seen it that way.

---

### Post by aaron91 on 2015-05-11
Ohhh a little confusion on my part. I'll take a look at the article. Sorry about the gap in responses, I was out of town. The article seems like its going to be helpful. I'll post again once I have something else to try. Thank you again for your efforts.

---

### Post by aaron91 on 2015-05-11
So, after messing with these setting over and over, I finally am able to connect to my shared drive. I will post below my testparm results. Thank you guys again for all the help. I'm not entirely sure what the fix was, I'm sure it had something to do the specifics in the smb.conf file, probably poor placement on a comma or space, who knows... 

```
[global]	server string = %h server (Ubuntu)
	interfaces = 10.58.150.34/255.255.255.0
	bind interfaces only = Yes
	server role = standalone server
	map to guest = Bad User
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	wins support = Yes
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	idmap config * : backend = tdb
	hosts allow = 10.58.130., 10.58.150.


[homes]
	read only = No


[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	print ok = Yes
	browseable = No


[storage]
	comment = NCCORP STORAGE
	path = /media/nccorp/396016c1-ed13-48a2-ab58-941c4ef7edd3/Storage
	read only = No


[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers 
```


However, I did change my /etc/network/interfaces file to show my primary interface as dhcp as well. as when I tried to make it static I lost all connectivity. I know this isn't best practice for a server but its a temporary fix. Thank you guys again.

---

### Post by TheFu on 2015-05-11
If was the added trailing periods.

```
hosts allow = 10.58.130., 10.58.150.
```
I'm still surprised the comma is allowed.
Previously you had:

```
hosts allow = 10.58.130, 10.58.150
```
That is COMPLETELY different.

---

### Post by aaron91 on 2015-05-12
I took out the comma in my smb.conf file however it adds it when I do the dump of the file through testparm. It seems like sometimes the changes that I made to the smb.conf file, whether its through "vi" "nano" or "gedit", wouldn't take place everytime and I always submitted the changes when exiting.

---

### Post by Morbius1 on 2015-05-12
> the dump of the file through testparm
Perhaps an interesting side note - perhaps not: testparm ( run by itself without any switches ) doesn't provide a dump of smb.conf or a dump of that file with the comments removed. It's more an interpreter letting you know what affect your smb.conf has on the default settings of samba. So if you were for example add a parameter to the global section that is already in the defaults when you run testparm it wouldn't show up at all because it has no affect.

---

### Post by TheFu on 2015-05-12
> **aaron91 said:**
> I took out the comma in my smb.conf file however it adds it when I do the dump of the file through testparm. It seems like sometimes the changes that I made to the smb.conf file, whether its through "vi" "nano" or "gedit", wouldn't take place everytime and I always submitted the changes when exiting.

Don't use **sudo gedit**. It can cause issues. Use **sudoedit**.
The smb.conf file must be edited with elevated privileges (sudo). That is basic for Unix administration. Attempting to edit it without that will always fail.  File and directory permissions are central to Unix security.

---

### Post by aaron91 on 2015-05-12
Morbius I think you are correct about it having no effect at all. After noticing this, i changed it in the global section instead of the share. and FU like I said, I tried it in several different means. I always use elevated commands as I am the only person who has access to the server.

---

