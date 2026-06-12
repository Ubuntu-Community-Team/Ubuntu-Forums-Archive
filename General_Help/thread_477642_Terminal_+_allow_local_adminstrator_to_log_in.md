---
title: "Terminal + allow local adminstrator to log in"
date: 2007-06-18
forum: General Help
---

### Post by strife303 on 2007-06-18
Here's the situation:

My account doesn't have administrator privileges  via the system -> administration -> users and groups option, so I can't make changes with my home account. When I disabled admin access I also didn't check the "allow local administrator to log in" option, so I can't log in as root graphically to change this.

Thus said - cannot use alt+f2 nautilus.

What I can do is login with root in the terminal.

What's the command that will let me set my home account back to administrator level so I can access System -> Administration -> Services, etc w/ my home account?

Thanks in advance!!! I'd like to enable apache today but I'm still terminal-retarded from years of windows use.

---

### Post by Brucevdk on 2007-06-18
Looks to me like privileges are added through the use of groups. Try adding your user name to the admin group in */etc/group* by adding it to the end. Use an editor like nano (CTRL + X = exit).

This is what my */etc/group* file says:
```

admin:x:114:bruce

```

---

