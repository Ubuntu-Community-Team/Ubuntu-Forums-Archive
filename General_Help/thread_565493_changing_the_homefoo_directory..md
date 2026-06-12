---
title: "changing the /home/foo/ directory."
date: 2007-10-02
forum: General Help
---

### Post by 0core on 2007-10-02
i had change a user name, but the home directory of the user is still the same name as before. example, if i had changed user foo to bar, /home/foo still remains foo and isn't /home/bar/. it's not a big deal really, just keeps everything else more organized. is there a way to "export" all of the original files to another home dir or even just rename it? i'm so confused. :P

thanks in advanced.

---

### Post by Masterj15 on 2007-10-02
of you the root then you should be able to rename your folder

---

### Post by SOULRiDER on 2007-10-02
Check out the command **usermod**, there an option to move a user's home folder:
```
Usage: usermod [options] LOGIN

Options:
  -c, --comment COMMENT         new value of the GECOS field
  -d, --home HOME_DIR           new home directory for the user account
  -e, --expiredate EXPIRE_DATE  set account expiration date to EXPIRE_DATE
  -f, --inactive INACTIVE       set password inactive after expiration
                                to INACTIVE
  -g, --gid GROUP               force use GROUP as new primary group
  -G, --groups GROUPS           new list of supplementary GROUPS
  -a, --append          append the user to the supplemental GROUPS
                                mentioned by the -G option without removing
                                him/her from other groups
  -h, --help                    display this help message and exit
  -l, --login NEW_LOGIN         new value of the login name
  -L, --lock                    lock the user account
  -m, --move-home               move contents of the home directory to the new
                                location (use only with -d)
  -o, --non-unique              allow using duplicate (non-unique) UID
  -p, --password PASSWORD       use encrypted password for the new password
  -s, --shell SHELL             new login shell for the user account
  -u, --uid UID                 new UID for the user account
  -U, --unlock                  unlock the user account
```

---

### Post by scruff on 2007-10-02
```

sudo mv ~/olduserhome ~/newuserhome

sudo chown -R newusername ~/newuserhome

```

Assuming the group is still the same (users is default) then nothing else would be needed. Otherwise you need to hit it with 'chgrp' too.

---

