---
title: "conky - display my external address"
date: 2017-05-29
forum: General Help
---

### Post by marchello_lippi2 on 2017-05-29
Hi all, 

I got dynamic external IP address and I would like to display it in conky ( I check it using **$ curl ipinfo.io/ip** in console so far). 
How do I perform it?

---

### Post by ajgreeny on 2017-05-29
You need to use the variable ${addr enp4s0} in your .conkyrc or whatever file you use for configuration of the display; here's what I have in mine with the up and down speed-graph boxes which you may find useful as well
```
NETWORK IP: $alignr enp4s0 -  ${addr enp4s0}
DOWN: ${downspeed enp4s0}/s$alignr UP: ${upspeed enp4s0}/s
${color #FFA500}${downspeedgraph enp4s0 40,158}$alignr${upspeedgraph enp4s0 40,158}
```
The screenshot is of the output this gives me.

EDIT:
Sorry; just noticed this is about external IP.

I think your command will do this and you need to run it and extract the output to the conky display with 
```
PUBLIC IP ${alignr}${execi 60 curl  ipinfo.io/ip}
```

---

### Post by marchello_lippi2 on 2017-05-29
**ajgreeny**, does work, thx.

---

