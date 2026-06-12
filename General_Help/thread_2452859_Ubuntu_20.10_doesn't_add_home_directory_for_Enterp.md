---
title: "Ubuntu 20.10 doesn't add home directory for Enterprise Active Directory Accounts"
date: 2020-10-29
forum: General Help
---

### Post by nhasian on 2020-10-29
installed Ubuntu 20.10 on a Raspberry Pi 4. After logging in with the user account I created during installation, I added an Enterprise user for Active Directory. 

I am able to log in with my Active Directory credentials. Unfortunately, a home account is not created for this user. As a result, programs such as firefox, chromium, etc, do not run properly. 


Is a home directory supposed to be created for enterprise users? How can I correct this?

----------------------

I found the solution to the problem. You have to run ```
pam-auth-update
``` and tick the option "Create home directory on login"

This will create a new user directory for each active directory user that logs in. Things will function normally after that such as firefox starting. I will have to submit a bug report about this.

---

### Post by SeijiSensei on 2020-10-29
What happens if you run
```
sudo useradd username
```

---

### Post by nhasian on 2020-10-29
I am not trying to add a local user, I have already added an Enterprise user via Active Directory that authenticates on a Windows AD Server. I tried manually adding the directory, but then I am unable to chown it to the user because the username is [email]user.name@domain.com[/email].
The user is not listed in /etc/shadow or /etc/passwd

---

