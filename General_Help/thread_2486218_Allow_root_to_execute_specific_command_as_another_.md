---
title: "Allow root to execute specific command as another user without user password"
date: 2023-04-23
forum: General Help
---

### Post by Drenriza on 2023-04-23
Hi all
How can I in /etc/sudoers.d/root (or some other filename) allow the root user
to execute the command

```
runuser -u USERNAME -c '/path/to/command/'
```

Without entering the user-password to execute the command as that user?
It is only a single command or script I would like the root user to be allowed to execute this way, so not * (everything).

If you have command to accomplish the same thing, please do not hesitate to add it, I am not exclusive with runuser.

Please note, using visudo is not an option because I need it to be non-interactive to be used in an automatic deployment.

Any suggestions or advice?

I am using Ubuntu 22.04 LTS

Thank you in advance
Best regards

---

### Post by TheFu on 2023-04-23
> **Drenriza said:**
>  
I am using Ubuntu 24.04 LTS

Impressive.  Here, it is still 2023. ;)

---

### Post by The Cog on 2023-04-23
runuser doesn't ask for a password. So the command you posted should work.

---

### Post by TheFu on 2023-04-23
root can run anything as any user.  No sudoer changes needed.  Perhaps the description isn't correct/clear for what you are really trying to accomplish?

---

