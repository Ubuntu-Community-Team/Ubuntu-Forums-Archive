---
title: "Accessing WiFi thought a a simple webserver?"
date: 2023-08-05
forum: General Help
---

### Post by josephchrzempiec on 2023-08-05
Hello, I’m working on a Ubuntu server that is in a small portable desktop computer I can take around. I normally have to type in some commands to type in the WiFi Ssid and password. I’m trying to find an easier way I can just select the ssid and just put in the password to be able to access internet. 

I looked online but I can not manage to anything like this. Only thing I found was to what. I’m currently doing putting in it manually though terminal.  Do anyone know a way for say a simple python webserver page that I can do this?

joseph

---

### Post by TheFu on 2023-08-05
Why not just setup network manager to connect at boot to the network?  Don't have the networking connected to any user.

BTW, servers really should use wired ethernet.  I doubt you'll listen, but when things don't work so well, I think you'll find a better solution, perhaps powerline or MoCA networking, instead, if ethernet cables can't be run where you need it.

Seems a website that used to cover these things has disappeared, so I can't provide a link.  I have powerline connecting different floors of my home, but if I upgrade it or didn't have anything, I'd switch to 2.5Gbps MoCA networking, which is faster and not dependent on the breaker box.  Powerline is pretty fast, but in my testing here, drastically changes based on location.  I have a 600Mbps powerline setup.  That's the theoretical max.  Within the same room, different power outlets, I saw about 220 Mbps.  Between two floors on opposite sides of the house, I'm seeing 62 Mbps.  Huge different.  Powerline and MoCA networks are stable, so completely unlike wifi.  The bandwidth doesn't fluctuate with either, though I see wifi fluctuating between 300 Mbps and 12 Mbps. I have no control over wifi performance. It is dependent on outside factors causing interference.  Plus, wifi isn't very secure. We learned that a few years ago when 20+ yr old security faults were found in all current wifi protocols.  Avoid wifi.

---

### Post by josephchrzempiec on 2023-08-05
The problem is I don&#8217;t know where I&#8217;m going half the time. And 99% of the time there is no Ethernet. And I can&#8217;t connect to a moca connection becuase it&#8217;s someone network. I can&#8217;t do powerline because I might be on a beach or in the middle of the woods but there is always a WiFi connection no matter where I go.

---

### Post by dragonfly41 on 2023-08-05
This is what I use for quick testing on localhost. 

[https://www.php.net/manual/en/features.commandline.webserver.php](https://www.php.net/manual/en/features.commandline.webserver.php)
 on local server.

But note to restart PHP server you need to kill port 8000  to kill running process.

I use zenmap to check which ports are running.

---

### Post by josephchrzempiec on 2023-08-05
The problem I&#8217;m facing is that I need to connect my wireless through a local webserver page on the same system. So that way I can access the internet. If I can do that through a small python server page I will be okay.

---

### Post by TheFu on 2023-08-06
> **josephchrzempiec said:**
> The problem I’m facing is that I need to connect my wireless through a local webserver page on the same system. So that way I can access the internet. If I can do that through a small python server page I will be okay.

I'm confused.   Uh ... why not just have the wifi connect at boot, not at login?  Allowing a local web server to do this is adding complexity that isn't needed and dropping security, since few people can create a secure webapp.

You can script this with nmcli, if you like. [https://ubuntu.com/core/docs/networkmanager/configure-wifi-connections](https://ubuntu.com/core/docs/networkmanager/configure-wifi-connections)
or
[https://askubuntu.com/questions/16376/connect-to-network-before-user-login](https://askubuntu.com/questions/16376/connect-to-network-before-user-login)

---

### Post by josephchrzempiec on 2023-08-08
True. However I don't know the wifi ssid or password ahead of time until I get there. I travel to a lot of places. I'm on the road a lot now and I take this syatem with me.

---

### Post by TheFu on 2023-08-08
> **josephchrzempiec said:**
> True. However I don't know the wifi ssid or password ahead of time until I get there. I travel to a lot of places. I'm on the road a lot now and I take this syatem with me.

Ah ... I get it.  I use **wicd-cli**, which has a TUI, for that on a laptop. I'd be surprised if NM didn't have a GUI, TUI and CLI interface.  Using a webserver for something like this means the web server process will need root access - that's a security nightmare to be avoided.  Heck, I'd probably check out **Cockpit** if I were really set on using a webserver for something like this.  [https://cockpit-project.org/](https://cockpit-project.org/)  I think it is in the Canonical repos.

---

