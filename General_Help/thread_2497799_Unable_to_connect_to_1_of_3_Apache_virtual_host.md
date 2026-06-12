---
title: "Unable to connect to 1 of 3 Apache virtual host"
date: 2024-05-17
forum: General Help
---

### Post by rodmanb on 2024-05-17
I'm trying to add Nextcloud to my domain. Have had it working before but not like I wanted so, I elected for a fresh install. I have the domain and 2 sub-domains. The domain and 1 of the sub-domains work perfectly. Unfortunately, the subdomain I want to use for Nextcloud is "Unable to connect". I've check, recheck and triple, quadruple checked the sites-available .conf file, the DNS record and things that made no sense to check (like looking for your keys in the freezer). In fact, I'm total at my wits end as to why 2 sites work and the other won't connect at all.
Any thoughts or ideas?

---

### Post by TheFu on 2024-05-18
I have 1 config file for each virtualhost.  Then I get one working and copy it over for the next one, modify the different parts as needed, get that working, then copy over the new file to the 3rd config file and get that working.

In short, simplify and test.

It should be clear that if you don't actually post the config file(s) here, nobody can help.

A few years ago, I got tired of Nextcloud upgrades failing (I'm not a PHP guy) and setup an LXC container to install the Nextcloud snap inside.  I've been using the Nextcloud snap for a few years and it has been maintained through snap upgrades (sometimes unwanted) for all this time.  Today, it same I'm running .... 
Nextcloud Hub 6 (27.1.1)

When I initially installed, it was v24 and I told the snap to never upgrade a major version without my explicit request. With snaps, backing up the entire container is 1 command, though it is extremely inefficient for both storage and time, it does work.  I used the "approved" backup method 1 time.  My daily backups use /snap/bin/nextcloud.export as the main method.  Then I use my normal backup tool to get daily, versioned, backups.  I also grab the container settings using the snap command and the snap HTTP interface.  

There are many things to like about the nextcloud snap and just a few things to dislike.  I do run a reverse proxy in front of the nextcloud snap system for added protections, TLS terminations and to keep nextcloud off the internet.  I don't allow access to most of the internal systems here without people from outside using a full VPN connection.  Anyway, it might be worth checking into for your needs.

---

