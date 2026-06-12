---
title: "How can I disable rygel (MediaServer) startup at boot?"
date: 2015-09-11
forum: General Help
---

### Post by chrisasl92 on 2015-09-11
Hello, 

I've rygel installed and I want to disable starting at boot.  
I looked at the rygel configuration file and haven't found anything related to startup.  

I also tried checking if it's a service started by init with ```
[FONT=Consolas]initctl list[/FONT]
``` and ```
[FONT=Consolas]ls /etc/init.d/
[/FONT]
``` but the resulting list, didn't contain rygel.

How can I achieve this?

---

