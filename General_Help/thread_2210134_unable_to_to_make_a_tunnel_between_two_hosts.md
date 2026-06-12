---
title: "unable to to make a tunnel between two hosts"
date: 2014-03-09
forum: General Help
---

### Post by neda2 on 2014-03-09
I am very new in Ubuntu and openswan. I have two virtual machines with installed Ubuntu 10.4 on a computer. i have also checked to see i the eth0 is bridge or not (it is not part of bridge). I want to make a tunnel between these two virtual machines. the ipsec.consf is as following after configuration:

# /etc/ipsec.conf - Openswan IPsec configuration file
# RCSID $Id: ipsec.conf.in,v 1.16 2005/07/26 12:29:45 ken Exp $


# This file:  /usr/share/doc/openswan/ipsec.conf-sample
#
# Manual:     ipsec.conf.5




version 2.0     # conforms to second version of ipsec.conf specification


# basic configuration
config setup
        # Do not set debug options to debug configuration issues!
        # plutodebug / klipsdebug = "all", "none" or a combation from below:
        # "raw crypt parsing emitting control klips pfkey natt x509 dpd private"
        # eg:
        # plutodebug="control parsing"
        #
        # enable to get logs per-peer
        # plutoopts="--perpeerlog"
        #
        # Again: only enable plutodebug or klipsdebug when asked by a developer
        #
        # NAT-TRAVERSAL support, see README.NAT-Traversal
       # plutodebug / klipsdebug = "all", "none" or a combation from below:
        # "raw crypt parsing emitting control klips pfkey natt x509 dpd private"
        # eg:
        # plutodebug="control parsing"
        #
        # enable to get logs per-peer
        # plutoopts="--perpeerlog"
        #
        # Again: only enable plutodebug or klipsdebug when asked by a developer
        #
        # NAT-TRAVERSAL support, see README.NAT-Traversal
        nat_traversal=yes
        # exclude networks used on server side by adding %v4:!a.b.c.0/24
        virtual_private=%v4:10.0.0.0/8,%v4:192.168.0.0/16,%v4:172.16.0.0/12
        # OE is now off by default. Uncomment and change to on, to enable.
        oe=off
        # which IPsec stack to use. netkey,klips,mast,auto or none
        protostack=netkey




# Add connections here


# sample VPN connection
# for more examples, see /etc/ipsec.d/examples/
conn test
        left=192.168.222.138
        leftsubnet=172.16.2.0/24
        leftrsasigkey=0sAQOZByIdUGh+PD3iWD7GOONfLutKOkKRwCVZNunSts9EL6uw8uJCwBcGfFMCxRPc2BqhZTwd$
        leftnexthop=%defaultroute
        right=192.168.222.137
        rightsubnet=172.16.1.0/24
        rightrsasigkey=0sAQOZByIdUGh+PD3iWD7GOONfLutKOkKRwCVZNunSts9EL6uw8uJCwBcGfFMCxRPc2BqhZTw$
        rightnexthop=%defaultroute
        auto=add


And the following for the other one:


conn test
        left=192.168.222.137
        leftsubnet=172.16.1.0/24
        leftrsasigkey=0sAQNZaNcBayXz1U6qZ7q602f7d6EC5Jg8Isp2gJLrYQwqGips2xVUDrWcX/sLuMGmzuVZRRwE$
        leftnexthop=%defaultroute
        right=192.168.222.138
        rightsubnet=172.16.2.0/24
        rightrsasigkey=0sAQNZaNcBayXz1U6qZ7q602f7d6EC5Jg8Isp2gJLrYQwqGips2xVUDrWcX/sLuMGmzuVZRRw$
        rightnexthop=%defaultroute
        auto=add


in both machies i added the routes and determine the interface via following command:
	root@ubuntu:/etc# ifconfig eth0:0 172.16.2.1 netmask 255.255.255.0
	root@ubuntu:/etc# route add 172.16.2.1 eth0:0
	root@ubuntu:/etc# route add -net 172.16.1.0 netmask 255.255.255.0 gw 172.16.2.1


but after adding and making up the tunel i got the foloowing:


	root@ubuntu:/etc# ipsec auto --add test
	root@ubuntu:/etc# ipsec auto --up test
	104 "test" #1: STATE_MAIN_I1: initiate
	003 "test" #1: received Vendor ID payload [Openswan (this version) 2.6.23 ]
	003 "test" #1: received Vendor ID payload [Dead Peer Detection]
	003 "test" #1: received Vendor ID payload [RFC 3947] method set to=109 
	106 "test" #1: STATE_MAIN_I2: sent MI2, expecting MR2
	003 "test" #1: NAT-Traversal: Result using RFC 3947 (NAT-Traversal): no NAT detected
	108 "test" #1: STATE_MAIN_I3: sent MI3, expecting MR3
	003 "test" #1: ignoring informational payload, type INVALID_KEY_INFORMATION msgid=00000000
	003 "test" #1: received and ignored informational message
	003 "test" #1: discarding duplicate packet; already STATE_MAIN_I3
	010 "test" #1: STATE_MAIN_I3: retransmission; will wait 20s for response
	003 "test" #1: ignoring informational payload, type INVALID_KEY_INFORMATION msgid=00000000
	003 "test" #1: received and ignored informational message
	003 "test" #1: discarding duplicate packet; already STATE_MAIN_I3
	010 "test" #1: STATE_MAIN_I3: retransmission; will wait 40s for response
	003 "test" #1: ignoring informational payload, type INVALID_KEY_INFORMATION msgid=00000000
	003 "test" #1: received and ignored informational message
	031 "test" #1: max number of retransmissions (2) reached STATE_MAIN_I3.  Possible authentication failure: no acceptable response to our first encrypted message
	000 "test" #1: starting keying attempt 2 of an unlimited number, but releasing whack




somebody please please help me i don't know what is the problem.

---

