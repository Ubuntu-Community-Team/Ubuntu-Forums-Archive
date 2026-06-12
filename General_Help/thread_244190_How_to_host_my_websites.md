---
title: "How to host my websites???"
date: 2006-08-26
forum: General Help
---

### Post by craigsharp on 2006-08-26
First and foremost, i'm almost a complete newbie to linux.  I played around with SuSE for a while, but didn't really care for it. So now i'm here,  I just installed ubuntu server and installed gnome because i dont know any coding or whatever it's called,  but i do want to host my own websites.  I have a total of 5 domain names that i'm having hosted and i want to save the money.  

The proble is, I dont know where to start.  Well, i guess i do or else i wouldnt have already installed ubuntu.  But any help would be very much appreciated.  From all the other threads i've read, i know this is a very helpful community of linux users who can help me out.

Thanks

---

### Post by ifokkema on 2006-08-26
Well, you'll need a webserver. Say, Apache 2. Go to System -> Administration -> Synaptic Package Manager. Search for Apache2 and install it. Then... I guess reading up on Apache 2 would be the next thing to do. See httpd.apache.org.

Good luck!

---

### Post by scratched on 2006-08-26
You also will need to look into getting a static IP address. It is most likely against your ISP's TOS to host your own website unless you pay extra for the service. You would need business class DSL or some other service that gives you a dedicated static IP address.

Like ifokkema said, you'll need apache2. There is a [great tutorial over on easylinux.info]("http://easylinux.info/wiki/Ubuntu#Apache_HTTP_Server") that explains step-by-step how to set up an apache server (along with configuring it) on Ubuntu linux.

---

### Post by az on 2006-08-26
Even better, this is Ubuntu specific:
[https://help.ubuntu.com/community/WebServerHosting](https://help.ubuntu.com/community/WebServerHosting)

---

