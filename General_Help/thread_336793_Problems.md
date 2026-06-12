---
title: "Problems"
date: 2007-01-12
forum: General Help
---

### Post by Requiem on 2007-01-12
Excuse me, could anyone help me with this problem?

Problem is, i can't contact the repos. I get a Connection refused error, why?  I can ping it just fine, but it keeps refusing connections. I guess I did something wrong but i can't figure it out. Pleaase help.

I'm on dapper, gnome. this is the error message from apt-get AND synaptic

> W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/w/w3m/w3m_0.5.1-4ubuntu2.6.06_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/w/w3m/w3m_0.5.1-4ubuntu2.6.06_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/d/dbus/libdbus-1-2_0.60-6ubuntu8.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/dbus/libdbus-1-2_0.60-6ubuntu8.1_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/d/dbus/dbus_0.60-6ubuntu8.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/dbus/dbus_0.60-6ubuntu8.1_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/d/dbus/libdbus-glib-1-2_0.60-6ubuntu8.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/dbus/libdbus-glib-1-2_0.60-6ubuntu8.1_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/d/dbus/dbus-1-utils_0.60-6ubuntu8.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/dbus/dbus-1-utils_0.60-6ubuntu8.1_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_1.5.dfsg+1.5.0.9-0ubuntu0.6.06_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_1.5.dfsg+1.5.0.9-0ubuntu0.6.06_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/libnspr4_1.firefox1.5.dfsg+1.5.0.9-0ubuntu0.6.06_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/libnspr4_1.firefox1.5.dfsg+1.5.0.9-0ubuntu0.6.06_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/libnss3_1.firefox1.5.dfsg+1.5.0.9-0ubuntu0.6.06_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/libnss3_1.firefox1.5.dfsg+1.5.0.9-0ubuntu0.6.06_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_1.5.dfsg+1.5.0.9-0ubuntu0.6.06_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_1.5.dfsg+1.5.0.9-0ubuntu0.6.06_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-common-data_0.6.10-0ubuntu3.4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-common-data_0.6.10-0ubuntu3.4_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-common3_0.6.10-0ubuntu3.4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-common3_0.6.10-0ubuntu3.4_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-client3_0.6.10-0ubuntu3.4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-client3_0.6.10-0ubuntu3.4_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-glib1_0.6.10-0ubuntu3.4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-glib1_0.6.10-0ubuntu3.4_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/d/dbus/libdbus-1-cil_0.60-6ubuntu8.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/dbus/libdbus-1-cil_0.60-6ubuntu8.1_all.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mozilla-thunderbird/mozilla-thunderbird_1.5.0.9-0ubuntu0.6.06_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mozilla-thunderbird/mozilla-thunderbird_1.5.0.9-0ubuntu0.6.06_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/d/dbus/python2.4-dbus_0.60-6ubuntu8.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/dbus/python2.4-dbus_0.60-6ubuntu8.1_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.5_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.5_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

And this is a sample ping...

> PING archive.ubuntu.com (195.248.90.35) 56(84) bytes of data.
64 bytes from 195.248.90.35: icmp_seq=1 ttl=50 time=207 ms
64 bytes from 195.248.90.35: icmp_seq=2 ttl=50 time=207 ms
64 bytes from 195.248.90.35: icmp_seq=3 ttl=50 time=205 ms
64 bytes from 195.248.90.35: icmp_seq=4 ttl=50 time=208 ms
64 bytes from 195.248.90.35: icmp_seq=5 ttl=50 time=205 ms
64 bytes from 195.248.90.35: icmp_seq=6 ttl=50 time=206 ms
64 bytes from 195.248.90.35: icmp_seq=7 ttl=50 time=208 ms
64 bytes from 195.248.90.35: icmp_seq=8 ttl=50 time=207 ms
64 bytes from 195.248.90.35: icmp_seq=9 ttl=50 time=207 ms
64 bytes from 195.248.90.35: icmp_seq=10 ttl=50 time=206 ms
64 bytes from 195.248.90.35: icmp_seq=11 ttl=50 time=208 ms
64 bytes from 195.248.90.35: icmp_seq=12 ttl=50 time=205 ms

--- archive.ubuntu.com ping statistics ---
12 packets transmitted, 12 received, 0% packet loss, time 11044ms
rtt min/avg/max/mdev = 205.078/207.032/208.348/1.245 ms


---

### Post by Sef on 2007-01-12
Post your sources list here please.

From the terminal (Applications > Accessories > Terminal):

cat /etc/apt/sources.list

---

### Post by nikhilk on 2007-01-12
From the ping output we can see the IP for archive.ubuntu.com is 195.248.90.35 but from the apt output the IP tried is 127.0.0.1 i.e. localhost! It is trying to fetch data from localhost:4001. Did you change your router settings lately, some port forwarding or something like that?

---

### Post by blackened on 2007-01-12
> **nikhilk said:**
> From the ping output we can see the IP for archive.ubuntu.com is 195.248.90.35 but from the apt output the IP tried is 127.0.0.1 i.e. localhost! It is trying to fetch data from localhost:4001. Did you change your router settings lately, some port forwarding or something like that?

nikhilk is right, that's a loopback address. Dunno why I didn't see that the first time I read this thread. You must've recently changed something in your router settings.  Because ping works as expected I would assume it to be something in the application level port forwarding settings. But then you know what they say about assumptions.

---

### Post by Requiem on 2007-01-13
Yep that's a loopback address but given that some GUIs use a loopback to connect to their own processes I'm not sure it is abnormal. That's what I thought I did something wrong, but can't say what.

The only thing that springs to mind is my failed attempt at intalling tor. Actually i did install tor, but never got to set it up, this is tor current output.

> Jan 12 23:21:20.190 [notice] Tor v0.1.0.16. This is experimental software. Do not rely on it for strong anonymity.
Jan 12 23:21:20.344 [warn] /var/lib/tor is not owned by this UID (1000). You must fix this to proceed.
Jan 12 23:21:20.344 [err] options_act(): Couldn't access/create private data directory /var/lib/tor
Jan 12 23:21:20.344 [err] init_from_config(): Acting on config options left us in a broken state. Dying.

And this is anon-proxy's

> [2007/01/12-23:25:59, critical] You must specifiy, which kind of Mix you want to run!
[2007/01/12-23:25:59, critical] Use -j or -c
[2007/01/12-23:25:59, critical] Or try --help for more options.
[2007/01/12-23:25:59, critical] Exiting...
[2007/01/12-23:25:59, critical] Terminating Programm!


How ever given that all the network-related apps work fine i doubt this as something to do with my problem.

I'm posting my sources file along with a ping ran as root, to confirm that also root can use the network. BTW I let automatix alter my sources.list, yes, but I haven't had any problems updating software, until now.

Thanks again I'm sure this has a solution.

> 
## Automatix sources.list
## This is automatically generated by Automatix


####################################
### Official Ubuntu Repositories ###
####################################

# Dapper Final Release Repository
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

# Dapper Security Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security multiverse

# Dapper Bugfix Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates multiverse

# Dapper Backports (new software versions, provided by the Ubuntu Backports Pr oject)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main


##############################
### Automatix Repositories ###
##############################

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

## created by automatixrepo3


> 
PING [www.l.google.com](www.l.google.com) (66.102.7.99) 56(84) bytes of data.
64 bytes from mc-in-f99.google.com (66.102.7.99): icmp_seq=1 ttl=240 time=64.0 ms
64 bytes from mc-in-f99.google.com (66.102.7.99): icmp_seq=2 ttl=240 time=68.2 ms
64 bytes from mc-in-f99.google.com (66.102.7.99): icmp_seq=3 ttl=240 time=65.5 ms
64 bytes from mc-in-f99.google.com (66.102.7.99): icmp_seq=4 ttl=240 time=64.9 ms
64 bytes from mc-in-f99.google.com (66.102.7.99): icmp_seq=5 ttl=240 time=66.4 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4019ms
rtt min/avg/max/mdev = 64.074/65.861/68.251/1.461 ms

---

### Post by Requiem on 2007-01-14
Don't leave me for dead yet. I know apt/synaptic are trying to connect to localhost instead of the proper repos, that the urls for the repos are ok, and that both root and my normal user account can use the network just fine and can ping to said repos.

Yes anon-proxy is installed but not in use. 

The root of the problems is that apt is looking for the repos in a funny place, what can I do about it?

---

### Post by blackened on 2007-01-14
Only other thing I could suggest would be to modify /etc/apt/apt.conf to suit your proxy config and see if that helps.

---

### Post by Requiem on 2007-01-15
this is all of my apt.conf:

> APT::Authentication::TrustCDROM "true";
Acquire::http::Proxy "false";


i tryed changing false to true and doing a apt-get update, it returns the same message...

EDIT: i think i found the solution here:

[http://forums.debian.net/viewtopic.php?t=310&](http://forums.debian.net/viewtopic.php?t=310&)

I'll know after rebooting. Is there I can help other users not to fall in this trap?

Also, that link I pasted, I didn't know an URL could end in &, what could that do?

---

### Post by blackened on 2007-01-15
You could email the guys at anon-proxy as it's apparently at the root of the problem. Maybe have them put something about it in their FAQ. And yeah, a URL can end in an ampersand. Usually it's to link some parameters together when calling up a server-side script.

---

