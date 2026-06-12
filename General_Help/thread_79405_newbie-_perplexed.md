---
title: "newbie- perplexed"
date: 2005-10-20
forum: General Help
---

### Post by drtvasudevan on 2005-10-20
am a newbie.
so sorry if these questions are silly or absurd. am still  getting the feel of linux.
whenever i try to do something through terminal there is an error msg.
given below is the msg generated.
the funny thing is the changes seem to take place though the error msg is given.
for example though there is an error msg while tryiong change the network settings, the changes happened and were accpted - namely activating eth0 and that is how i was able to connect to net.

what is happening?
regards
tv

tv@cdl01:~$ su
Password:

root@cdl01:/home/tv/Automatix # cd /.. root@cdl01:/ # sudo network-admin 
(network-admin:10327): Gdk-WARNING **: locale not supported by Xlib

(network-admin:10327): Gdk-WARNING **: cannot set locale modifiers

(network-admin:10327): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

** (network-admin:10327): CRITICAL **: gst_xml_element_set_content: assertion `node != NULL' failed
root@cdl01:/ #

---

