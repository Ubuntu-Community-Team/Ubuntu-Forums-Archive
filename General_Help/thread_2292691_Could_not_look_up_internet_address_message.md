---
title: "Could not look up internet address message"
date: 2015-08-30
forum: General Help
---

### Post by Jonners59 on 2015-08-30
I seem to have run in to a little boot up problem on one of my machines.  Getting the following error.

```
Could not look up internet address for mediaserver.
This will prevent Xfce from operating correctly.
It may be possible to correct the problem by adding
mediaserver to the file /etc/hosts on your system.
```

Content of etc/hosts file...  I have added mediaserver as suggested

```
127.0.0.1 localhost
127.0.1.1 mediaserver.JONATHANECHIARA

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
mediaserver
```

Running 15.04 and up to date.

---

### Post by SeijiSensei on 2015-08-30
You need to specify the IP address for mediaserver, not just its name.  Follow the pattern of the entries at the top of the file.  You might start with modifying the entry for 127.0.1.1 to add "mediaserver" as an alias like this:
```
127.0.1.1 mediaserver.JONATHANECHIARA mediaserver
```
or just remove the ".JONATHANECHIARA" part of the name.

---

### Post by Jonners59 on 2015-08-30
> **SeijiSensei said:**
> You need to specify the IP address for mediaserver, not just its name.  Follow the pattern of the entries at the top of the file.  You might start with modifying the entry for 127.0.1.1 to add "mediaserver" as an alias like this:
```
127.0.1.1 mediaserver.JONATHANECHIARA mediaserver
```
or just remove the ".JONATHANECHIARA" part of the name.

Thanks.  I'll try that later...

FYI  The JONATHANECHIARA is the network name....  as per Windows   Is that as you would expect?

---

### Post by SeijiSensei on 2015-08-30
No. Linux uses names like host.example.com. Your method would work if you have a local domain name server that is authoritative for the JONATHANECHIARA domain, but I doubt that's the case.

---

### Post by Jonners59 on 2015-09-01
Sorted...  Thanks :-)

```
127.0.1.1 mediaserver
```

---

