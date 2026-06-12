---
title: "Nextcloud installed - but how to share files and use https ?"
date: 2017-12-12
forum: General Help
---

### Post by freeflyjohn on 2017-12-12
[COLOR=#000000][FONT=HelveticaNeue]I have successfully installed Nextcloud on my Ubuntu server but I am struggling to share files outside of my home network and use https. [/FONT][/COLOR]
[COLOR=#000000][FONT=HelveticaNeue]
[/FONT][/COLOR]
[COLOR=#000000][FONT=HelveticaNeue]1) I can successfully login using my IP address (192.168.1.136) but I would like to be able to share files with friends and family outside of my home network.  How can I do this ?  I have a free dynamic DNS with Dynu so I tried replacing  my internal IP address (192.168.1.136) with my Dynu address but this didn't work.  I am also unsure if I need to open any ports on my router and Ubuntu firewall.[/FONT][/COLOR]
[COLOR=#000000][FONT=HelveticaNeue]
[/FONT][/COLOR]
[COLOR=#000000][FONT=HelveticaNeue]2) When I login to my Nextcloud account, I have the message "You are accessing this site via HTTP. We strongly suggest you configure your server to require using HTTPS instead".  I added the following to /etc/apache2/sites-available/nextcloud.conf but it didn't work.[/FONT][/COLOR]
[COLOR=#000000][FONT=HelveticaNeue]
[/FONT][/COLOR]
[COLOR=#000000][FONT=HelveticaNeue]<VirtualHost *:80>[/FONT][/COLOR]
[COLOR=#000000][FONT=HelveticaNeue]   ServerName cloud.nextcloud.com[/FONT][/COLOR]
[COLOR=#000000][FONT=HelveticaNeue]   Redirect permanent / [https://cloud.nextcloud.com/](https://cloud.nextcloud.com/)[/FONT][/COLOR]
[COLOR=#000000][FONT=HelveticaNeue]</VirtualHost>[/FONT][/COLOR]
[COLOR=#000000][FONT=HelveticaNeue]
[/FONT][/COLOR]
[COLOR=#000000][FONT=HelveticaNeue]Nextcloud version: 12.0.4[/FONT][/COLOR]
[COLOR=#000000][FONT=HelveticaNeue]Operating system and version: Ubuntu 16.04[/FONT][/COLOR]
[COLOR=#000000][FONT=HelveticaNeue]Apache or nginx version: Apache/2.4.18[/FONT][/COLOR]
[COLOR=#000000][FONT=HelveticaNeue]PHP version: 7.0.22[/FONT][/COLOR]

---

### Post by TheFu on 2017-12-13
1) You must open and forward the specific port needed for Nextcloud to work.  This is a huge security risk, so be aware that your entire network is at risk doing this.  The .136 IP seems like a DHCP internal LAN IP.  It is very, very, important that this "server" have a static LAN IP so the port forward doesn't need to change.  It is completely possible that .136 **is** a static IP, but unless you did something to make that happen intentionally, then it is not.  You probably want to forward port 443/tcp from the WAN IP to the static LAN IP.

2) You'll need to setup certificates, public certificates, to make a web server deal with HTTPS traffic. You cannot just forward HTTP traffic to HTTPS default ports and expect it to work.  There are thousands of how-to guides for this stuff.  You probably want to use "Let's Encrypt" certificates.  I do.


I would STRONGLY urge you not to allow HTTP/HTTPS traffic into your LAN.  Use a full VPN instead.  OpenVPN is well supported by every platform and would secure the LAN access.  Setting up openvpn servers are non-trivial, but 1,000,000x more secure than allowing unknown people/networks access to a server on your LAN.  The client-side use is fairly bonehead, which is perfect for non-technical people.  OpenVPN clients exist for every networked OS that I know and do not require root to use, though that does make it easier.  So, if you have android and want to access your nextcloud server, you would startup the openvpn client, which would create a tunnel into your home LAN for any use you might desire, including Nextcloud access.
Or ... you can use ssh as a SOCKS proxy and gain access to the internal website too. This is fine for technology-smart people, but not for normal people.

[https://www.linuxbabe.com/cloud-storage/setup-nextcloud-server-ubuntu-16-04-apache-mariadb-php7](https://www.linuxbabe.com/cloud-storage/setup-nextcloud-server-ubuntu-16-04-apache-mariadb-php7) are the instructions that I followed to setup nextcloud, Let's Encrypt.  In the end, I decided to lock down access and prevent anyone from the outside to have any access.  I'm not comfortable running php webapps over the public internet.  I've been using an ssh-SOCKS proxy for remote access when needed and sync any files needed on Android BEFORE leaving the LAN.

BTW, you cannot just use any DNS name you want.  nextcloud.com is already taken, so you cannot point there from outside your network.

Grasshopper, you have much to learn.  Which is completely fine. We all started somewhere.  I'd suggest you start with remote ssh first, however.

---

