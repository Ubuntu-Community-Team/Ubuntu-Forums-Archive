---
title: "Headless system 'randomly' becoming unresponsive"
date: 2008-03-15
forum: General Help
---

### Post by KrisWillis on 2008-03-15
I have an install of 7.04 running on a headless machine that is used as a media server. Every couple of days, sometimes weeks, the machine becomes unresponsive - Its mt-daapd share disappears from all of my clients that access it, web requests time out (running Apache2), attempts to connect over SSH time out and I cannot access any SAMBA shares.

The only way to regain access is to hit the reset button and wait for it to boot. It is very inconvenient for me to hook up a monitor to it, but is there any logs I can check after rebooting that might give some insight as to what is causing this?

Many thanks.

---

### Post by lafflam on 2008-03-16
On the headless machine, is the network interface using a static IP or DHCP?

```
sudo cat /etc/network/interfaces
```

---

### Post by KrisWillis on 2008-03-17
DHCP, but after rebooting, it keeps the same IP it has always had.

---

### Post by lafflam on 2008-03-17
Hmmm...so I assume you are using a router with Static DHCP to assign the same IP to the system based on MAC address?

My reason for this line of questioning is this:

I had my home server set up to get its IP via DHCP, and my router set up to assign the same IP based on MAC address (i.e., static DHCP...the simplicity of DHCP with the benefits of static IP).

Then I assigned a real static IP address to the server in /etc/network/interfaces, but didn't change my router setup. The server would be accessible for a while, but then (apparently randomly) become unresponsive. I couldn't ping the server from any system on the network. However, if I logged into the server locally, I could ping the router and other systems from the server, and then I would be able to ping the server from other systems on the network. 

It was like I woke the server up or something.

I'm sure I could have made whatever adjustments I need to the router and server so that I could use a static IP, but decided I like the simplicity of static DHCP instead.

Does anything like this apply to your situation?

If not, we may need more info about your setup (/etc/hosts, /etc/network/interfaces, perhaps some info about the router setup)

---

### Post by lafflam on 2008-03-17
Also, keep an eye on this thread:

[http://ubuntuforums.org/showthread.php?t=720891](http://ubuntuforums.org/showthread.php?t=720891)

Seems like similar problem.

---

### Post by fsmithred on 2008-03-18
If the server is completely  locked up (i.e. there's a keyboard on the server, and you can't log in and shut it down) then it may be a hardware problem.  A bad power supply could ruin other things, so it's a good one to rule out early. Give your server some head and run memtest, too.

---

