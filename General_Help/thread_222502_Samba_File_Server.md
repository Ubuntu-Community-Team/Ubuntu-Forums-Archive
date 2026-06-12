---
title: "Samba File Server"
date: 2006-07-25
forum: General Help
---

### Post by justin2021 on 2006-07-25
I recently received a Dell Dimension 4600C that was supposedly broken. Well after fixing it I have decided that I want to make it a file server. My main plan is to allow friends and family to be able to access their own personal folder in the server, from their Windows computers, and me be able to put things in the folders from my Ubuntu computer. So far I have installed Debian 3.1 onto it and already apt-geted samba. Where do I go from here? :-k

---

### Post by wieman01 on 2006-07-25
Next thing would be to share a folder via Samba (using the graphical file sharing tool in Gnome) under the same workgroup as your Windows clients (important!). I think the graphical tool allows you to do Windows file sharing including the setup of a workgroup.

I am not in front of my own computer right now, so I cannot give you a screenshot. But that's the way to go.

---

### Post by justin2021 on 2006-07-25
Okay, well so far i got to a point where a folder appears on my desktop (ubuntu desktop) saying "justin on debian", but when i click it it gives an error:

Could not open location 'ssh://justin@debian:22/home/justin'

Details: The host "debian" could not be found.

I dont understand because I have both computers plugged up to my router and i am able to secure shell into the server with the command line...

Also, when try to start ssh with /etc/init.d/ssh start on the server, i get this error:

Starting OpenBSD Secure Shell server: sshdCould not load host key: /etc/ssh/ssh_host_rsa_key
Could not load host key: /etc/ssh/ssh_host_dsa_key
Disabling protocol version 2. Could not load host key
sshd: no hostkeys available -- exiting.


[EDIT] problem solved, all i had to do was add the ip and name to  my computer's hosts. now that i can acces the folder saying "justin on debian" i open it and there is nothing in there... do i have to add stuff?

---

### Post by andy_cowman on 2006-07-25
I am not sure if its helpful or not but I found the orginal smb.conf just didnt work for sharing to windows machines. This is the one i put together that lets windows machines access my folders. It might be useful to you even though it may well be a bit simplistic for what you need.

good luck!

[global]
guest ok = yes
security = share
workgroup = MSHOME
smb passwd file = /etc/smbpasswd
#logon script should go in netlogon directory
#below you will find a example of this
server string = Samba Server
load printers = no
printcap name = /etc/printcap

# Un-comment the following to provide a specific roving profile share
# the default is to use the user's home directory
wins support = no
[Photos]
    path = /home/john/
    browseable = yes
    guest ok = yes
# NOTE: If you have a BSD-style print system there is no need to
# specifically define each individual printer
#[printers]
    ;comment = All Printers
    ;path = /var/spool/samba
    ;browseable = yes
# Set public = yes to allow user 'guest account' to print
    guest ok = yes
   writable = yes
   printable = yes

[MyDocuments]
path = /home/john
available = yes
browseable = yes
public = yes
writable = yes
guest ok = yes

---

### Post by justin2021 on 2006-07-25
thx for that. now my only problem is that me, as the admin of this file server, needs to be able to access all users folder that i add to this server. i also need all the folders to only be able to get stuff off of, and not be able to put things in them from the users. i should be the only one who is able to put things in them, but i want to make one folder that can be accessed by all users, and they are able to put stuff in it... make any sense? :)

---

### Post by wwitthoff1 on 2006-09-19
> **justin2021 said:**
> thx for that. now my only problem is that me, as the admin of this file server, needs to be able to access all users folder that i add to this server. i also need all the folders to only be able to get stuff off of, and not be able to put things in them from the users. i should be the only one who is able to put things in them, but i want to make one folder that can be accessed by all users, and they are able to put stuff in it... make any sense? :)


The server guide section on samba helped me figure it out.

---

### Post by dgray_from_dc on 2006-10-31
I have a similar problem.  My router runs DHCP so I don't have hosts files on my machines.

  I've managed to get my Kubuntu Dapper box to share as long as the IP address is known.

  I have an older box on the network loaded with Xubuntu Dapper that I can see using my Kubuntu box, a Knoppix laptop, and a WinXP desktop.  However, when I go to list the shares I get a message that the Xubuntu box doesn't exist.

  When I look at my router, I don't see host names for my Ubuntu-based machines, just IP addresses.  I think this is part of my problem.  I think I need a local DNS server but I've read that if I'm not careful this will wreak havoc on Internet name resolution.

  In any event, I'd like the set up peer-to-peer for my desktop machines, a static IP Samba server, and need only type in a host name to access any of them.  I think I've got a pretty good handle on configuring shares, but I think my issue is elsewhere in the server setup.  I've even poked holes in my firewall so that SMB, SSH, and HTTPS(for webmin) can get through.

HELP!!

---

### Post by David Corrales on 2006-10-31
You can also set the Samba server to be a WINS name server. Think of it like DNS but for windows shares.

---

### Post by dgray_from_dc on 2006-11-01
I've got my Xubuntu box set up to be a WINS server (though I don't know that I've done it correctly).  Should I change the master browser priority?

I also discovered that if I drop out to a shell, I can sudo mount with no problem.

However, most of the time, I still can't browse the network or shares with smb4k or xsmBrowser without already establishing a connection manually.  And even when I can see the list of shares I can't mount through the GUI.

When configuring smb4k to use sudo to mount I get the following error:
"The file /etc/sudoers is currently edited by the user __.  Please try again later."
I am doing no such thing.:confused: 

And there is still the question of proper name resolution.  I can't even ping by hostname.  I've even tried using the [Xubuntubox].myhome.westell.com name using the domain of my ISP as I see it in webmin, nothing.

](*,)

Edit:

I just discovered that my router has built-in firewall capabilities.  I opened up the appropriate ports on the appropriate IP address ranges and got a lot more browsing capability.  After doing that, I discovered that for some reason when I got the /etc/sudoers error it was a result of the password dialog coming up behind the smb4k window.

---

### Post by dgray_from_dc on 2006-11-06
> **David Corrales said:**
> You can also set the Samba server to be a WINS name server. Think of it like DNS but for windows shares.

Thanks David!  After resolving the issue with my router, WINS worked like a charm (at least within the Samba framework).

  The thing I don't understand is that I set up my Xubuntu box as my WINS server and my Kubuntu box keeps taking over as master (even when Xubuntu is started first).  I guess this isn't a problem, seeing as when one goes down the other takes over.  I still just want to know how to do it right.  Again, could this be a Master Browser setting issue?  They're both at the default of 20.

And am I barking up the wrong tree for answers for DNS settings?  Anyone happen to know a thread where I can find this info off-hand?

---

### Post by dgray_from_dc on 2007-01-11
Update:

  I started over with the older box.  I installed Kubuntu on it and got Samba and Webmin up and running.  I gave the new machine a master browser setting of 254 (highest) and everything works just fine now.

---

