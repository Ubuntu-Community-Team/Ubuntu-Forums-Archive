---
title: "Can't get pam_unix to work in apache2"
date: 2005-04-24
forum: General Help
---

### Post by firepoet on 2005-04-24
Greetings all,

I've just converted over from Gentoo to Ubuntu (yeah, I know..hehe), and am having a little trouble with getting Apache2 to authenticate using pam_unix.

Here's my config stuff:

/etc/pam.d/apache2
```

@include common-auth
@include common-account

```

common-auth, common-account, and ssh files are all defaults in /etc/pam.d

/etc/apache2/mods-enabled/dav_svn.conf (snippet):
```

  AllowOverride None
  AuthType Basic
  AuthName "Repository"
  AuthPAM_Enabled on

  Require valid-user
  Order Allow,Deny
  Allow from all

```

Now, I've tried logging on with SSH (which also uses pam_unix) to make sure I'm not a total moron.  Here are the relevant log lines:

```

Apr 24 09:25:04 starkeylnx apache2: (pam_unix) authentication failure; logname= uid=33 euid=33 tty= ruser= rhost=127.0.0.1  user=stephen
Apr 24 09:25:29 starkeylnx sshd[21037]: Accepted keyboard-interactive/pam for stephen from ::ffff:127.0.0.1 port 42072 ssh2
Apr 24 09:25:29 starkeylnx sshd[21040]: (pam_unix) session opened for user stephen by (uid=0)
Apr 24 09:25:37 starkeylnx sshd[21040]: (pam_unix) session closed for user stephen

```

I used the same password (I copied it into the clipboard to make sure) and it worked with SSH and not with apache2.

Any thoughts are much appreciated!

-Stephen.

---

### Post by firepoet on 2005-04-24
Some more information:

I wrote a simple perl script to attempt PAM authentication, and, on a whim, ran the script as the www-data user.  Lo and behold, I got the same failure results!

So, the question now is, how do I tell Ubuntu that the www-data user has the power to do Pam authentication?

Thanks!

-Stephen.

---

### Post by firepoet on 2005-04-24
Answer found:

Put www-data into the shadow group

Never mind, I guess!

:-)

---

### Post by crazybill on 2005-04-24
Thanks for the question and the answer!

---

