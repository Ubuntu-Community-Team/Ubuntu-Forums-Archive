---
title: "Kind of Fixed!  - Evolution CPU usage problem"
date: 2008-04-30
forum: General Help
---

### Post by the_maassk on 2008-04-30
For those (like me) who were plagued by the CPU usage peaking up (and staying there) when using Evolution (specifically when you open the Compose Message window) - I discovered a kind of FIX -

I noticed that the CPU would spike up and the Compose window would become sluggish when trying to fetch email address from LDAP servers for me.

In Preferences >> Autocompletion - I unchecked my LDAP servers from the list and just left the 'Personal' address book there as checked. I then went to the address book and copied over all my contacts from the LDAP servers to the Personal address book. I know I will not get updated/added addresses from the server now - but that only happens once in a while. I can always copy over the addresses once a month or something.

Now my Evolution is USABLE again :guitar:

Hope this helps someone!

---

### Post by Nunu on 2008-04-30
It did thanks for the tip

---

### Post by arcanus on 2008-05-23
So the problem is narrowed down to the autocomplete then, very nice :)

Magne

---

### Post by Lester King on 2009-03-11
Worked for me. Thanks a lot!

---

