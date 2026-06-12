---
title: "Cannot download torrents anymore"
date: 2007-11-11
forum: General Help
---

### Post by vnetha on 2007-11-11
Hi,

I've been using Gutsy since it came out.
I have all the software i need installed.
and until recently, I was able to download torrents fine.

but suddenly couple of days ago, my torrent software stopped working.
I'm using Deluge. and I get this error under Tracker Status...

"Alert: Connection refused (HTTP code=-1, times in a row=6)"
The torrent perennially says "Connecting...".

can anyone help?

I've tried other kinds of software to see if that changes anything, but no.
Transmission, utorrent thru wine all have the same problem.


Vivek.

---

### Post by Sebastian Stein on 2007-11-11
Maybe your firewall is blocking inbound connections on the torrent ports and so you are not able to download anymore?

Sebastian
--

---

### Post by vnetha on 2007-11-11
That's not it.
I have no firewall installed.
and I have port forwarding enabled on the router\switch.

I've also tested the connection through the active port in Deluge.
It says everything is fine, but still doesn't download.
like i said, it used to work until a couple of days ago.

I haven't changed anything since, except restart my machine.
does anyone think the ISP might be meddling?

I even have encryption enabled.


Vivek.

---

### Post by por100pre1 on 2007-11-11
Just in case:

```
sudo iptables -L
```

post the results. :-k

---

### Post by rye_ on 2007-11-11
EDIT : IGNORE THIS, I'VE JUST SEEN THAT YOU'VE TRIED THIS 

I had this problem too.

My guestimate is that you're connected via a router and it has a built in firewall. This firewall is blocking deluge, i.e. not allowing incoming connections.

Go to your router configuration page, via firefox and select to disable your firewall for a simple and quick solution.

Ryan

---

### Post by vnetha on 2007-11-11
Hi,

I mentioned earlier that I have port forwarding setup.
I would think that that would override my router firewall.
besides, I haven't changed my router settings from when Deluge used to work fine.
anyhow, here's the outputs just for kicks...

```
vivek@vivek-desktop:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```


Vivek.

---

### Post by Athanasius on 2007-11-11
perhaps your internet service provider is blocking your downloads, I have heard that they are doing that now.  Open Deluge, file>preferences>network>and then check "prefer to encrypt entire stream"

---

### Post by vnetha on 2007-11-11
I already have that option checked.
I've tried using random ports and forced encryption too. 
doesn't seem to help. any other ideas?


Vivek.

---

### Post by AnthoMacP on 2007-11-13
> **vnetha said:**
> 
doesn't seem to help. any other ideas?


you from canada? if you're using demonoid trackers it may be blocking you along with the rest of us. I can't seem to download from any demonoid trackers anymore.

---

