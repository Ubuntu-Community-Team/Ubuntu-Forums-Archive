---
title: "Guru99 website says &quot;sudo passwd -l 'username' &quot; is to &quot;Display all env variables&quot;."
date: 2021-02-14
forum: General Help
---

### Post by Swan_DB on 2021-02-14
[https://www.guru99.com/linux-commands-cheat-sheet.html](https://www.guru99.com/linux-commands-cheat-sheet.html) (it's under USER MANAGEMENT COMMANDS OF LINUX section).

I did```
sudo passwd -l
```and omitted any username, and my linux terminal came back with: 

> Usage: passwd [options] [LOGIN]

Options:
  -a, --all                     report password status on all accounts
  -d, --delete                  delete the password for the named account
  -e, --expire                  force expire the password for the named account
  -h, --help                    display this help message and exit
  -k, --keep-tokens             change password only if expired
  -i, --inactive INACTIVE       set password inactive after expiration
                                to INACTIVE
**  -l, --lock                    lock the password of the named account**
  -n, --mindays MIN_DAYS        set minimum number of days before password
                                change to MIN_DAYS
  -q, --quiet                   quiet mode
  -r, --repository REPOSITORY   change password in REPOSITORY repository
  -R, --root CHROOT_DIR         directory to chroot into
  -S, --status                  report password status on the named account
  -u, --unlock                  unlock the password of the named account
  -w, --warndays WARN_DAYS      set expiration warning days to WARN_DAYS
  -x, --maxdays MAX_DAYS        set maximum number of days before password
                                change to MAX_DAYS

Am I missing something, or is this Guru99 site wrong and giving bad info?

---

### Post by QIII on 2021-02-14
If your are looking in the "User management commands of linux" section, it looks like the first four commands' given descriptions are garbage -- repeated from the section above.

---

