---
title: "$HOME/.dmrc file is being ignored"
date: 2007-04-20
forum: General Help
---

### Post by wsscott on 2007-04-20
Receive the following message when starting Ubuntu....

"User's $HOME/.dmrc file is being ignored.  This prevents the default session and language from being saved.  File should be owned by user and have 644 permisions.  User's $HOME directory must be owned by user and not writable by other users."

How do I find the file and fix the permissions?

Thanks

---

### Post by taurus on 2007-04-20
Press <Ctrl><Alt>F2 and log in with your username and password.  Then, at the prompt, run

```
sudo chmod 644 /home/**username**/.dmrc
sudo chown **username**:**username** /home/**username**/.dmrc
```
Replace **username** with your login name.

Reboot and see if you can log in to Gnome again.

```
sudo shutdown -r now
```

---

