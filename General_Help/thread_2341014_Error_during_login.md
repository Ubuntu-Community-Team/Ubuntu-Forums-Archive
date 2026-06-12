---
title: "Error during login"
date: 2016-10-24
forum: General Help
---

### Post by sheikki on 2016-10-24
After I login, I get this error message:

```
find '/etc/apt//sources.list': No such file or directory
find '/etc/apt//sources.list': No such file or directory
```

Obviously such file does not exist (the double slash). However, I have absolutely no idea why find is trying to find such file. I don't have ~/.bash_profile. My ~/.profile sources ~/.bashrc. There's nothing about sources.list in my ~/.bashrc. What might be causing the call that leads to the error message? Root and user crontabs are empty so it's not that at least. OS is Ubuntu 14.04.5 LTS. Is there some log that might reveal what is causing this?

---

### Post by ajgreeny on 2016-10-24
Could it be that update manager which is checking for updates after login is looking for that incorrect pathway for some reason.

I have the update manager/notification turned off on my system and have no idea where the configuration for it might be but it could be worth a search for an update-manager.conf file or similar to see if there is a problem there.

---

