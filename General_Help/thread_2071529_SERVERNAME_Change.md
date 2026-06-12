---
title: "SERVERNAME Change"
date: 2012-10-15
forum: General Help
---

### Post by dpbklyn on 2012-10-15
Hello and thank you in advance...

I just noticed that my development servers name have changed to SERVERNAME.  That is...the prompt that used to say username@acme:~$ now says username@SERVERNAME:~$.  I dont remember changing anything, but then again I may have.  I am a newbie, so I am not really sure where this would be set.

Again, I am a relative newbie to ubuntu so please be gentle.

Thank you,

dp

---

### Post by Cheesemill on 2012-10-15
Can you post the results of the following please:
```
echo $PS1
hostname
```

---

### Post by dpbklyn on 2012-10-16
Thank you for your response...

```
Last login: Mon Oct 15 15:23:06 2012 from 192.168.12.53
dp@SERVERNAME:~$ echo $PS1
\[\e]0;\u@\h: \w\a\]${debian_chroot:+($debian_chroot)}\u@\h:\w\$
dp@SERVERNAME:~$ hostname
SERVERNAME
```

---

### Post by Cheesemill on 2012-10-16
You've somehow changed the name of your system.
To change it back you need to edit the /etc/hostname and /etc/hosts files and replace SERVERNAME with acme (or whatever the correct name is).

---

