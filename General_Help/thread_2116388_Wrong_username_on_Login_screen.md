---
title: "Wrong username on Login screen"
date: 2013-02-15
forum: General Help
---

### Post by an0n1 on 2013-02-15
Just installed Ubuntu via Wubi for the second time, wubi prompted me for a username and password before installation which I entered. Now when I get to the login screen the wrong username is showing (this could be the username used with a previous install). I managed to jump into a terminal and login with the credentials I provided before installation. 

I'd just like to know how I'd go about replacing the wrong username at the graphical login screen with the right one via the terminal. I couldn't see a way to change it from the login screen itself.

edit: I tried to change the password for the account showing on the graphical login screen, but it's telling me the user does not exist.

---

### Post by linuxsyst on 2013-02-15
You could make a new user ```
adduser <usernane> --group admin
```

---

### Post by an0n1 on 2013-02-15
> **linuxsyst said:**
> You could make a new user ```
adduser <usernane> --group admin
```

I have a username that works through the terminal, I just want that user to show on the graphical login instead of this one that is apparently non-existent. :)

---

### Post by steeldriver on 2013-02-15
AFAIK the lightdm login screen displays the 'full name' field from the /etc/passwd file rather than the actual login name that's used by the system - you can change the full name (aka 'display name') using either the GUI 'User Accounts' tool or with the chfn command

```
sudo chfn -f "*what ever*" *user*
```where *user* is your actual login name i.e.

```

$ sudo chfn -f "John Henry" steeldriver
$
$ grep steeldriver /etc/passwd
steeldriver:x:1002:1002:John Henry,,,:/home/steeldriver:/bin/bash
$ 

```

---

