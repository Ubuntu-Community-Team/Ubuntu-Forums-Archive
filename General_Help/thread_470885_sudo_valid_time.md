---
title: "sudo valid time"
date: 2007-06-11
forum: General Help
---

### Post by _simon_ on 2007-06-11
Is there anyway to change the amount of time that sudo privileges are available before having to re-enter your password, or forcing the password to be re-entered for certain commands regardless of when the password was last entered?

---

### Post by schorsch on 2007-06-11
> **_simon_ said:**
> Is there anyway to change the amount of time that sudo privileges are available before having to re-enter your password, or forcing the password to be re-entered for certain commands regardless of when the password was last entered?

There is a parameter called " timestamp_timeout" which can be set in /etc/sudoers. The usage is explained in the manpage of the sudoers file.

---

### Post by drs305 on 2007-06-11
You can edit the sudoers file with visudo (it can't be edited by normal text editors). Note: this is not a file you want to mess up!

```
sudo visudo
```

add the following line at the end:
				
Defaults:username timestamp_timeout=10	
			
Change the number to the timeout in minutes you desire. Replace 'username' with your username. You might need a blank line at the end.

Ctrl X, Y, enter to save

Note: usual disclaimer of the fact you are reducing the security of your system by extending the authentication timeout...

---

### Post by _simon_ on 2007-06-11
Thanks guys, I actually want to decrease the authentication timeout ;)

---

