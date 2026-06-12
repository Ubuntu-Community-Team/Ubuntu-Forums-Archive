---
title: "running Apache on any port except 80"
date: 2007-08-14
forum: General Help
---

### Post by boondocks on 2007-08-14
I selected the default LAMP system when I installed from the Ubuntu 6.06.1 Server CD.

Now I want to change the default http port 80 to some other number.

Where can I make this change?

---

### Post by robrmd9 on 2007-08-14
Hey,

Try changing /etc/apach2/ports.conf from 

```
Listen 80
```

to whatever port you want to use, then restart apache with 

```
/etc/init.d/apache2 restart
```

But if you are trying to use a port other than 80 because your ISP blocks port 80, and you are behind a router, consider forwarding the alternative port to your local server's port 80, and then you won't have to change apache's config at all.

Edit:  This is how my Feisty server is set up, so I'm not sure if Dapper's is the same.  But /etc/apache2 is the place to search for the listen port.

---

### Post by boondocks on 2007-08-14
Got it.   Thanks.

---

