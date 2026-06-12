---
title: "unable to resolve *some* hosts in web browser"
date: 2014-09-15
forum: General Help
---

### Post by Vlad_Anghene on 2014-09-15
Hello,
I'm relatively new to Ubuntu and I'm running the latest :
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

I ran into some issues with the firefox browser (and also Chrome and Lynx for that matter).
Sometimes, Ubuntu can't resolve hosts (like youtube.com and such).
It's not a firewall thing since I haven't configured any filters (and upon restart of OS, it's kinda fixed until it isn't anymore).
I tried looking at resolvconf logs but they are empty.
Pinging said hosts works perfectly there's a 0 drop.

Anyone experienced this before ? 
Anything else works okay (except in some instances where CSS fails to load and icons are missing in my gmail).

Any help would be greatly appreciated.
Thanks

---

### Post by Vlad_Anghene on 2014-09-16
bump

---

### Post by matt_symes on 2014-09-16
Hi

Is this a DNS resolver issue ?

When you cannot resolve a host,  can you do it from the command line ?

```
nslookup www.youtube.com
```

Do you still have the same issue if you use a specific DNS server (say Google or OpenDNS ) ?

Google ...

```
nslookup www.youtube.com 8.8.8.8
```

OpenDNS

```
nslookup www.youtube.com 208.67.222.222
```

What happens if you restart the network manager service ?

```
sudo service network-manager restart
```

If restarting network manager if too drastic, you could send a SIGHUP to dnsmasq and then try.

```
sudo kill -SIGHUP $(pgrep dnsmasq)
```

Have you made any any changes to resolv.conf or dclient.conf (they should be overwriten anyway but....) ?

```
cat /etc/resolv.conf
```

```
cat /etc/dhcp/dhclient.conf
```

Are you behind any kind of proxy ?

That's the steps i would start using to debug this.

Kind regards

---

### Post by Vlad_Anghene on 2014-09-17
Hello mat, thanks for your advice. I will look into it, I restarted the network-manager service and it still doesn't work (youtube in this case)


I'm behind some sort of proxy in the dormitory of a student hall. Don't know about what's going on, the sys admin keeps messing with the confs every day and he doesn't look like he knows what he's doing.

---

### Post by matt_symes on 2014-09-17
Hi

> **Vlad_Anghene said:**
> I'm behind some sort of proxy in the dormitory of a student hall. Don't know about what's going on, the sys admin keeps messing with the confs every day and he doesn't look like he knows what he's doing.

Hmmm. I would investigate this to start with :)

Kind regards

---

