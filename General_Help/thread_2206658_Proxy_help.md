---
title: "Proxy help"
date: 2014-02-20
forum: General Help
---

### Post by fusionp on 2014-02-20
Hi all, I have a couple of questions.

First some basic background.

First off I have no real experience with proxies. I understand the concepts and have installed a test transparent proxy on a mikrotik device. Now as far as Ubuntu goes, I have recently configured a few Ubuntu servers, running a web hosting apache server, a postfix mail server and a server running owncloud. So I can make my way around the system but usually off someone else's documentation :-)

What I want to achieve? I run a W.I.S.P with around 400 users, my core router runs RouterOS and balances 4 WAN links with PCC. Now I would like to configure a transparent proxy so that I can redirect specific IP's to my proxy. Unfortunately Mikrotik built-in proxy does not play nice with PCC and mangle rules, there is some documentation out there to get it working but I've tried them all and re-written my mangle rules and it just never seems to work as intended....so I'm now considering configuring an Ubuntu server running Squid transparent proxy, so that I can redirect a particular customer IP to a payment reminder page.

At present I have a private class B network that NAT's out my 4 WAN ports. I don't want to use a hotspot, what I would like to do is place a proxy on the same subnet as my customers, the proxy will use one IP on the same subnet as my customers.

So first of all is this possible? or do I have to have the proxy in a DMZ or running with two separate IP's?
Secondly, will packets redirected to the proxy keep the original customers IP or will this be replaced with the mikrotiks IP?

Any help much appreciated

---

