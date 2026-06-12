---
title: "Internet Cafe Problem"
date: 2007-06-13
forum: General Help
---

### Post by shawnerz on 2007-06-13
All,
I am (still) running Edgy Eft on a notebook computer.  It is a dual boot machine with Windows and Ubuntu.  I am having problems at the Internet cafe.  Everything works perfectly in Windows and IE.  I start IE and my browser gets redirected to the Cafe's webpage so I can login and pay for the service.
When I boot into Linux, Firefox can not connect to the webpage.
I downloaded Firefox for Windows, and that works perfectly.

I am running the Firestarter firewall, but it is disabled.  In the Networking section, I am set to DHCP.
ifconfig tells me I got an IP address, and I have the address of the gateway.
However, when I ping the gateway, I get a message saying the network is unreachable.

At first I thought this may be a Firefox issue.  Then when I tried to ping the gateway and couldn't, that indicated to me that it is a networking issue.
Is there something in /etc that I do not have configured correctly?  Any ideas anyone?
Thanks in advance,
-Shawn

---

### Post by Blayde on 2007-06-13
Here are some questions I would ask myself in this situation:

Does Ubuntu connect to other networks w/o problems?
Is the ip address & gateway you get on Windows similar to the ip address & gateway on Ubuntu?
Can you ping your own ip address?
Does the cafe use a proxy server that isn't getting set up correctly in Ubunutu?
Does the cafe restrict usage of other operating systems on it's network?

I hope one of these helps you w/ your problem.

---

### Post by DivineOmega on 2007-06-13
Set the Firefox proxy settings to automatic and you should be fine. I had a similar issue at my University's network.

---

### Post by shawnerz on 2007-06-14
I think I answer both Blayde and DO's questions in one post.
Blayde: 
Does Ubuntu connect to other networks w/o problems?
Yes.  On my home network, Ubuntu works fine.  However, my home network uses static IP addressing.

Is the ip address & gateway you get on Windows similar to the ip address & gateway on Ubuntu?
Yes.  I did get a different IP address, but it is within the range of valid IP addresses (192.168.4.XXX)

Can you ping your own ip address? 
 HHmm...haven't tried.  I'll do that and get back to you.

Does the cafe use a proxy server that isn't getting set up correctly in Ubunutu?
No proxy.

Does the cafe restrict usage of other operating systems on it's network?
There is nothing in writing that I know of.  It is possible that buried in the Terms of Service, it states that the network only supports IE.  I haven't read them that closely.

DO: The Proxy settings are set to automatic.  Still doesn't work. :(

I originally thought this was a Firefox problem.  I made a post on MozillaZine.org.  One suggestions was to change the agent to fake the Internet Cafe into thinking I'm running IE.
I will give that a shot and see what happens.
Thanks for the suggestions.
-Shawn

---

### Post by warcriminal on 2007-06-14
Another important topic is, is there wireless at the Cafe that may be grabbing the IP for you?  If that is the case you have to login to the wireless router or else the only thing you can see is the IP of the router which includes their webpage.

Try disabling wireless as well.

---

### Post by HereInOz on 2007-06-14
The problem is probably that the router DHCP server at the Internet cafe is not properly relaying the DNS settings to the Ubuntu installation, or Ubuntu is not properly accepting them.  This happens with some routers and some Ubuntu installations.

How to fix?  Either set up a static IP with static DNS at each Internet cafe (not a brilliant idea, but it would work :) ) or upgrade to Feisty, which has much better networking, and solves this problem in almost every case.

---

### Post by Blayde on 2007-06-14
The last thing I can think of is to erase your static ip when you switch to DHCP mode. I've had problems in the past with the Network Manager set to DHCP, but with an ip address in the static settings below. After you erase the static ip, disable networking and then enable it again. That's what I did for awhile when I switched between my home network and school network. Now I have two profiles that I switch between - it's much faster.

---

### Post by shawnerz on 2007-06-16
Sorry, I've been away for a couple of days.  Just to tie up the loose ends:
The Internet cafe does not have wireless.  It is all hard wired.  Wireless has never worked properly on my laptop in Ubuntu.  I figured I'd cross that bridge when I got to it.
Pinging my own IP address does work.
Switching the agent in Firefox does not solve the problem.
Unless there are other ideas, I guess the solution is to go to Fiesty.
Thanks,
-Shawn

---

