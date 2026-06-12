---
title: "Print only one line of a file / output."
date: 2012-10-27
forum: General Help
---

### Post by Gotti on 2012-10-27
I need to do what the title states.

For example, entering 

```
nmap -sP 192.168.1.0/24 | grep 'Nmap scan report'
```

returns

```
Nmap scan report for 192.168.1.1
Nmap scan report for 192.168.1.8
Nmap scan report for 192.168.1.4
```

How can I get it to only output say...line 2? I assume some sort of awk line?

---

### Post by Vaphell on 2012-10-27
```
... | awk 'NR==2'
```
or
```
... | sed -n 2p
```

---

