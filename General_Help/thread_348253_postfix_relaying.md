---
title: "postfix relaying"
date: 2007-01-28
forum: General Help
---

### Post by maino82 on 2007-01-28
Does anyone know if there's a way to have postfix relay via a certain smtp server based on whatever domain name the request is coming from. For example, if I have 2 domains and I want anything coming from domain1.com to be sent from [email]admin@domain1.com[/email] and everything from domain2 to come from [email]user@domain2.com[/email], is there a way to do that? My ISP blocks port 25, so I've had to set up postfix to relay via gmail, but the problem is so far I've only been able to figure out how to send email through only one email address, despite having multiple domains hosted on my box. Any help you could offer would be greatly appreciated!

---

### Post by etola on 2007-04-27
see this howto. 

[http://prantran.blogspot.com/2007/01/getting-postfix-to-work-on-ubuntu-with.html](http://prantran.blogspot.com/2007/01/getting-postfix-to-work-on-ubuntu-with.html)

it worked for me together with 

[http://freshmeat.net/articles/view/1673/](http://freshmeat.net/articles/view/1673/)

but i left the transport configuration as in fresmeat version.

---

