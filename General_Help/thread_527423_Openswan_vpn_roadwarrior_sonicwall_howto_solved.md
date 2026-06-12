---
title: "Openswan vpn roadwarrior sonicwall howto solved"
date: 2007-08-16
forum: General Help
---

### Post by john_navarro on 2007-08-16
After 100 hours of effort and help from MOH and MCRXDS on the IRC #openswan forum I've got a roadwarrior (remote laptop) VPN session to a Sonicwall TZ170 firewall with the standard OS working with Ubuntu Feisty. Setting up openswan it not trivial and having full access to the firewall made things much easier. But I'd like to document what I did to get things working and some hints which may help others trying to eastablish VPN's with other devices. This is not a hand-holding HOWTO but more of a NOTES dump which should help you get things working.

IMPORTANT
Be sure you have only one VPN application installeded. So for this HOWTO, make sure OpenSwan in only install. Nothing else such as strongswan, racoon, kvpnc, etc.   Port 500 being used by something else is a good indication that you have another VPN type application running. A &#8220;netstat -an | grep :500&#8221; will show this to you.

BE ROOT
You want to do all you config testing and building as root &#8211; forget sudo.  So in a terminal type   &#8220;sudo su&#8221;

RE STARTING  THE VPN  SUBSYSTEM (IPSEC)
ipsec setup --stop         (shuts it down - that's dash dash stop)
ipsec setup --start          (brings it back up - that's dash dash start)

STARTING VPN CONNECTION
ipsec auto --add home        (add this vpn configuration to subsystem in memory)
ipsec auto --up home          (bring up the vpn connection)

home = my conection defition defined within the ipsec.conf file. the ipsec.conf file can have more than one defintion.


STOPPING VPN CONNECTION
ipsec auto --down home    (break the vpn connection - dash dash down)
ipsec auto --delete home   (bring up the vpn connection - dash dash delete )

OTHER COMMANDS
ipsec look           (shows you vpn routes)
ipsec barf            (dumps all VPN config info)
ipsec status


TROUBLESHOOTING STUFF

Payload malformed:   Typically means you have a wrong Phase 1 [SA]. check to see if the encryption algorithms are the same on each side of the VPN tunnel.

No Proposal chosen:  You will see this a lot when things are broken. Basically you have to match the firewall and openswan proposals. For example, if on the firewall you have for phase one  3DES SHA1 using Group 5, then you will get a &#8220;no proposal chosen&#8221; if you set up Openswan to use 3DES SHA1 Group2&#8221;.  More later on this. What you should know is that if ANYTHING is different with ID setups or proposals you will get the generic &#8220;no proposals chosen.&#8221;  This will drive you nuts after a while.

VPN up but can't ping:  
  a) be sure that you have enabled VPN NAT Translation on sonicwall
  b) check to make sure that the firewall software running on Ubuntu is not blocking pings or other comms through vpn. once the vpn is up packets are sent via ESP protocol.
  c) make sure that the local client network addressing is different than from that of the soncwall. CHECK TCPIP MASKS. For example you can not have a local and remote network using the same addressing; i.e.  192.168.1.0


Multiple interfaces: if you have multiple interfaces be sure to properly define interfaces within the ipsec.conf file;  i.e.  interfaces="ipsec0=eth0"
        
An IPSEC client uses UDP port 500 and protocol ESP (protocol 50).


PROPOSALS:

Group1: 768 bits
Group2: 1024 bits
Group5: 1536 bits

On the Sonicwall I had for IKE (phase 1): Group 5, 3DES, SHA1

My ipsec.conf file then had:      ike=3des-sha1-modp1536


The -modp1536 is how you tell openswan to use group 5. And to specify group 2 you would have used -modp1024 instead.


HOW I DID TESTING
I had two terminal windows open and wireshark running. One window was running &#8220;tail -f /var/log/auth.log&#8221; so that I could see what was being logged as I made changes. I'd look at the packets and what was being logged to understand what was going on.


AUTHENTICATION SNAGS
As a stated earlier if authentication isn't set up correctly you'll get the generic &#8220;no proposals chosen&#8221; message leaving you to guess what's going on. It was a big surprise when things started working for me because all I was getting were &#8220;no proposals chosen&#8221; earlier.


MY SONICWALL VPN CONFIGURATION

VPN -> Settings -> GROUP VPN
   IPSEC keying mode: IKE using preshared secrets
   IKE (phase 1) Proposal: Group 5, 3des, sha1
   ipsec (phase 2) proposal: esp, 3des, sha1, PFS disabled
   under advanced: check off (select) require authentication of VPN client via xauth

VPN -> Advanced
   be sure to enable NAT traversal
USERS -> Local Users
   create an ID and be sure to enable (check it off) vpn client access   (example    john99 with password &#8220;abcdefg&#8221;)

VPN -> Settings
   be sure ENABLE VPN is checked and write down the Unique Firewall Identification for later use (for example (snw12345)
   also put something in for the shared secret  (For example: A100B200C300)


IPSEC.CONF  -   DO NOT include my comments encased in ( )

version	2.0	# conforms to second version of ipsec.conf specification

config setup
	nat_traversal=yes
	nhelpers=1
	interfaces="ipsec0=eth0"

conn home
	 type=tunnel
	 leftid=@john00
	 left=192.168.111.121                                     (your laptop ip address)
	 leftxauthclient=yes
	 right=1.1.1.1                                                   (sonicwall wan ip address or  FQDN; i.e.  mysonic.mydomain.com )
	 rightsubnet=172.17.1.0/24                             (sonicwall lan subnet)
	 rightxauthserver=yes
         rightid=@snw12345                                        (sonicwall unique firewall identifier)
	 authby=secret
	 auto=add
	 auth=esp
	 esp=3des-sha1
	 ike=3des-sha1-modp1536                             (group 5)
	 xauth=yes
	 pfs=no
 	 keyingtries=1
	 aggrmode=yes               

#Disable Opportunistic Encryption

include /etc/ipsec.d/examples/no_oe.conf



IPSEC.SECRETS
@john00 @snw12345 : PSK "A100B200C300"    (this is the shared secret under the VPN Policy)


ESTABLISHING TUNNEL
ipsec auto --add home        ( dash dash add space home )
ipsec auto --up home          ( dash dash up space home )


I was then prompted for a user ID &#8211; I typed in john00
then I was prompted for password &#8211; I typed in qwerty

vpn was then established!

To shut it all down: 

ipsec auto --down home
ipsec auto --delete home        
ipsec setup --stop 


Good Luck!

---

### Post by john_navarro on 2007-08-16
Attached are Sonicwall config screen shots

---

### Post by john_navarro on 2007-08-16
More screen shots

---

### Post by learnincurve on 2007-09-21
Hi,

 Thank you so much for the excellent guide. Setting the encryprion strength in the IKE string had been a real problem, and I couldn't find it documented anywhere.

My next problem is assigning an IP address for the OpenSwan Road Warrior on the virtual network. SonicWall TZ 170 standard v. 3.0.0.1 to OpenSwan 2.4.9

I'v efollowed your instructions, using DH5, ike=3des-sha1-modp1536, esp=3des-sha1 and aggrmode

Authentication works like a dream now, but I'm still unable to communicate with the private net (172.16.2.0/24). Seems I'm failing to get an IP.  Do you know what protocol the SonicWall tz170 uses? I'm guessing it's not l2tp by default as this has to be switched on specifically. The whole process is hidden in the Doze Global VPN Client which creates a virtual adapter apparently getting its IP through standard dhcp.

Cheers!

---

### Post by john_navarro on 2007-10-19
You're not going to get an IP address as you would with dial-up. What you're doing is establishing an encrypted tunnel between two machines either locally or over the internet.

If you're connected and can't ping then start looking at routing issues or a firewall on the box is blocking pings.

---

### Post by georgious_ on 2007-11-05
Hey John,
I've spend quite a lot of time bumping my head against the wall with Sonicwall.
I've tried your tutorial but unfortunately get

003 "imatrix" #1: multiple transforms were set in aggressive mode. Only first on                       e used.
003 "imatrix" #1: transform (5,2,2,0) ignored.
003 "imatrix" #1: multiple transforms were set in aggressive mode. Only first on                         e used.
003 "imatrix" #1: transform (5,2,2,0) ignored.
112 "imatrix" #1: STATE_AGGR_I1: initiate
003 "imatrix" #1: ignoring unknown Vendor ID payload [404bf439522ca3f6]
003 "imatrix" #1: received Vendor ID payload [XAUTH]
003 "imatrix" #1: received Hash Payload does not match computed value
223 "imatrix" #1: STATE_AGGR_I1: INVALID_HASH_INFORMATION

here is my ipsec.conf

version 2.0
config setup
	nat_traversal=yes
	nhelpers=1
	interfaces="ipsec0=ppp0"

conn imatrix
	type=tunnel
	left=78.90.115.***
	leftsubnet=192.168.101.11/32
	leftid=@gmomchilov
	leftxauthclient=yes
	right=209.216.***.***
	rightsubnet=192.168.200.1/24
	rightid=@0006B1156***
	rightxauthserver=yes
	keyingtries=0
	pfs=no
	authby=secret
	auto=add
	auth=esp
	esp=3des-sha1
	ike=3des-sha1
	xauth=yes
	aggrmode=yes

#Disable Opportunistic Encryption

include /etc/ipsec.d/examples/no_oe.conf

Any help would be greatly appreciated.

---

### Post by abmmydeen on 2008-01-07
Hi John,

I am using almost the same setup that is Openswan-2.4.10 as client as roadwarrior but through GPRS Modem (wireless) instead of how you have connected your PC through wired modem.

Moreover i am using same Sonicwall TZ 170 Enhanced Firewall.  I cannot get tunnel up. I have done it using the pdf from teh following link.

[http://www.sonicwall.com/downloads/SonicOS_Enhanced_to_Openswan_Using_GroupVPN_with_XAUTH.pdf](http://www.sonicwall.com/downloads/SonicOS_Enhanced_to_Openswan_Using_GroupVPN_with_XAUTH.pdf)

You reply is very much appreciated...

---

### Post by john_navarro on 2008-02-13
Another thing to consider if you manager to get the tunnel up but you can't ping anything on the other side:

make sure IP forwarding is enabled in kernel. To check issue this command:

sysctl net.ipv4.ip_forward

if it returns zero then it's diabled. To enable do the following:

on the fly change:  sysctl -w net.ipv4.ip_forward=1

for a permanent change:
vi /etc/sysctl.conf
add line:  net.ipv4.ip_forward = 1   or uncomment existing line 
then reboot or issue: sysctl -p /etc/sysctl.conf

---

### Post by msjones on 2008-02-13
Can anybody help me with my connection to my work VPN?

I am trying to connect to a sonicwall 3060 pro firewall using openswan.

When I try and start ipsec (**sudo ipsec setup --start**) I get the following error:

**ipsec_setup: (/etc/ipsec.conf, line 6) section header "nat_traversal=yes" has wrong number of fields (1) -- `--start' aborted**

Here is my ipsec.conf:

version	2.0	# conforms to second version of ipsec.conf specification

# basic configuration

config setup
nat_traversal=yes
nhelpers=1
interfaces="ipsec0=eth18"

# Add connections here

conn work
type=tunnel
left=**********
leftsubnet=**********
leftid=@*********
leftxauthclient=yes
right=80.1.********
rightsubnet=************
rightid=@0006B10D52F8
rightxauthserver=yes
keyingtries=0
pfs=no
auto=add
auth=esp
esp=3des-sha1
ike=3des-sha1
xauth=yes
authby=secret
aggrmode=yes

Openswan ipsec.secrets
# Create an entry in the ipsec.secrets file:
@GroupVPN @0006B10D52F8 : PSK "***********************"

# Disable Opportunistic Encryption

include /etc/ipsec.d/examples/no_oe.conf

Can anybody help??

---

### Post by fortran01 on 2008-03-20
I'm getting the following error. Any hints?

112 "casc" #6: STATE_AGGR_I1: initiate
003 "casc" #6: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-00]
003 "casc" #6: ignoring unknown Vendor ID payload [404bf439522ca3f6]
003 "casc" #6: received Vendor ID payload [XAUTH]
003 "casc" #6: Can't authenticate: no preshared key found for `@plap' and `@Cas-Datacenter'.  Attribute OAKLEY_AUTHENTICATION_METHOD
003 "casc" #6: no acceptable Oakley Transform
214 "casc" #6: STATE_AGGR_I1: NO_PROPOSAL_CHOSEN

---

### Post by itsdaveperdue on 2008-04-25
msjones:

Try tabbing out the configuration file spacing.  so:

```

config setup
        nat_traversal=1

```

Here is my ipsec.conf:

```

version 2.0 # conforms to second version of ipsec.conf specification

config setup
	nat_traversal=yes
	nhelpers=1
	interfaces="ipsec0=eth0"

conn home
	type=tunnel
	leftid=@GroupVPN
	left=192.168.5.193
	leftsubnet=192.168.5.193/32
	leftxauthclient=yes
	right=11.22.33.44
	rightsubnet=192.168.100.0/24
	rightxauthserver=yes
	rightid=@0001234567
	authby=secret
	auto=add
	auth=esp
	esp=3des-sha1
	ike=3des-sha1-modp1536
	xauth=yes
	pfs=no
	keyingtries=1
	aggrmode=yes

#Disable Opportunistic Encryption

include /etc/ipsec.d/examples/no_oe.conf

```

That seemed to help me.

I've also noticed that instead of putting my username as the left ID I had to put @GroupVPN (case sensitive) per the SonicWALL document.  Other than those changes everything worked fine.

Now I figured out the whole DHCP thing before, but I forgot how to do it.  So once I figure that out I'll put it here.

---

### Post by learnincurve on 2008-05-06
> Now I figured out the whole DHCP thing before, but I forgot how to do it. So once I figure that out I'll put it here.

It would be great if you could!

 I have a new problem (finally testing this from a physical machine instead of a VM. When I do a sysctl -w net.ipv4.ip_forward=1 before connecting, I get:

Enter secret:
002 "*****" #1: XAUTH: Answering XAUTH challenge with user='*****'
002 "*****" #1: transition from state STATE_XAUTH_I0 to state STATE_XAUTH_I1
004 "*****" #1: STATE_XAUTH_I1: XAUTH client - awaiting CFG_set
037 "*****" #1: encountered fatal error in state STATE_XAUTH_I1

This didn't happen from VM (didn't help either :-( )

If I change it (back) to sysctl -w net.ipv4.ip_forward=0

Authentication is okay, but I can't connect to anything on other side.

Kernel 2.6.24 
Openswan IPsec 2.4.12

Cheers!

Marius

---

### Post by ctaborda on 2008-07-12
Anyone got it to fully work? I'm having a weird issue now, its saying:

# We cannot identify ourselves with either end of this connection.

---

### Post by ctaborda on 2008-07-12
Whenever I start it, I see this in the logs:

Jul 12 02:10:42 mylaptop pluto[11066]: packet from 204.11.XXX.XXX:500: ignoring informational payload, type NO_PROPOSAL_CHOSEN

Any idea?

Edit: Got it to work!, something I did notice is that, whenever you make a change you got to take it all down, and start ipsec from 0, if not it doesn't apply new settings.

---

### Post by itsdaveperdue on 2008-07-12
Ya you do have to reestablish the tunnel if you change something.

Regarding the error:
# We cannot identify ourselves with either end of this connection.

If anyone finds this in the future they'll want to know the fix (not just that you've fixed it).  I've seen that error when I don't have the left and leftsubnet set properly in /etc/ipsec.conf.  So check there.

---

### Post by itsdaveperdue on 2008-07-12
> **ctaborda said:**
> Whenever I start it, I see this in the logs:

Jul 12 02:10:42 mylaptop pluto[11066]: packet from 204.11.XXX.XXX:500: ignoring informational payload, type NO_PROPOSAL_CHOSEN

Any idea?

Edit: Got it to work!, something I did notice is that, whenever you make a change you got to take it all down, and start ipsec from 0, if not it doesn't apply new settings.

Actually come to think of it...have you been able to get the VPN to work while youre using DHCP; so you don't have to edit the ipsec.conf file every time you get a different IP (e.g. at the coffee shop, at home, blah blah)?

---

