---
title: "fully qualified hostname"
date: 2007-03-30
forum: General Help
---

### Post by dryder on 2007-03-30
Hi,

I've accumulated some questions that I can not resolve/understand so please forgive me if I ask them over the next few days ... MTIA :-)

When a document is sent to be faxed (efax) I get "Cannot get our fully qualified hostname".

I asked the developer and he felt a) it was not important to efax, b) that I had done something that now (as it was OK before) stopped the computer getting its hostname.

May I ask please:
1. What does the message mean?
2. Where is the hostname 'kept' - is it easily 'fixed'?

My Netgear router is the DHCP server and all LAN IP addresses for each computer are assigned in there according to its MAC address. The computer name is correct in that table. (But until I am fully conversant with Ubuntu/Linux and have everything working, this is my only linux box).

Many thanks,
David

---

### Post by acormack on 2007-03-31
Each computer has a hostname  e.g. computer1 and an ip address  11.1.1

The domain name system is used over the internet as away of allowing you to find computers by name instead of number.

But your networks has a computer1 and I might have one as well

So we need a way of knowing which computer1 we are looking for.  We do that using the domaind name

You might register  dryder.org  so your computer is computer1.dryder.org

The Fully Qualified Domain Name just means **hostname.domainname** format

The hostname is kept in /etc/hosts

You can check/set the hostname using the **hostname** command or using the system settings menu.

Alec

---

### Post by dryder on 2007-04-07
Hi,
My apologies for the unexpected and unavoidable absence.

In my /etc hostname file it simply says server-ubuntu, which is correct - the name I gave at installation.

I am still getting the efax error and occasionally elsewhere 'invalid hostname".

Is there a (safe) way of re-establishing/repairing the hostname throughout the system? Of course, the name in the file is the same as the name for the assigned IP address in my router dhcp table.

MTIA,

David

---

### Post by acormack on 2007-04-08
David

edit /etc/hosts (as root)

on the line that says **server-ubuntu**

replace the text **server-ubuntu** with 

**server-ubuntu.dryder.org   server-ubuntu**

if you type **man hosts** you will see the explanation that this is the fully qualified domain name FQDN followed by an alias.

You should then be able to ping (on your local network) either

ping server-ubuntu

or

ping server-ubuntu.dryder.org

Please note this will only work locally because you haven't registered the domain dryder.org on the Internet.

p.s.  dryder.org hasn't been registered by anyone else so for about £10 per annum you could register the domain and then receive emails in the format 

[email]david@dryder.org[/email] or {anything}@dryder.org and alias [www.dryder.org](www.dryder.org) to your own website if you have one.

Hope this helps.

---

### Post by dryder on 2007-04-08
Thank you very much Alec.

I will try it and appreciate your help.

David.

---

### Post by dryder on 2007-04-08
May I ask if I also need to edit the 'hostname' file which still says server-ubuntu?

As it did not change when I made the changes you suggested to /etc/hosts I am not sure if they serve different purposes.

Once I made the changes and rebooted Open Office gave me an error sayiny sopmething about needing to end a process - it went after an ofice app opened before I could make a note of it.

Apologies for troubling you - many thanks.

David

---

### Post by acormack on 2007-04-09
David

The hostname in /etc/hostname should match whatever is in /etc/hosts.  My files are shown below.

alec@kdtop:/etc$ **cat /etc/hosts**

127.0.0.1 localhost.localdomain localhost kdtop
127.0.1.1 kdtop

alec@kdtop:/etc$ **cat /etc/hostname**
kdtop

alec@kdtop:/etc$ **hostname -f**
localhost.localdomain

alec@kdtop:/etc$ **ping kdtop**
PING localhost.localdomain (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost.localdomain (127.0.0.1): icmp_seq=1 ttl=64 time=0.028 ms
64 bytes from localhost.localdomain (127.0.0.1): icmp_seq=2 ttl=64 time=0.029 ms
64 bytes from localhost.localdomain (127.0.0.1): icmp_seq=3 ttl=64 time=0.029 ms
64 bytes from localhost.localdomain (127.0.0.1): icmp_seq=4 ttl=64 time=0.029 ms
64 bytes from localhost.localdomain (127.0.0.1): icmp_seq=5 ttl=64 time=0.029 ms
64 bytes from localhost.localdomain (127.0.0.1): icmp_seq=6 ttl=64 time=0.028 ms

--- localhost.localdomain ping statistics ---            

alec@kdtop:/etc$ **ping localhost.localdomain**
PING localhost.localdomain (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost.localdomain (127.0.0.1): icmp_seq=1 ttl=64 time=0.028 ms
64 bytes from localhost.localdomain (127.0.0.1): icmp_seq=2 ttl=64 time=0.029 ms
64 bytes from localhost.localdomain (127.0.0.1): icmp_seq=3 ttl=64 time=0.029 ms
64 bytes from localhost.localdomain (127.0.0.1): icmp_seq=4 ttl=64 time=0.029 ms

--- localhost.localdomain ping statistics ---


Reading recent posts it seems that the 127.0.1.1 is a very recent addition (in Edgy?).  If you set up your files like mine above do you still have problems?

Alec

---

### Post by dryder on 2007-04-09
Hi Alec,
My files before and after following (I hope) your last post:
Before:
/etc/hosts:
127.0.0.1 localhost
127.0.1.1 server-ubuntu.dryder.org server-ubuntu

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

/etc/hostname:
server-ubuntu

Now:
/etc/hostname:
server-ubuntu.dryder.org server-ubuntu

(I have no idea what the "# The following lines are desirable for IPv6 capable hosts" section means).

I can ping both server-ubuntu.dryder.org and server-ubuntu (how do I get it to stop pinging without closing the terminal?) :-)

I never paid any attention to this before, but in the terminal I open to sign in as root (gksudo nautilus), these messages appear:
david@server-ubuntu:~$ gksudo nautilus
(nautilus:19880): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(nautilus:19880): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.

(and during editing the files):

(gedit:20039): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(gedit:20108 ): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Does this Authentication refer to the hostname above?

Many thanks for your perseverance.

David

---

