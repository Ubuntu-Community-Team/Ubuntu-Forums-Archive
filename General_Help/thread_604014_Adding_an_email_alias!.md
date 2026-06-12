---
title: "Adding an email alias??!"
date: 2007-11-05
forum: General Help
---

### Post by stormfrog on 2007-11-05
Hi,

I have installed some default e-mail server following the guide from ubuntu.

I have been searching all night for how to add an e-mail alias but there just isnt any information about it. Ive found some retarded newsgroups for linux nerds  but no actual guide for how to simply do this.

I am running postfix and something... courier? Dunno how to check which one I installed.

I am just looking for a command like "addemailalias f00" that will forward all mail sent to [email]f00@mydomain.org[/email] to my own account [email]myuser@mydomain.org[/email].

How is this done? It refuse to believe it can be more advanced than this.

Ive read all the postfix manual and all Ive found is reference to a some value called postfox_virtual_maps in the postfix database. Someone must be joking if they think users are going to edit the postfix database manually :D 

Regards,

---

### Post by dkirk on 2007-11-05
I admit that I haven't done this before, but it seems pretty easy.  Check out man aliases.  I haven't got postfix installed, but I found the man page at [http://www.postfix.org/aliases.5.html](http://www.postfix.org/aliases.5.html)

I would edit /etc/aliases and add
```
f00: myuser
```
and then run either newaliases or postalias.  That should do it.

-- 
Later

David Kirk

---

### Post by dcstar on 2007-11-06
> **dkirk said:**
> I admit that I haven't done this before, but it seems pretty easy.  Check out man aliases.  I haven't got postfix installed, but I found the man page at [http://www.postfix.org/aliases.5.html](http://www.postfix.org/aliases.5.html)

I would edit /etc/aliases and add
```
f00: myuser
```
and then run either newaliases or postalias.  That should do it.

-- 
Later

David Kirk

All of that should work, it is quite easy once you have the basic postfix up and working (I have root e-mails from logcheck forwarded to my user account this way, and then I have Evolution pick them up every minute from my local system).

---

