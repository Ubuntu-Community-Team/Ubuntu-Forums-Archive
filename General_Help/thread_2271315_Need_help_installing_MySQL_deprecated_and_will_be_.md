---
title: "Need help installing MySQL deprecated and will be removed in a future release"
date: 2015-03-29
forum: General Help
---

### Post by andreadixon825 on 2015-03-29
I'm trying to start mysql and I get this message, I dont understand what this means, Thank You

root@Bazic:~# > service mysqld start
150329  6:00:24 [Warning] Using unique option prefix key_buffer instead of key_buffer_size is deprecated and will be removed in a future release. Please use the full name instead.

I got it to run but know I'm getting this message.
 Access denied for user 'root'@'localhost' (using password: NO)

---

### Post by pmi2 on 2015-03-29
Its a warning alerting you to the fact that this prefix (meaning this exact name for a feature or function) has been superseded by another name, and should be avoided.  Old name being repalced by a new name, that is all.  See better explanation here: [http://en.wikipedia.org/wiki/Deprecation](http://en.wikipedia.org/wiki/Deprecation)

and also see in post below, scroll down to first answer:

[http://serverfault.com/questions/550734/is-it-key-buffer-or-key-buffer-size](http://serverfault.com/questions/550734/is-it-key-buffer-or-key-buffer-size)

---

