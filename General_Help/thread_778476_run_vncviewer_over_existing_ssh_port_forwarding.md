---
title: "run vncviewer over existing ssh port forwarding"
date: 2008-05-02
forum: General Help
---

### Post by boondocks on 2008-05-02
From my laptop, I am using ssh to remotely login to my linux server:

```
  ssh  Moi@myLinuxServer1   -p 32211   -D 32211  
```

Then in the laptop's Firefox, I specify:
> Manual proxy configuration:
SOCKS Host: localhost    Port: 32211
Now I am using the laptop's Firefox via the ssh proxy of myLinuxServer1.
Its working great!


Now, while this ssh proxy is up and running -
[LIST]
[*]Can I run vncviewer on the same laptop utilizing the same port (32211) forwarded over ssh?
[*]So that I can remotely control myLinuxDesktop1, on the same LAN as myLinuxServer1.
[/LIST]
What would be the commandline syntax for vncviewer ?

---

