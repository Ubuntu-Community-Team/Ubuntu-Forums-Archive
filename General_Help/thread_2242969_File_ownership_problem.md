---
title: "File ownership problem"
date: 2014-09-05
forum: General Help
---

### Post by mark114 on 2014-09-05
Hi

Files created by uploaded programs have the wrong file ownership and I can't do anything with them.

I have 2 groups ...

root
www-data

and one user: bluesplayer

When I upload files directly the group and ownership is fine: www-data / bluesplayer

When a program creates files on the server they are: www-data / www-data and I can't do anything with them.

How do I correct this?

Thanks

---

### Post by mcduck on 2014-09-05
Just add yourself to the *www-data* group. That's the best way to allow multiple users to access & edit files on a web server anyway, and works just as well even if you are the only user editing them.

```

sudo usermod -a -G www-data bluesplayer

```

---

### Post by mark114 on 2014-09-05
> **mcduck said:**
> Just add yourself to the *www-data* group. That's the best way to allow multiple users to access & edit files on a web server anyway, and works just as well even if you are the only user editing them.

```

sudo usermod -a -G www-data bluesplayer

```

When I try that I get this ... 

'cannot lock /etc/password; try again later'

is there something else the matter?

---

