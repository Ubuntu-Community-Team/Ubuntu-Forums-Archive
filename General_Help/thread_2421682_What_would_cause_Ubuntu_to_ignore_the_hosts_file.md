---
title: "What would cause Ubuntu to ignore the hosts file?"
date: 2019-06-25
forum: General Help
---

### Post by jonh001 on 2019-06-25
I'm running 18.04.  I have an entry in the hosts file (E.g. reg.stratus.local) pointing to a private IP address (which is reachable when my VPN is up).
When I'm using a web app I cannot connect to the host using the FQDN.  The error out was so quick it made me suspicious so I ran a tcpdump to see what was going on.
The request doesn't even make it to the host.  It all dies with DNS resolution.  For some reason Ubuntu is trying to use Google (i.e. 8.8.8.8 and 8.8.4.4) to resolve it even when there is an entry in the hosts file.   Using the IP address works as far as reachability is concerned, but there are some TLS errors wrt to IP and not FQDN....not relevant here.

I checked /etc/nsswitch.conf and under hosts, "files" is the first entry which I believe means check the hosts file first.
I also thought the .local may be causing an issue so I disabled the avahi daemon.

My /etc/resolve.conf file shows the nameserver picked up by systemd-resolved when the VPN fires up (my FDQN is for testing so it's not resolvable).
Without the VPN resolv.conf shows my router as the DNS and the router uses Cloudflare (1.1.1.1).

So not sure **why the hosts file is being ignored** and why Google DNS is used even through it's not configured anywhere (although I read somewhere that it's a hardcoded default within systemd-resolved, although not sure if that's true).

Any ideas?

---

### Post by TheFu on 2019-06-26
Which browser?   
Try a different browser.  I don't use Chrome, so don't know if that is the issue.

I know that newer versions of Android ignore the hosts files as a security precaution.

---

### Post by jonh001 on 2019-06-26
Both Firefox and Chromium behave the same.  But you raise a great point related to the browser.
The browser is the issue as CLI commands (E.g. curl and wget) work fine.
Thanks for the help.

---

### Post by SeijiSensei on 2019-06-26
Did you add the entry to /etc/hosts on both the server and the client?

---

