---
title: "update manager does not run automatically anymore"
date: 2013-06-13
forum: General Help
---

### Post by ELMIT on 2013-06-13
I must run now then and when update-manager from the command line, since it is running anymore automatilcally.

I am not sure if it is related to that, but when I run it in a command window, then I see:
> update-manager
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied


The update settings are for daily.

Also maybe related, I get everday now the message that an online account needs attention. Each time I just need to enable the accounts for facebook and twitter. It seems it does not remember it till tomorrow.

---

### Post by sandyd on 2013-06-13
[https://bugs.launchpad.net/ubuntu/+source/debconf/+bug/959364](https://bugs.launchpad.net/ubuntu/+source/debconf/+bug/959364)

---

### Post by ELMIT on 2013-06-13
So it is a bug and as the link shows, there is no cure yet?

---

### Post by bugbear6502 on 2014-01-16
I think I know what causes this - I once ran 

sudo update-manager

and now I get this message, and update-manager does not ask for authentication.

I think running update-manager as root has created some permission problems.

Can anyone advise on this normal "clean install" permissions and content of this file?

 BugBear

---

