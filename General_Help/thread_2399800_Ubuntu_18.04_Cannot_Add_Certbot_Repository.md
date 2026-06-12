---
title: "Ubuntu 18.04 Cannot Add Certbot Repository"
date: 2018-08-29
forum: General Help
---

### Post by spock9458 on 2018-08-29
I am a bit of a noobie with ubuntu, but familiar with unix/linux a little bit.  I am configuring a web server for testing purposes, according to some tutorials I found posted on Digital Ocean, and I am on the step that involves setting up encryption with certbot.  I have had some issues with setting up the networking for the server - initially I was trying to configure netplan with the (default) installed cloud-init version, but I have since disabled that and configured a netplan yaml file using the renderer networkd.  I feel that my inability to add the repository for certbot is related to my possible incomplete networking setup. 

I am using a static IP address, and I have nameservers pointing to 8.8.8.8 address.  I can ping and receive replies from 8.8.8.8, and also I receive replies when I ping domain names such as google.com, so I think my dns resolution is working.  However when I try this command: [LEFT][COLOR=#3A3A3A][FONT=monospace]add-apt-repository ppa:certbot/certbot it takes quite a while but I eventually receive the following error: Cannot add PPA: 'ppa:~certbot/ubuntu/certbot'.
ERROR: '~certbot' user or team does not exist.

I have searched for answers through Google, but have found nothing that has fixed my issue. Can someone point me to the answer that will fix my problem?

Thanks,
Rob
[/FONT][/COLOR][/LEFT]

---

### Post by spock9458 on 2018-08-30
So the problem appears to be with my DMZ networking configuration.  I had originally set my firewall to allow only http, https, dns and ssh outbound to the internet from my dmz, where my web server is.  This morning I tried to add the ftp service to see if that would help, and it did not.  So just as an experiment I changed it to allow ALL traffic outbound and then the "add-apt-repository ppa:certbot/certbot" worked perfectly right away.  The question I have now - which specific service or port do I need to allow out through my firewall in order to add repositories, and any other functions my ubuntu web server might need?  Thanks,
Rob

---

