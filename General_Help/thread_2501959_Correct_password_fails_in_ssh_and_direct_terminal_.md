---
title: "Correct password fails in ssh and direct terminal access - works in recovery mode"
date: 2024-10-28
forum: General Help
---

### Post by cumigoreng on 2024-10-28
Ubuntu 20.04 LTS
I was testing the hardening on the test system based on cis benchmark 2.0.1
In the middle of running the hardening script using sudo, apparently multiple same line in /etc/sudoers cause issue with the sudo. This was fixed by removing the duplicate line.

After reboot to attempt re rerun the script, i was locked out, both root and another admin user cant login using the correct password. 
In the single users  recovery mode, the password can be used for login.
Sudo -u otheradmin ps aux, shows otheradmin do run the task (im pretty sure pam.d/su* works fine).
Attempt to "passwd user" , then sync, doesnt correct the issue, both ssh and terminal access return incorrect login.
[SIZE=2][FONT=arial]Also tried [COLOR=#0C0D0E]pam-auth-update --force, just in case the problems is with pam.
[/COLOR][/FONT][/SIZE]
Below is the configuration that cause the issue (found it) :

Edit the /etc/pam.d/common-auth file and add the auth line below:
```
auth required pam_tally2.so onerr=fail audit silent deny=5 unlock_time=900
```

Edit the /etc/pam.d/common-account file and add the account lines bellow:
```

account requisite pam_deny.so
account required pam_tally2.so

```

whenever it was added to the respective pam configuration, the password will not work in terminal or ssh. 
trying to reset using  /sbin/pam_tally2 -u user  --reset, result in no such file or directory. The module exist for 20.04 though : [https://manpages.ubuntu.com/manpages/focal/man8/pam_tally2.8.html](https://manpages.ubuntu.com/manpages/focal/man8/pam_tally2.8.html)
Any ideas what how to fix this? 
Best regards

---

