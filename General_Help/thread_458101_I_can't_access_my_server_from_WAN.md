---
title: "I can't access my server from WAN"
date: 2007-05-29
forum: General Help
---

### Post by cje on 2007-05-29
I need some help to access my server from outside my LAN. 
I have an ubuntu server at my LAN, behind a Netgear WPN824 router.
The server is accessible inside LAN.

I've forwarded all Http/ftp traffic on port 80 and 20-21 to the server. I've even set the DMZ to the local server address.
I get response when pinging the router from WAN
I've tried setting NAT filtering to open.

Anyone who knows what I do wrong?

Thanks for any suggestions.

---

### Post by blazercist on 2007-05-29
most isp's block traffic on port 80 unless you have the business package, that would probably explain why your server is not accessible on that port, perhaps your provider blocks port 21 too?

---

### Post by cje on 2007-06-22
thanks blazercist
I got the same answer from my ISP ....

---

### Post by cje on 2007-07-05
Ok, I'm on again with a new ISP supplier ;-)

Just one more question before I go too deep into the router configuration; are there any configurations which are necessary to make the Ubuntuserver accessible from WAN? Or is it just "plug and play"

Thanks for any advice.

---

### Post by switchOv3rload on 2007-07-05
Make sure you are running DNS if you have a name configured for your website, otherwise just typing in the WAN IP provided that you have port forwarded to your local ip should work!

---

### Post by cje on 2007-07-06
thanks for the reply switchOv3rload
I'm using the ISP WAN DNS not the local router DNS (if any ...?) - is it correct?
Is it better to remove the name of the server for testing the WAN access?
(I've configured the router to route the http/ftp traffic to the server ip)

---

