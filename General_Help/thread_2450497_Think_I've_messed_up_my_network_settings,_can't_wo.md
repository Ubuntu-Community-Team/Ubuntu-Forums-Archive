---
title: "Think I've messed up my network settings, can't work out exactly what!"
date: 2020-09-15
forum: General Help
---

### Post by cable_guy on 2020-09-15
Hi all,

My Ubuntu 20 server is acting strangely, loads of strange console messages, so I took the time to try troubleshoot today.

Apt-get update moaned about name resolution so I learnt about this new ip command taking over from ifconfig, but I can't work out how to check my server's nic's DNS servers. 

When I run systemd-resolve --status I get "failed to get global data: failed to activate service "org.freesesktop.resolve1".

I have no idea what this means, the only clue I've got is that I THINK I attempted at some point to change the DNS servers to my local "pi hole" server.

Can any one advise any next troubleshooting steps please?

---

### Post by dragonfly41 on 2020-09-15
I found an interesting package in repo named **lynis** which runs multiple audit tests including name services.
This might offer some clues.

---

### Post by TheFu on 2020-09-15
Where name resolution looks on all Unix systems is controlled by the /etc/resolv.conf file. A few different tools may be screwing around with that file.  If you have a pi-hole on the LAN, you don't need those other tools. They can be disabled.  Just point the /etc/resolv.conf entries at the static IP address for the pi-hole.  Here's mine:
$ more /etc/resolv.conf 
```
nameserver 172.22.22.80
nameserver 172.22.22.81
```
The /etc/resolv.conf file could be a symbolic link somewhere else.  That isn't needed or desired if you have a LAN DNS available, like the pi-hole.
I run 2 pi-hole servers, primary and fallback.
172.22.22.80 is the primary.
172.22.22.81 is the fallback, it runs on a different system, because without any DNS, then the internet seems down, but it is just the name resolution, not the internet.  You can put any DNS server into the file.  1.1.1.1, 1.0.0.1, 8.8.8.8, 8.4.4.8 are well-known DNS from Cloudflare and Google.

So, if you leave systemd.resolved running and enabled, it will screw up the /etc/resolv.conf file all the time.  Stop it, disable it, and "mask" it so it doesn't get used anymore. If necessary, you can "unmask" it, enable it, and start it later.  

Resolvconf is another tool that will try to manage the /etc/resolv.conf. We only want 1 tool doing this, so if you have both installed, it is best to remove/purge one.  These tools were supposed to make stuff better and for most people running 1 computer on their home network, they do. For people with multiple computers, a local DNS server that caches like a pi-hole does, is better for the LAN in many situations.

These are big changes. Think about it it.  But you've already got the pi-hole, so if that isn't being fully used (and maintained), then the effort setting it up wasn't really useful.

So, the 1st two steps are:
to see the permissions and links -  **ls -al /etc/resolv.conf**
and to show the contents of that file.

---

