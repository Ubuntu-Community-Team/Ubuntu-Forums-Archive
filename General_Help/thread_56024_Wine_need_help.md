---
title: "Wine need help"
date: 2005-08-11
forum: General Help
---

### Post by arlie on 2005-08-11
Everytime I do this "sudo apt-get install wine" I get this message:

Err [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ wine 0.0.20050725-winehq-1
  Error reading from server. Remote end closed connection
Failed to fetch [http://wine.sourceforge.net/Ubuntu/apt/binary/wine_0.0.20050725-winehq-1_i386.deb](http://wine.sourceforge.net/Ubuntu/apt/binary/wine_0.0.20050725-winehq-1_i386.deb)  Error reading from server. Remote end closed connection
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


What's missing? Please help I'm new to linux.

---

### Post by Caboose on 2005-08-11
> maybe run apt-get update or try with --fix-missing

if that doesn't work, download that file and 'sudo dpkg -i wine_0.0.20050725-winehq-1_i386.deb'

---

### Post by arlie on 2005-08-12
[QUOTE=Caboose]if that doesn't work, download that file and 'sudo dpkg -i wine_0.0.20050725-winehq-1_i386.deb'[/QUOTE]
 Thanks.

---

### Post by markulf on 2005-08-25
to me it seemed as if both apt-get and firefox stopped downloading the file due to heavy load and timeouts, in the end i succeeded with wget

---

### Post by wadesmart on 2005-08-26
08262005 1500 GMT-5

I had the same problem and just installed it though Synaptic. 

I have another problem though. 

I kinda got things working but, how can you get IE to download and install? I downloaded AvantBrowser but nothing happens. I tried IE but only the installer downloads and apparently it cant reconnect to the net?

Wade

---

