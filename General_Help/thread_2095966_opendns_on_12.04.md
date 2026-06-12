---
title: "opendns on 12.04"
date: 2012-12-18
forum: General Help
---

### Post by Quarkrad on 2012-12-18
I have a dynamic ip from my ISP (TalkTalk) and configured opendns on my router.  I've set everything up but have an issue with the opendns updater that (I understand) talks to opendns when the ISP dynamically changes my ip address.  It is a little confusing what to do on ubuntu because opendns only provides an updater client for Windoze and Mac.   I have a text doc in /etc/ called ddclient.conf that contains the following text:

[B]##
## OpenDNS.com account-configuration
##
use=web, web=myip.dnsomatic.com
ssl=yes
daemon=3600
server=updates.opendns.com
protocol=dyndns2
login=*my opendns email address*
password=*my opendns password*
*my opendns network nickname*[/B]


so, I've set up the opendns end and set my router with the opendns dns addresses but it is not working.  The test 'blocked' web addresses I have in my opendns settings account are not blocked.  I'm not sure how the above ddclient.conf file speaks to opendns - is there something else I have to do?

---

### Post by jim_deadlock on 2012-12-18
You're getting mixed up. OpenDNS provides an OUTGOING DNS service. In other words it lets your computer lookup domain names of websites you're visiting and it also allows you to set up parental filters and that sort of thing, for OUTGOING connections. ddclient is not required for any of this, you simply enter the OpenDNS nameservers in your router settings and then you're good to go regardless of whether your ISP gives you a dynamic IP or not.

You need ddclient if you want to have a permanent domain name associated with your computer in order to run a service on it such as FTP or maybe a games server or something like that. For this, you have to get an account with a domain forwarding service such as no-ip.com, then set up ddclient to update your IP address on this account. Note: this is nothing to do with OpenDNS, that's already set up as above.

So the solution to your problem all depends on what exactly your aims are, which dyndns service you've signed up with etc.

---

### Post by jim_deadlock on 2012-12-18
I see now that dnsomatic.com is the DNS forwarding tool of OpenDNS (I didn't know they had one until now). Anyway, this is the reason they want you to enter your opendns login details in the ddclient.conf file. You should have at some point chosen a new domain name when setting up your dnsomatic account, right? So enter that, and your opendns details as it says.

You would then need to try and connect to whatever service you're running on your PC by using your new domain name. This assumes that your service is properly up and running and you've set up all your port forwarding correctly on your router.

---

### Post by Quarkrad on 2012-12-21
Thanks - I understand a little better now.  However, I have still not got this working.  All I have done is set up a free account on opendns and configured blocks on two domains to test to see if everything works.  My opendns setup looks like this - attached.  I am a bit confused where **ddclient.conf** sits in 12.04,  some pages say **/etc/ddclient.conf** and some **/etc/ddclient/ddclient.conf** - at the moment I have the file in both places!  My ddclient.conf looks like this:

[B]## OpenDNS.com account-configuration
##
use=web, web=myip.dnsomatic.com
ssl=yes
server=updates.opendns.com
protocol=dyndns2
login=xxxxxx@yyyyy.com
password=xxxxxxxxxx
home[/B]

Everything appears to work in the sense that I can browse and my two domains are blocked.  If I go to Welcome opendns I'm told I'm connected to opendns.  However, the next day my ISP provides me with a new ip and the domains are not blocked although Welcome Opendns tells I am connected.  I am confused what **ddclient.conf** is doing though - assuming it is supposed to be communicating with Opendns (I assume to inform that my (dynamic) ip address has changed) how does it do it?  Should ithere not be some sort of script somewhere so that when Ubuntu launches it runs ddclient.conf so that it tells Opendns of my ip change?

---

### Post by Quarkrad on 2012-12-22
I had errors in my ddclient.conf file and another file was missing - etc/default/ddclient.   I followed this page and it all worked.

[http://www.youtube.com/watch?v=iuDCuUEmKF4](http://www.youtube.com/watch?v=iuDCuUEmKF4)

---

