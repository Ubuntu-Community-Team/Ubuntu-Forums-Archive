---
title: "Conky chokes on multiple connections...."
date: 2008-04-08
forum: General Help
---

### Post by Anduu on 2008-04-08
I have conky configured to display incoming and outgoing connections.When there are multiple connections open (while downloading/seeding a torrent for example....) conky seems to stall.It does not crash or anything it just stops refreshing.Once the connections are closed it will resume it's normal operation.

Now I can see it not being able to handle the load from torrent connections however a lot of times it will choke under the load of just a few.Like while simply surfing the web...

Attached is the related code in my .conkyrc for monitoring my network.I am far from an expert and this code is hacked together basically by trial and error and by using snippets from the ginormous "post your .conkyrc ......" thread.

Maybe I went about it all wrong or there is a more streamlined way of coding it.

Any help would be greatly appreciated.

```
${offset 1}${color #D6C6AF}NETWORK: ${color}${addr eth0}
${offset 1}${color #FFECD1} Total Connections: ${color}${tcp_portmon 1 61000 count}

${offset 1}${color #D6C6AF} UpLoad: ${color}${upspeedf eth0}k/s${color}  Total: ${totalup eth0}
${offset 1}     ${upspeedgraph eth0 20,160 420000 ff0000 70}

${offset 1}${color #D6C6AF}Connections: ${color}${tcp_portmon 1 32767 count} ${alignr} Service/Port${color grey}
${tcp_portmon 1 32767 rhost 0} ${alignr} ${tcp_portmon 1 32767 lservice 0}
${tcp_portmon 1 32767 rhost 1} ${alignr} ${tcp_portmon 1 32767 lservice 1}
${tcp_portmon 1 32767 rhost 2} ${alignr} ${tcp_portmon 1 32767 lservice 2}
${tcp_portmon 1 32767 rhost 3} ${alignr} ${tcp_portmon 1 32767 lservice 3}
${tcp_portmon 1 32767 rhost 4} ${alignr} ${tcp_portmon 1 32767 lservice 4}

${offset 1}${color #D6C6AF} DownLoad: ${color}${downspeedf eth0}k/s ${color} Total: ${totaldown eth0}
${offset 1}     ${downspeedgraph eth0 20,160 004200 00ff00 700}

${offset 1}${color #D6C6AF}Connections: ${color}${tcp_portmon 32768 61000 count} ${alignr} Service/Port${color grey}
${tcp_portmon 32768 61000 rhost 0} ${alignr} ${tcp_portmon 32768 61000 rservice 0}
${tcp_portmon 32768 61000 rhost 1} ${alignr} ${tcp_portmon 32768 61000 rservice 1}
${tcp_portmon 32768 61000 rhost 2} ${alignr} ${tcp_portmon 32768 61000 rservice 2}
${tcp_portmon 32768 61000 rhost 3} ${alignr} ${tcp_portmon 32768 61000 rservice 3}
${tcp_portmon 32768 61000 rhost 4} ${alignr} ${tcp_portmon 32768 61000 rservice 4}
```

---

### Post by Anduu on 2008-04-22
One bump for good measure ;)

---

