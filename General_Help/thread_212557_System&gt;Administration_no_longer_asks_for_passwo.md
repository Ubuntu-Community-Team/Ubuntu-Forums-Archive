---
title: "System&gt;Administration no longer asks for password?"
date: 2006-07-10
forum: General Help
---

### Post by Boomy on 2006-07-10
It just stopped asking all of a sudden. I logged out and back in and it still allows me to make all the changes I want without a password.

---

### Post by Boomy on 2006-07-10
Rebooted and its back to normal.

---

### Post by frodon on 2006-07-10
It's how sudo is configured by default, once you typed your root password a 5 minutes period start during which you don't have to type the sudo password anymore.
Obviously you can configure this time to a different value (even 0 if you want to type your password all the time).

Related link : 
[http://doc.gwos.org/index.php/Change_default_timeout_in_sudo](http://doc.gwos.org/index.php/Change_default_timeout_in_sudo)

---

### Post by scxtt on 2006-07-10
it's also timed, so if you enter it once - then you start a task that requires a p/w, it won't ask you again til 'times up' ...

---

