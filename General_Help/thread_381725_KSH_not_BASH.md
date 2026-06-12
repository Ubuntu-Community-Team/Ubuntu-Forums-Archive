---
title: "KSH not BASH"
date: 2007-03-11
forum: General Help
---

### Post by Ezra on 2007-03-11
I've been using KSH and find it suits me more than BASH, I was wondering if anyone knew how to make it a default shell system wide and not BASH. Any help would be appreciated, thanks.

---

### Post by jrib on 2007-03-11
you can make it your default shell using the 'chsh' command.  I'm not sure exactly what you mean by "default shell system wide".  Do you mean for it to be the default for all new users?

---

### Post by Ezra on 2007-03-11
> Do you mean for it to be the default for all new users?
Yeah so if I, or another user (new or not), logs in it's the shell they use.

---

### Post by jrib on 2007-03-11
> **Ezra said:**
> Yeah so if I, or another user (new or not), logs in it's the shell they use.

Well you can change yours with 'chsh'.  To make it the default for new users you create, take a look at /etc/addusers.conf (I think the gui will use this too, but I am not sure).

---

