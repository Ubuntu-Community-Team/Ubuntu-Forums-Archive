---
title: "I need some proxy app"
date: 2005-05-05
forum: General Help
---

### Post by wporzo on 2005-05-05
First of all.. it's my first post in this huge community. This is good moment to say Hello! :)

.. and this is my problem:
In my apartment I have very simple local network. My computer is connected to the Internet, and second PC is connected to my computer. My provider does not allow to share connection. In Widnows XP I have installed some proxy application and that is why my second unit can connect to the Internet. What I need.. is proxy application for my fresh Ubuntu.

---

### Post by kvidell on 2005-05-05
[QUOTE=wporzo]First of all.. it's my first post in this huge community. This is good moment to say Hello! :)

.. and this is my problem:
In my apartment I have very simple local network. My computer is connected to the Internet, and second PC is connected to my computer. My provider does not allow to share connection. In Widnows XP I have installed some proxy application and that is why my second unit can connect to the Internet. What I need.. is proxy application for my fresh Ubuntu.[/QUOTE]
 Check out "corkscrew" (apt-cache show corkscrew)

---

### Post by Gallows on 2005-05-05
[QUOTE=kvidell]Check out "corkscrew" (apt-cache show corkscrew)[/QUOTE]

Have a look at tinyproxy 

To quote:

..."which is very light on system resources, ideal for smaller networks and similar situations where other proxies (such as Squid) may be overkill"...

Or have a look at Squid  - apt-cache show squid - [http://www.squid-cache.org/](http://www.squid-cache.org/)
A bit heavy handed perhaps but pretty cool.

---

### Post by Takis on 2005-05-05
Why don't you put a firewall between your desktop computers and the Internet? [Smoothwall](http://www.smoothwall.org/) firewalls have DHCP and proxy inbuilt (and are free).

---

