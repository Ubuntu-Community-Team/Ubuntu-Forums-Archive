---
title: "Ubuntu 13.04 Virtualbox extension pack - password"
date: 2013-08-10
forum: General Help
---

### Post by dj722000 on 2013-08-10
Alright another one got me. When I installed Ubuntu, I only gave one password I use to log into Ubuntu. Thats it. No passwords any place else. Well, I insalled virtualbox and I needed to install the extension pack and it asked me for a password, so I typed mine in and it is now telling me it is the wrong password!!!!!!!!!! Just what password are they asking for? I never gave one to Oracle or any other place as I have not signed up through them, only to Ubuntu when I installed it. I have no idea what password they are asking for as it will not except mine. Any ideas where to get my password for this?

Oh ya, to install the extension pack, I just sudo su in the terminal, then dropped the extension pack into the terminal, it started to install until it asked me for what ever password they are looking for, apparently not mine. Is there something special I need?

---

### Post by dj722000 on 2013-08-10
Oh my, I got it. What a pain. 

Have to open terminal, type gksu-properties

If it is set to su, have to change it sudo

Then it excepts your password.

---

### Post by cumari on 2013-08-17
thx you so much!

it works!:P

---

### Post by howefield on 2013-08-17
Or for those who don't run a mile at the sight of a terminal...

```
sudo VBoxManage extpack install path_to_the_extpack_package
```

Substituting "path_to_the_extpack_package" with the actual path on your machine.

---

