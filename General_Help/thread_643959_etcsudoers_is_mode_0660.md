---
title: "/etc/sudoers is mode 0660"
date: 2007-12-18
forum: General Help
---

### Post by froggiestone on 2007-12-18
I didn't find any post related to this, so now i'm writing my first post :)

The thing is, that i might have changed the file permission on some system folders. But now when i'm logged normally in, i can't access admin programs anymore, nothing happens when i click the synaptic package manager for instance. i checked the auth.log and it says:

Dec 18 17:53:23 Superbrain sudo:   torben : /etc/sudoers is mode 0660, should be 0440 ; TTY=unknown ; PWD=/home/torben ; USER=root ; COMMAND=/usr/bin/restricted-manager

i tried open a terminal and write sudo chmod /etc/ 
But it just says the same: sudo: /etc/sudoers is mode 0660, should be 0440

How can i change it back :( ?

The reason why i did it was because i'm tired of typing my password all the time..

---

### Post by taurus on 2007-12-18
Boot into recovery mode from GRUB menu and run

```
chmod 440 /etc/sudoers
shutdown -r now
```
If you don't know what you are doing, stop monkeying around with file permissions or you will crash your machine beyond repair, eventually.

---

### Post by jken146 on 2007-12-18
If you want to change the password timeout for sudo, type ```
sudo visudo
```
Then go to the line that begins with **Defaults** and append the following to it. ```
,timestamp_timeout=**x**
```
where **x** is the number of minutes your password is 'remembered' for.  A negative number means 'forever'.  I have mine set to zero and I don't recommend increasing the timeout, especially setting it to forever, as this is far too close to running as root in my opinion.  Dangerous.

I don't know about your permissions thing though.

---

### Post by froggiestone on 2007-12-18
Cool, it worked fine, i'm not gonna do that again :)

And thanks for the tip on setting the session for the password :)

---

