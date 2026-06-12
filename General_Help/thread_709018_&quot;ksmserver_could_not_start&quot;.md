---
title: "&quot;ksmserver could not start&quot;"
date: 2008-02-27
forum: General Help
---

### Post by vkshiu on 2008-02-27
My kubuntu does not log on to my user account. Once I put in my user and pass, the message "ksmserver could not start" and kicks me back out to the logon screen.

I am able to log on as console. I have tried removing ksmserver and then reinstall it (along with kubuntu-desktop). That did not work. This is the second time it has happened to me, with no prior warning. Shut down fine, then the next day I go turn it on this happens.

Help please?

---

### Post by amingv on 2008-02-27
Maybe one of the . files has changed owners/group in your home directory?
try running:

```
sudo chown -v yourusername:yourusername .ICEauthority .k*
```

---

### Post by vkshiu on 2008-02-27
> **amingv said:**
> Maybe one of the . files has changed owners/group in your home directory?
try running:

```
sudo chown -v yourusername:yourusername .ICEauthority .k*
```

Turns out it has to do with the language pack upgrade problem.. thanks anyhow!

---

### Post by ostracize on 2008-02-29
Could you be a little more descriptive? I just experienced the same problem and I know that I upgraded some language packs recently. How do I get back to status quo?

---

### Post by ostracize on 2008-02-29
Bump

---

