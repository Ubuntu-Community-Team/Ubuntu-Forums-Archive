---
title: "DNS resolve not working"
date: 2020-03-29
forum: General Help
---

### Post by masenius on 2020-03-29
I installed pihole in docker as an experiment and since port 53 was in use by systemd-resolved I stopped the service and removed the symlink for /etc/resolve.conf. After experimenting I restored the symlink and started the service again but I cannot get any dns lookup to work.

Just running dig without specifying the nameserver doesn't work:
```

$ dig google.com

; <<>> DiG 9.11.5-P4-5.1ubuntu2.1-Ubuntu <<>> google.com
;; global options: +cmd
;; connection timed out; no servers could be reached

```

But explicitly specifying the nameserver works:
```

$ dig google.com @127.0.0.53

; <<>> DiG 9.11.5-P4-5.1ubuntu2.1-Ubuntu <<>> google.com @127.0.0.53
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 4393
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;google.com.                    IN      A

;; ANSWER SECTION:
google.com.             7       IN      A       172.217.20.46

;; Query time: 3 msec
;; SERVER: 127.0.0.53#53(127.0.0.53)
;; WHEN: Sun Mar 29 08:20:03 UTC 2020
;; MSG SIZE  rcvd: 55

```

resolve.conf is holding the correct nameserver and linked to the correct file:
```

$ cat /etc/resolve.conf

# This file is managed by man:systemd-resolved(8). Do not edit.
#
# This is a dynamic resolv.conf file for connecting local clients to the
# internal DNS stub resolver of systemd-resolved. This file lists all
# configured search domains.
#
# Run "resolvectl status" to see details about the uplink DNS servers
# currently in use.
#
# Third party programs must not access this file directly, but only through the
# symlink at /etc/resolv.conf. To manage man:resolv.conf(5) in a different way,
# replace this symlink by a static file or a different symlink.
#
# See man:systemd-resolved.service(8) for details about the supported modes of
# operation for /etc/resolv.conf.

nameserver 127.0.0.53
options edns0
search lan

```

```

$ ls -l /etc/resolve.conf

/etc/resolve.conf -> ../run/systemd/resolve/stub-resolv.conf

```


The correct nameserver is used by systemd-resolve:
```

$ resolvectl status

Link 2 (enp3s0)
      Current Scopes: DNS
DefaultRoute setting: yes
       LLMNR setting: yes
MulticastDNS setting: no
  DNSOverTLS setting: no
      DNSSEC setting: no
    DNSSEC supported: no
  Current DNS Server: 192.168.10.1
         DNS Servers: 192.168.10.1
                      fe80::1213:31ff:fe6c:7882
          DNS Domain: lan

```

Even if I hardcode nameserver in /etc/resolve.conf it still isn't picked up by dig.

If dig, nslookup and all other tools are not using /etc/resolve.conf, what are they using? Am I missing any overriding configuration?

---

### Post by TheFu on 2020-03-29
/etc/resolve.conf is the wrong name for the file.
/etc/resolv.conf is the correct name.

i can't comment about anything else, but i seriously doubt 127.0.0.53 is the correct ip for your docker container that has port 53/udp open for the rest of the subnet. No other machine will be able to access that ip.

---

### Post by masenius on 2020-03-29
Your're kidding me, wrong name of the file, and here I'm sitting reading pihole souce code. Thank you, saved my day!

---

