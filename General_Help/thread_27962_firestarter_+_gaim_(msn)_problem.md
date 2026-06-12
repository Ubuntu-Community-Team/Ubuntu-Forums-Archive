---
title: "firestarter + gaim (msn) problem"
date: 2005-04-18
forum: General Help
---

### Post by tread on 2005-04-18
I've done a quick search but couldn't anything like this in the archives, so here is my problem:

I installed firestarter, and I'm running the default configuration, with dhcp enabled. I started gaim, and yahoo messenger starts fine. MSN gets stuck at the retrieving buddy list stage, and I looked at the debug window in gaim, the buddy list has been retrieved so it's probably stalling at a stage after that. 

I turned off the firewall, and msn started up fine.

Do I need to setup something in firestarter here? And if so, how? Need help here .. networking isn't one of my stronger points :(

---

### Post by tread on 2005-04-18
bump!

Just a quick note saying the default config worked with msn or didn't work would help too!
I'm going to try use netstat to find what ports msn is using while connecting, since the connection clearly reaches a certain point and then stops. My guess is that msn switches ports at that point .. more on that once i've used netstat.

---

### Post by tread on 2005-06-06
bumping this again ..

---

### Post by dresnu on 2005-06-06
To let gaim connect and do all the handshaking, list retrieving ecc. for   msn accounts you need to open port 1863. I guess you 're using a  restrictive outbound policy in firestarter, so you just need to add a rule in your whitelist for that port. As long as I know you also need to enable https(port 443) for msn, but If you can access https web pages you don't need to worry about that ;-)

---

### Post by tread on 2005-06-06
Doesnt work. My inbound policy is:
Allow connections from 
192.168.0.1 (gateway)
Allow service for:
Port 443 everyone
Port 1863 everyone
Port 5050 everyone

The outbound policy is permissive by default, and I haven't blacklisted any traffic yet.

---

### Post by RavenOfOdin on 2006-02-09
I'm having the same problem, and am on restrictive set-up as well.

My policy for MSN is set as follows:

Allow inbound connections from/outbound connections to:
65.54.239.140
207.46.4.0-207.46.4.255

Allow service for:

Port 1863: everyone
Port 6891-6901: everyone

When I disable the firewall briefly, sign in and then enable again - it works fine.

---

