---
title: "Evolution will not authenticate Exchange"
date: 2007-11-03
forum: General Help
---

### Post by flamingdragon on 2007-11-03
I am trying to set up Evolution to work with my uni OWA server, and, basically, it won't authenticate.  I type in the correct username and password (and address), hit authenticate, and it seems nothing happens. Doesn't fail authentication, nor succeed at it. But it wont let me continue the setup, either.

It definitely fails if I type the wrong password, as you would expect.

Any ideas?

---

### Post by pete on 2007-11-03
Don't know how your Exchange environment is set up, but I have to prepend my domain name and a backslash to my user name in Evolution's authentication prompt. e.g.:

[INDENT]"[domain_name]\[user_name]"[/INDENT]

Maybe you've already tried this, but you didn't mention it in your post.

---

### Post by flamingdragon on 2007-11-03
Sorry, yes, I did. The result was the same.

---

