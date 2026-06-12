---
title: "Facebook-App-ID - is this a number 234541986032774 or a name"
date: 2015-03-01
forum: General Help
---

### Post by dilbert_one on 2015-03-01
hello dear ubuntu-experts,


i have a site - a page on facebook. 

i want to have a facebook-feed that is displaying the last post on my wordpess-blog.

therefore i have set up several plugins in wordpress: 

some need to haeve a Facebook-App-ID - a number with  a number like that 234541986032774

and some others do not want to have a number like above - they need the page 

like so: https//www.facebook.com/my_page

note: ive found the following line

> 
Facebook App ID or User Token (for all facebook feeds). Not required to make the feed work. A User Token however will allow you to see certain post types that may be returning the message, Undefined Attachment. See how to GET APP ID or USER TOKEN.


so what is correct - do i need to fill out all the times the number or can i add the name of the page

love to hear from you

---

### Post by tgalati4 on 2015-03-02
The facebook API has changed several times.  That is what happens when linking from one service (facebook) to another service (wordpress).  So depending on when the tip was written, it is (or was) valid at the time of writing, but may not work today.  The general trend is for services to use tokens to improve security, otherwise any service can grab the feed and that might be a security problem.

Unfortunately, using tokens makes it difficult to get different feeds from the same service because the tokens are different and the method used to authenticate tokens probably uses IP address to allow only one token at a time.

---

