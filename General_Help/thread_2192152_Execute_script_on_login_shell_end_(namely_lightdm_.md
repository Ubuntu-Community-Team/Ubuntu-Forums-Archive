---
title: "Execute script on login shell end (namely lightdm and ssh) or decrypt on boot"
date: 2013-12-06
forum: General Help
---

### Post by helloworld1215 on 2013-12-06
I would like to have services that access resources that are decrypted before said services start. Ie, I want encrypted directories served by apache or the data dir of postgresql to be encrypted. 

Considering this I have the following functionalities I am interested in:

1. I would like decrypt a container on boot with a password prompt so that the services can be started subsequent to that. Will the boot be successfully interrupted by a prompt for input if one were to add such an prompting executable to the runlevel? Does a shell even exist for such a prompt at boot?

2. Another functionality that has value disparately from the specified goal (as it is a fundamentally incorrect implementation because one cannot run dedicated services from a permanently logged in shell) would be:

How does one specify a script to be run on shut down of login shells for a user? Ie, start services from .profile and stop them from a script that automatically runs on exit from the lightdm-session and other shell login sessions, namely ssh.

---

### Post by helloworld1215 on 2013-12-06
1. Can be resolved by cryptdisks and /etc/crypttab
2. Would still be interested in the location for a script run on user logout.

---

### Post by steeldriver on 2013-12-06
For sessions managed by lightdm, you could try specifying a script to be run via the session-cleanup-script parameter - see the sample file at /usr/share/doc/lightdm/lightdm.conf.gz

```

# session-cleanup-script = Script to run when quitting a user session (runs as root)

```

For ssh sessions, you could try the user's .bash_logout file (although be aware this will only be triggered by 'graceful' logouts, not SIGHUPs) - you may find this superuser.com answer helpful [http://superuser.com/a/410534](http://superuser.com/a/410534)

---

