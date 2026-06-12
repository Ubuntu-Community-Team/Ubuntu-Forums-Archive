---
title: "How to route traffics(through wifi-connections) by domain name(desktop)?"
date: 2021-09-21
forum: General Help
---

### Post by eSPiYa on 2021-09-21
How to achieve this? Having a list of domain names that can only be accessed through my mobile phone's wi-fi hotspot, if it is not connected on my phone's wi-fi hotspot it will block the connection.

I want to join a certain play-to-earn game where for some reason very strict to only have a max of 2 players per internet connection. And there are already 2 of them using this connection, so if I joined too, there's a huge chance that the 3 of us getting banned, so I'm going to use my phone's wi-fi hotspot to avoid this. Blocking my connection to the said site will prevent me from logging in using our home's connection to the site by accident.

I'm using Ubuntu Mate 21.04.

---

### Post by QIII on 2021-09-21
Is the two person limit a part of the ToS of access to the game?

---

### Post by ActionParsnip on 2021-09-22
Set your phone as a WiFi hot-spot and have one system connected to that

---

### Post by eSPiYa on 2021-09-22
> **QIII said:**
> Is the two person limit a part of the ToS of access to the game?
Unfortunately, yes. Their rules is quite weird for this but we have to abide or else we'll get banned.

---

### Post by The Cog on 2021-09-23
Do you want to maintain your house internet connection for everything else as you play, or to drop the house connection and use the phone exclusively while playing? If you wnat to split the traffic, do you have two different wifi interfaces?

When you are using the house, and when you are using the phone, are you given different IP addresses? "ip addr" or "hostname -I" will list all your current addresses.
Also, check the IP address of the game server(s). "host <domain-name> might tell you, but you need to do it several times in case they have multiple addresses.

Depending on the answers, it may be possible to configure firewall rules that only allow connections over your phone.

---

### Post by eSPiYa on 2021-09-23
> **The Cog said:**
> Do you want to maintain your house internet connection for everything else as you play, or to drop the house connection and use the phone exclusively while playing? If you wnat to split the traffic, do you have two different wifi interfaces?

When you are using the house, and when you are using the phone, are you given different IP addresses? "ip addr" or "hostname -I" will list all your current addresses.
Also, check the IP address of the game server(s). "host <domain-name> might tell you, but you need to do it several times in case they have multiple addresses.

Depending on the answers, it may be possible to configure firewall rules that only allow connections over your phone.

I assign IP addresses to my devices through our router by Mac Address, so the laptop that I'm using to play the said game(and running Ubuntu Mate) have a fix IP address, but I don't have that kind of option on my phone's hotspot. So the IP address changes.

---

### Post by DuckHook on 2021-09-23
Thread closed for staff review.

---

### Post by DuckHook on 2021-09-24
Thread re-opened after staff review.

---

