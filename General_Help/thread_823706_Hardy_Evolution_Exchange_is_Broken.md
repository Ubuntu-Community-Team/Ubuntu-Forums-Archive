---
title: "Hardy Evolution Exchange is Broken"
date: 2008-06-09
forum: General Help
---

### Post by jaferguson2 on 2008-06-09
Hello All,

    I recently installed Hardy as an upgrade from using Fedora Core 8 as my Linux platform. I love the platform so far except for one huge issue. I have to use the Evolution Exchange connector, and it appears to be non-functional. If I open Evolution and enter my OWA user ID and URL ([https://email.xxxxx.com/exchange](https://email.xxxxx.com/exchange)) and hit authenticate I get the following error without fail; "Unable to connect to server" , "Error in URL"?. I know the URL works because I can be logged into the OWA at the same time I am trying to configure Evo.

I have tried uninstalling all the evolution packages and dependencies and reloading it all with the same error I am running evolution 2.22.2. I hope that I can get some assistance with this, I am hoping if there is not a simple fix that Canonical can get a patch released ASAP or it might be back to Fedora 9. Any thoughts or posts that I have missed.

---

### Post by moore.bryan on 2008-06-09
i haven't had this issue lately, but i found the best way around it was to compile from cvs following [this]("http://www.go-evolution.org/Compiling_Evolution_from_CVS") walk-through.

---

### Post by jaferguson2 on 2008-06-09
I did find this bug that was filed.
[https://bugs.launchpad.net/ubuntu/+source/evolution-exchange/+bug/209438](https://bugs.launchpad.net/ubuntu/+source/evolution-exchange/+bug/209438)

---

### Post by ilrudie on 2008-06-09
Use /usr/bin/exchange-connector-setup-2.22 to setup evolution/exchange.  I had problems connecting to OWA using evolutions configuration GUI.  This one worked for me though.  It has some quirks but nothing too weird that I recall.  Hope that helps.

---

### Post by jaferguson2 on 2008-06-11
So since I started this thread I should wrap it up. I have found the culprit and I am will throw out the information for any others who may find it helpful. 

The initial URL that I was using was actually a Virtual IP (VIP) on a load balancing module that was doing SSL offload. This is an older SSL accelerator and could not handle the new TLS encryption that was used in the new releases of Evolution. This must have been changed after the Evolution security advisory that was released. That would explain why large numbers of users whose Evolution was upgraded just stopped connecting. The workaround in my case was to point evolution to the HTTP socket of the Real Server address not the VIP. Hope this might help someone else in the future.

---

### Post by chrisl1977 on 2008-08-29
I spent almost two days struggling with getting Exchange OWA over SSL to work in Evolution.  I tried using /usr/bin/exchange-connector-setup-2.22 from the terminal and viola!  IT WORKS!!!  Thanks! - Chris

	:guitar:

---

### Post by lesbianpenguin on 2008-09-02
well i tried /usr/bin/exchange-connector-setup-2.22 the same error.................

---

### Post by realstraw on 2008-09-06
Same here... :(

---

