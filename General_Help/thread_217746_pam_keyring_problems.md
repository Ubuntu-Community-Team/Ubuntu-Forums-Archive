---
title: "pam keyring problems"
date: 2006-07-17
forum: General Help
---

### Post by Asewd on 2006-07-17
I installed pam_keyring to avoid putting in my keyring password every time networkmanager starts.  But, after I installed it, gdm wouldn't auto-login, constantly giving me "Authentication failed" errors, and I even couldn't login from a terminal, after putting in my username I get and invalid login error.  I booted up into single user and removed the package, but still got the same errors.  So, basically I can't login at all, ever, which isn't what I was trying to do at all.  So if anyone knows of anything I could try that would be great.

---

### Post by philippe_carlo on 2006-07-17
Boot in recovery mode. You should get a prompt, where you are logged in as root. Here you can change the password for any user, by typing passwd <user>.

---

### Post by Asewd on 2006-07-17
I don't think it's a password problem, I'll try resetting it when I get home, but when I try to login I enter my username and it fails, it doesn't even ask me for my password.

---

