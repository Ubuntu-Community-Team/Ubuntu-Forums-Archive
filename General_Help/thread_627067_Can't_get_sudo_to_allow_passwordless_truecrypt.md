---
title: "Can't get sudo to allow passwordless truecrypt"
date: 2007-11-29
forum: General Help
---

### Post by Pollywoggy on 2007-11-29
I have tried a couple of approaches to this after reading some tutorials for TrueCrypt, but none has worked.  I want to be able to use the "truecrypt" command without having to enter a password, so I used visudo to edit my sudoers file:

%truecrypt ALL=(root) NOPASSWD:/usr/bin/truecrypt

I also added myself to the group I created, "truecrypt"


When I use it with sudo, I am still asked for my password.

What am I doing wrong?

---

### Post by dagnabit dang doohickey on 2007-11-29
```
*username*   ALL = NOPASSWD: /usr/bin/truecrypt
```

If you want to run additional apps without passwords, add them to the same line using a comma separator. For example, this will also allow synaptic to run without a password:

```
*username*   ALL = NOPASSWD: /usr/bin/truecrypt, /usr/sbin/synaptic
```

---

### Post by Pollywoggy on 2007-11-29
> **dagnabit dang doohickey said:**
> ```
*username*   ALL = NOPASSWD: /usr/bin/truecrypt
```

If you want to run additional apps without passwords, add them to the same line using a comma separator. For example, this will also allow synaptic to run without a password:

```
*username*   ALL = NOPASSWD: /usr/bin/truecrypt, /usr/sbin/synaptic
```

Thanks, I think I found my problem.  NOPASSWD entries should be the last ones in the list.  I did not know that.  I knew order was important, but I had not put the NOPASSWD entry at the end of the file, so it did not work.

---

