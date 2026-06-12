---
title: "Login and Non-Login Shells"
date: 2007-01-19
forum: General Help
---

### Post by Buck2348 on 2007-01-19
I have automatic login enabled.  Does the system read/execute my .bash_profile during startup, or must I include everything I want to run (e.g. adding to the $PATH) in .bashrc?  If so, what is the .bash_profile file good for?

Thanks,
Buck

---

### Post by bodhi.zazen on 2007-01-19
Bash configuration files: [http://heimhardt.com/htdocs/bashrcs.html](http://heimhardt.com/htdocs/bashrcs.html)

In .bash_profile

Add:> source /home/username/.bashrc

---

### Post by Buck2348 on 2007-01-19
Thank you very much.

Buck

---

