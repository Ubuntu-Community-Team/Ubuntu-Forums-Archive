---
title: "Evolution Exchange support broken?"
date: 2004-10-15
forum: General Help
---

### Post by tophfisher on 2004-10-15
Hi All,

Quick question I hope. I am using my new ubuntu system at work and we use Exchange 2000, so I wanted to use Evolution to connect to my exchange server, and I have done this before with other distros... But now on my new ubuntu system i get an error:

```
 Evolution is unable to open exchange backend&#58; No such file or directory.
```

I have re-installed the connector using Synaptic but no luck, and one here have a tip?

---

### Post by chard on 2004-10-27
Had the same issues myself. 
I solved it by removing the leading / in the OWA path.
Changed "/exchange" to "exchange" and entering my windows name without the @<domain> portion. 

Also, it should be noted that the full path is the combination of your exchange name the OWA path entry.  

This also helped with the "Could not find Exchange Web Storage System" error.

---

### Post by ulrich on 2004-10-28
hi,
strangely enough evolution works for me with the 'old' settings ('/exchange' :))
but has someone got 'public folders' working?
for example: i click on the left the 'exchange' button
and then i get a tree of all the folders but... thats all.
see shot [ here ](http://delphi.moltomedia.de/ulrich/shot2.png)
is there anything im missing?

thanks

ulrich

---

