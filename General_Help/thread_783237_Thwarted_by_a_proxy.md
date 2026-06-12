---
title: "Thwarted by a proxy"
date: 2008-05-05
forum: General Help
---

### Post by HaDAk on 2008-05-05
I'm setting up an 8.04 server at work, and I'm unable to do an apt-get update.  Upon researching the error code thrown, I've discovered that I need to go through my proxy.  Unfortunately, I do not have access to the proxy (however, I do know it's FQDN - I'm just unable to resolve it.).  I also know that any machine dropped on the network gets an IP address, and is allowed to go to a certain subset of websites, until they authenticate properly using IdentD.  I can't install IdentD because I can't update my sources list.  I feel like I'm running in circles here, and I know there has to be an easier way.  Please help!

---

### Post by Monicker on 2008-05-05
Request to have access through the proxy for reaching the Ubuntu servers.

---

### Post by HaDAk on 2008-05-05
Unfortunately, that's not an option.  I'm *the* IT guy here, and since I've only been here about two months, they're not giving me access to anything.  Any questions I ask go unanswered.  So, I have to devise a workaround in the meanwhile.

---

### Post by Monicker on 2008-05-05
You are the only IT guy, yet you have no access to configure the proxy???

Interesting.

---

### Post by HaDAk on 2008-05-05
I know, right?

So, my laptop, for example, has internet access out of the box.  Only once I authenticate myself using IdentD do I get the "full package" (that is, unrestricted access).

How do I trick the proxy into letting me have access, even limited, so I can apt-get install an identd package?

---

### Post by Monicker on 2008-05-05
> **HaDAk said:**
> I know, right?

So, my laptop, for example, has internet access out of the box.  Only once I authenticate myself using IdentD do I get the "full package" (that is, unrestricted access).

How do I trick the proxy into letting me have access, even limited, so I can apt-get install an identd package?

I'm sorry, I can't assist you with bypassing proxies or circumventing access controls.  If you have a legitimate need for access, then you should take it up with the people who have the ability to grant it.

---

### Post by HaDAk on 2008-05-05
Back to chasing my tail...
Thanks anyway.

---

### Post by Envirotech on 2008-05-05
try googling for the deb package. and download it from somewhere else

---

### Post by HaDAk on 2008-05-05
Hrm. Why didn't I think of that? Anyway, I've got pidentd up and running...just trying to figure out how to change what it reports itself as.

---

