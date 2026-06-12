---
title: "bypass sudo?!"
date: 2007-08-09
forum: General Help
---

### Post by sabokesa on 2007-08-09
Hi!
I've been wondering if i could bypass the sudo command for my user, for example if i would like to invoke a networking restart (/etc/init.d/networking restart) and not to enter sudo before the entire command by not logging on to root ?
thx in advance

---

### Post by heimo on 2007-08-09
> **sabokesa said:**
> Hi!
I've been wondering if i could bypass the sudo command for my user, for example if i would like to invoke a networking restart (/etc/init.d/networking restart) and not to enter sudo before the entire command by not logging on to root ?
thx in advance

Yeah, probably possible to do, and involves editing sudoers file using visudo. But depending on what you're trying to achieve, there may be better ways. To me, it seems that restarting network isn't too common task, so it can't be about five extra characters + password you need to type? (sudo + space + passwd)

---

### Post by muddymind on 2007-08-09
If U still want to avoid sudo do this:
```

sudo visudo -f /etc/sudoers 
```

add a line ate the end of file with this
```

username ALL = NOPASSWD: /etc/init.d/networking restart 
``` 
change username to your username

to exit press ctrl+X and it will ask if you want to save...
If there is some problem with the syntax it will warn you and you SHOULD NOT ANSWER "Q" (without the quotes)... Answer "e" (without the quotes) to edit it again to correct the error

[]

---

