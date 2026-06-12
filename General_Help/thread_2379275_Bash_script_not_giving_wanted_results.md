---
title: "Bash script not giving wanted results"
date: 2017-12-03
forum: General Help
---

### Post by lsutiger on 2017-12-03
I have the following script running in rc.local
```
#!/bin/bash
URL_LIST=("smtp.isp.net" "someplace.com" "otherplace.net")
GATEWAY="192.168.1.1"
 
IP_LIST=()
 
for url in $URL_LIST
  do
    ip=`dig +short $url`
    IP_LIST+=("$ip")
  done
  
for ips in $IP_LIST
  do
    ips=(`echo $ips | tr " " "\n"`)
    for ip in $ips
      do
        ip route add $ip via $GATEWAY
      done
  done
```
It is successfully adding the new route for the first item in the URL_LIST, but not the others. What am I missing here?

---

### Post by Holger_Gehrke on 2017-12-03
Why use an array where a simple string will suffice ? Why loop twice, when you can do it in one pass ?
```

#!/bin/bash
URL_LIST="smtp.isp.net someplace.com otherplace.net"
GATEWAY="192.168.1.1"
 
for url in $URL_LIST
  do
    ip=`dig +short $url`
    echo ip route add $ip via $GATEWAY
  done

```

The 'echo' in line 8 can be removed once you're sure that the script creates the right commands.

And while you may have meant the URLs as dummies, they do all exist. And the first one shows a potential problem: 'dig +short' does not always produce just an IP-address as output. If the name is an alias, dig will output the real name and the ip.

Holger

---

### Post by lsutiger on 2017-12-04
Thank you

---

### Post by Hadaka on 2017-12-04
Hi, this would work to replace your .. dig command

```
ip=`[COLOR=#000000]ping -c1 google.com | awk '/PING/{print $3}'| tr -d '()'`
[/COLOR]#    ~or~
[COLOR=#000000]ip=`ping -c1 "$url" | awk '/PING/{print $3}'| tr -d '()'`[/COLOR]
```
Hope that is useful to you.

---

### Post by lsutiger on 2017-12-04
Thank you

---

