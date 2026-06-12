---
title: "Chrome Notices . . ."
date: 2014-10-25
forum: General Help
---

### Post by Jack Sterling on 2014-10-25
For about a month I have been getting a message saying: "The application Chromium Web Browser has stopped unexpectedly." when, in fact, it is working fine. Why is this?

It happens almost daily. I send the notice and go right on working until it pops up again. In additional info it states; "It appears you have have made changes in the /etc directory" which is also not true.

OS: 14.04 w/Gnome desktop updated daily on an HP dm1. I have added both Xubuntu and Lubuntu (desktops only) for experimentation purposes.

---

### Post by tgalati4 on 2014-10-25
Open a terminal and run it and see if there are any initial errors:

```
google-chrome --debug
```

---

### Post by sammiev on 2014-10-25
This is likely the error you will see.

```
google-chrome --debug
ATTENTION: default value of option force_s3tc_enable overridden by environment.
Created new window in existing browser session
```

I have noticed this as well for sometime.

---

### Post by Jack Sterling on 2014-10-25
Thanks - tried it and got this returns: google-chrome: command not found

---

### Post by J_Me on 2014-10-25
If your using chromium try
```
chromium-browser -debug
```

---

### Post by Jack Sterling on 2014-10-26
Tried that also - same response: "command not found"

---

### Post by vasa1 on 2014-10-26
> **J_Me said:**
> If your using chromium try
```
chromium-browser -debug
```
Should be **chromium-browser --debug** with -- not -.

---

### Post by Jack Sterling on 2014-10-26
Tried that also - same response: "command not found"

---

