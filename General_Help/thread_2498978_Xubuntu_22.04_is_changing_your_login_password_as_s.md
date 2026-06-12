---
title: "Xubuntu 22.04: is changing your login password as simple as this?"
date: 2024-07-06
forum: General Help
---

### Post by ardouronerous on 2024-07-06
[IMG]https://i.redd.it/bna7xoch9vad1.jpeg[/IMG]

Hello, I want to change my login password, but I've never done it before, so I'm a little hesitant because I don't want to brick my current install. So, I'm looking for some advice before I do this.

So, is changing your login password as simple as this?

---

### Post by ajgreeny on 2024-07-06
Not quite!
Changing that will simply change your setting which currently asks for your password at login and allow you to set autologin, not a secure method of login in, in my opinion.

I'm not on a Linux box at the moment and can't remember the exact command needed but try **passwd <username> *newpassword***
You will be asked to confirm the new password but that should then be set.

---

### Post by ardouronerous on 2024-07-06
This is the result:

```
passwd ardouronerous newpassword
Usage: passwd [options] [LOGIN]

Options:
  -a, --all                     report password status on all accounts
  -d, --delete                  delete the password for the named account
  -e, --expire                  force expire the password for the named account
  -h, --help                    display this help message and exit
  -k, --keep-tokens             change password only if expired
  -i, --inactive INACTIVE       set password inactive after expiration
                                to INACTIVE
  -l, --lock                    lock the password of the named account
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
```

---

### Post by Holger_Gehrke on 2024-07-06
Actually, it is that simple. If you click on 'Change' you get a form in which you have to enter your current password and can then change the password (or create a random one). You can *also* set automatic login in that form. See image of the form attached.

Holger

---

### Post by ardouronerous on 2024-07-06
> **Holger_Gehrke said:**
> Actually, it is that simple. If you click on 'Change' you get a form in which you have to enter your current password and can then change the password (or create a random one). You can *also* set automatic login in that form. See image of the form attached.

Holger

I tested this out on a virtual machine, yes it worked, thanks.

---

### Post by ajgreeny on 2024-07-08
Just shows how much I've forgotten about some of these simple things, but it's been nearly 20 years since I even looked at that screen.

I will now examine it more closely!

---

