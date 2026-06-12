---
title: "[SOLVED]Script not working as how i want"
date: 2017-11-21
forum: General Help
---

### Post by jaweewo on 2017-11-21
Ubuntu 16.04

I want an script to show up all the users connected to the system and then show the user full name and then the last time he logged ON. i tried something like: 

#!/bin/bash
who
lastlogon.

PD: Im new in ubuntu :P sorry guys, can you help me?[IMG]https://ubuntuforums.org/images/icons/icon10.png[/IMG]
PD2: lastlogon don't work if i write it alone but i look it up in network that it should work

---

### Post by litlesam on 2017-11-21
> **jaweewo said:**
> Ubuntu 16.04

I want an script to show up all the users connected to the system and then show the user full name and then the last time he logged ON. i tried something like: 

#!/bin/bash
who
lastlogon.

PD: Im new in ubuntu :P sorry guys, can you help me?[IMG]https://ubuntuforums.org/images/icons/icon10.png[/IMG]
PD2: lastlogon don't work if i write it alone but i look it up in network that it should work

Hi and welcome,

Have you tried

who
last username

---

### Post by yancek on 2017-11-21
Put a semi-colon after the first command and it is not "lastlogon" but rather last logon".

```
who; last logon
```

The link below gives various options for the 'who' command.  Not sure what you want with the "user full name"?

[https://www.cyberciti.biz/faq/unix-linux-list-current-logged-in-users/](https://www.cyberciti.biz/faq/unix-linux-list-current-logged-in-users/)

---

### Post by jaweewo on 2017-11-21
> **yancek said:**
> Put a semi-colon after the first command and it is not "lastlogon" but rather last logon".

```
who; last logon
```

The link below gives various options for the 'who' command.  Not sure what you want with the "user full name"?

[https://www.cyberciti.biz/faq/unix-linux-list-current-logged-in-users/](https://www.cyberciti.biz/faq/unix-linux-list-current-logged-in-users/)
Thanks bro! is just a test, i think i can take it with cut and /etc/passwd

---

