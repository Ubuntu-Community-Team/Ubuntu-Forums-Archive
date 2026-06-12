---
title: "How do I better understand DNS(dnsmasq) in Ubuntu 16.04?"
date: 2018-07-22
forum: General Help
---

### Post by thesearch on 2018-07-22
[SIZE=2]I was having a DNS resolution issue which lead me on a  search to change what I thought would be a simple DNS setting, but it  seems there are many layers to DNS in the default Ubuntu 16.04  configuration.[/SIZE]

[SIZE=5]
[U]The problem
[/U]
[SIZE=2]I connected to a public network and for some reason I  could not resolve host names for a specified domain, but I could ping  the address directly, so I know that everything was online. Dig returned  no answer section, the server defined as being used for the query was  127.0.1.1. I tried running the query directly against google's DNS  server and it returned the proper address in the answer section. So, I  assumed something must be wrong with the DNS settings on the network  router.
[/SIZE][/SIZE][HR][/HR][SIZE=5][SIZE=2]

[SIZE=4]Didn't work[/SIZE]
```
dig example.com
``` 
[/SIZE][/SIZE][HR][/HR][SIZE=5][SIZE=2]

[SIZE=4]Did work[/SIZE]
```
dig @8.8.8.8 example.com
```
[/SIZE][/SIZE][HR][/HR]

With the help and direction if some people in the #dns IRC channel I ran

```
netstat -nulp
```

and found that the process handling 127.0.1.1:53 is dnsmasq.[SIZE=5]


_Problem resolution_
[LIST]
[*][SIZE=2]/etc/resolve.conf could be edited and works temporarily, but gets overwritten when changing networks - and the file tells you that it will be overwritten.
[/SIZE] 
[*][SIZE=2]/etc/resolvconf/resolv.conf.d/tail can be created and 'nameserver 8.8.8.8' can be added, but this is appended underneath 'nameserver 127.0.1.1' which is used primarily and the resolution still doesn't work.
[/SIZE] 
[*][SIZE=5][SIZE=2]/etc/resolvconf/resolv.conf.d/head can be modified and 'nameserver 8.8.8.8' which is prepended to 'nameserver 127.0.1.1'; this does resolve the issue as it seems to become the primary server used for resolving domain names. It also seems to hold after a system reboot, but the file does warn not to modify it as it will be overwritten; I am not sure in which circum[/SIZE][/SIZE] 
[*][SIZE=5][SIZE=2]/etc/dhcp/dhclient.conf there is a 'prepend domain-name-servers' directive that can be uncommented/added and appended with 8.8.8.8 this DOES resolve the issue. This seems to be the correct solution and is the one I am currently using.[/SIZE][/SIZE] 
[/LIST]


_What is actually happening?_[SIZE=2]
So, I resolved my issue which is nice, but it also seems there are many layers of how this works in Ubuntu 16.04. I was hoping somebody could break down for me and point me in the right direction to understanding how this all comes together. I believe the dnsmasq process is running as a child process under network-manager, but how is this all loaded? How are all of these different config files pulled in and in which order? Are some of them omitted if a certain variable has already been defined.

I'm hoping to gain some insight to more quickly be able to resolve a similar issue in the future while also having a much better understanding of what is actually going on here.




Thanks so much for your time and thoughts.[/SIZE]

[/SIZE]

---

