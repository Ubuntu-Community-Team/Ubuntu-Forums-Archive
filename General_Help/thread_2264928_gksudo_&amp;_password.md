---
title: "gksudo &amp; password"
date: 2015-02-11
forum: General Help
---

### Post by balia on 2015-02-11
I have a launcher with gksudo -u someuser firefox
Why does this launcher require root password instead of the password of the currently logged-in user.
The password window has the following message:
 "Enter YOUR password to run the application firefox as someuser"

NOTE: 
On my system, I enforce root password for all sudo requests.
In /etc/sudoers, I have "Defaults rootpw"
Is there any relation?

---

### Post by grahammechanical on 2015-02-11
It is my guess that like sudo, gksudo is triggering the request for an administrator password. In your case, someuser would have to have administrator privileges for their password to be accepted.

Are you aware that the command you are using will load Firefox with root or administrator privileges? I think that would be very risky. Why do you need a web browser to have administrator privileges? Any application with a GUI that we load with gksudo will have administrator privileges. 

Regards.

---

### Post by steeldriver on 2015-02-11
Am I correct in assuming you are trying to run the application as a different **non-root** user (using the -u or --user switch)?

If so, you might want to try adding --su-mode or -w

```

       --su-mode, -w

              Force gksu to use su(1) as its backend for running the programs.

```

---

### Post by balia on 2015-02-11
Sorry; my mistake in the orginal post, I should have mentioned that I was testing both gksu and gksudo:
```
gksu/gksudo -u someuser firefox
```
In this instance, gksu & gksudo behave the same in requiring root password.
I actually don't want someuser to have root privileges.
**The question should have been why gksu requires root password for someuser?**

When I try:
```
gksu --su-mode -u someuser firefox
```
I get "Failed to run Firefox as someuser" "This account is currently not available"
This is not entirely surprising as someuser has a /usr/sbin/nologin shell and the command fails accordingly.
Can I still run firefox for someuser (non root) with a nonlogin shell?

---

