---
title: "/etc/hosts - assign domain name for shared IP hosting?"
date: 2014-06-17
forum: General Help
---

### Post by whitee on 2014-06-17
Hi, 

I've been trying to edit /etc/hosts as seen [here]("http://ubuntuforums.org/showthread.php?t=3407") as I need to access a website on a shared IP hosting, how do I do it?

That is, I need to externally access [http://www.someshop.test1/]("http://www.erektionshop24.test1/") at the IP 46.165.253.147 while when I load 46.165.253.147 in my browser it gives me another website. I've got the following setting but it doesn't work. 

```

# cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    mycoolname
46.165.253.147  http://www.someshop.test1/

```

I also cleaned my chrome DNS cache, flushed sockets and restarted the browser, but [http://www.someshop.test1/](http://www.someshop.test1/) still gives me DNS lookup failed and the IP still points somewhere else.

---

### Post by rahul4557 on 2014-06-17
try it without [http://www](http://www).

just type
> 46.165.253.147  someshop.test1

---

### Post by whitee on 2014-06-17
Nope, it's the same.

> [www.someshop.test1](www.someshop.test1)	IPV4	error: -105 (ERR_NAME_NOT_RESOLVED)	2014-06-17 09:12:58.859 [Expired]


---

### Post by rahul4557 on 2014-06-17
try with www except http://
 [www.someshop.test1](www.someshop.test1)

---

### Post by whitee on 2014-06-17
> **rahul4557 said:**
> try with www except http://
 [www.someshop.test1]("http://www.someshop.test1")


Worked a treat, thank you

---

