---
title: "Tomcat with 2 network interfaces"
date: 2014-08-07
forum: General Help
---

### Post by Billett05 on 2014-08-07
Hi,

I'm currently running Ubuntu server 14.04 with a single tomcat instance. I want to be able to run 2 seperate Nics but when doing so I lose access to my tomcat instance on my external URL.  Is there a way that I can restrict one of my interfaces to only work on 2 specific ports (ssh and SFTP) so that I can manage the server internally but not disrupt access to the site?

Regards

Chris

---

### Post by cj13579 on 2014-08-07
You will want to bind it to a particular IP address. To do that, edit *tomcat/conf/server.xml* and add some connector information:

```
<Connector 
    port="8080" 
    protocol="HTTP/1.1" 
    address="127.0.0.1"
    connectionTimeout="20000" 
    redirectPort="8443" 
  />
```

---

### Post by Billett05 on 2014-08-07
I've tried this method and it didn't work. I set the address to the IP of my eth0, it then stopped it from being accessible on the LAN and on my URL.

So that I can give a fuller picture I will try and describe my setup a little more.

1. I have a BT business line with a URL registered to its external IP. This is then set to port forward 8080 to my eth0 IP
2. My eth1 is set to my local network IP of 192.168.x.x with runs on a different network to the eth0 network.

---

### Post by Billett05 on 2014-08-07
Ok, slight change, it works locally connecting using my eth0 IP but when I use my URL which port forwards to doesn't work. Do I need to set this to the external IP address?

---

