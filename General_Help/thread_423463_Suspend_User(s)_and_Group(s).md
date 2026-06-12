---
title: "Suspend User(s) and Group(s)"
date: 2007-04-25
forum: General Help
---

### Post by dbenson on 2007-04-25
I would like a quick way to suspend one or multiple user accounts. I'm a parent with three kids. At times I want to prevent one or more of them from logging into the computer. Is there a quick way that I, as admin, can easily prevent them from loging in. If I could do this remotely, that would be even better. The only way I have figured out is to go into each of the user preferences and change each of their passwords manually. Then I have to repeat the process to re-enable them. Thanks.

---

### Post by taurus on 2007-04-25
Or you can change their shell from /bin/bash to /bin/false in /etc/passwd.

```
sudo nano -Bw /etc/passwd
```
<Ctrl>o to save and <Ctrl>x to exit.

---

