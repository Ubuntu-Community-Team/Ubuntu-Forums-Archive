---
title: "PAM cracklib minclass is not beeing recognized"
date: 2007-11-15
forum: General Help
---

### Post by gibking on 2007-11-15
Hi folks,
i have a problem with my pam configuration, that is:
The minclass option for the pam_cracklib module is beeing ignored.

My /etc/pam.d/common-password looks like this
```

password required         pam_cracklib.so retry=3 minclass=3 minlen=8 difok=4
password required         pam_unix.so use_authtok remember=5 md5

```

Nevertheless i can set my password to 'asdfghjk'.
What am I doing wrong?

Another thing is that I'd like to prevent users from choosing a password they already had in the last 5 months. Is there a PAM module out there which can provide this? Or do i have to "remember=999999" and delete the /etc/security/opasswd every 5 months?

Thanks in advance

---

