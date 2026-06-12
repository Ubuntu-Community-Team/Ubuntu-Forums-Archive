---
title: "Trying to install program keep getting an error"
date: 2017-01-29
forum: General Help
---

### Post by fruggle on 2017-01-29
```
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 discord : Depends: libappindicator1 but it is not going to be installed
 git : Depends: liberror-perl but it is not going to be installed
       Depends: git-man (> 1:2.7.4) but it is not going to be installed
       Depends: git-man (< 1:2.7.4-.) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
``` 

Every time I try to install anything with apt-get I always get this error, any thoughts?

---

### Post by ian-weisser on 2017-01-29
Did you try the system's recommended solution? (it's on the bottom line of the error message)

---

### Post by Bucky Ball on 2017-01-30
Welcome. Did you also try:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get dist-upgrade
```

The last command will NOT upgrade your current release to a newer one. Post any and all errors you get from those commands. If none, try to install something and post any and all errors you get from that, if any. 

Always include the release and flavour of Ubuntu you are using in support requests. Will help to speed things up. ;)

---

