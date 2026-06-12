---
title: "What command do you run in the terminal of ubuntu to find info about your ip address?"
date: 2008-06-27
forum: General Help
---

### Post by Brii on 2008-06-27
I need to find out what dns server im on the fix the inter net on my windows partition

    
Additional Details

im using linux not vista when i do ipconfig in vista it doesnt give me a dns server ip because the internet is not working on vista only working on ubuntu

so in ubuntu i have to figure out the server and put that number into to windows configuration because vista is to stupid to figure it out by itself

---

### Post by sean_fitz on 2008-06-27
```
cat /etc/resolv.conf
```

The output from this command should have a line that says:
"nameserver 192.168.10.1"

Where the IP address given is that of your DNS server.

---

### Post by Titan8990 on 2008-06-27
ifconfig is the Linux exuivelent of ipconfig. Nslookup is a multi-platform tool.

---

