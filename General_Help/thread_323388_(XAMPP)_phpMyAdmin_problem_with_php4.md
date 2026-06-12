---
title: "(XAMPP) phpMyAdmin problem with php4"
date: 2006-12-22
forum: General Help
---

### Post by rustncogs on 2006-12-22
[B]Hi all,

So earlier I installed XAMPP.

Everything was going fine until I switched to php4, now phpMyAdmin doesn't work, and says:[/B]


Warning: session_write_close() [function.session-write-close]: The session id contains invalid characters, valid characters are only a-z, A-Z and 0-9 in /opt/lampp/phpmyadmin/index.php on line 44

Warning: session_write_close() [function.session-write-close]: Failed to write session data (files). Please verify that the current setting of session.save_path is correct (/tmp) in /opt/lampp/phpmyadmin/index.php on line 44

Warning: Cannot modify header information - headers already sent by (output started at /opt/lampp/phpmyadmin/index.php:44) in /opt/lampp/phpmyadmin/index.php on line 101

[B]If I switch back to php5 though it works fine.

Any ideas?

Thanks.[/B]

---

### Post by tamir n on 2007-02-21
if you use XAMPP   1.6 only.
i have the same thing to.


but in the second computer i install the xampp 1.55  and there was no problem.
i see that the phpmyadmin 2.9.2 is the problem p.s. (2.9.2 is the version on  XAMPP 1.6, and 2.9.1 is the version on  XAMPP 1.55)
or second guess is the php 4.4.5 compile problem.

i hope it will help

---

