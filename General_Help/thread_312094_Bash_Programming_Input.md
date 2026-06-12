---
title: "Bash Programming Input"
date: 2006-12-03
forum: General Help
---

### Post by Bakerconspiracy on 2006-12-03
Hello,
I have created a small and simple script to connect remotely to my ssh server. It reads as follows.

#!/bin/bash
ssh admin@.....

now what command would i use to put the input in for the password and press enter like i would have to logging into my server?
(I hope i put this thread in the right place :-k )

---

### Post by kevinlyfellow on 2006-12-03
you can put it in as a arguemnt, for example you might run the script like
```
./sshscript mypassword
```
in this case the password is stored as the variable $1

or you can use the read command
```

echo "enter password"
read -s password #the  -s is so that no one 
[INDENT]#can read the password while your typing[/INDENT]

```

in which case the password is stored as the variable $password

Hope I answered your question

edit:
after reading your post again, I think I missed your question, sorry.  If your looking for to input the password for ssh automatically in a script, I'm not sure how to do it or if you can, it might become a security problem if it did allow for such a thing

---

### Post by syxbit on 2006-12-03
use public and private keys
much safer/easier

---

### Post by Bakerconspiracy on 2006-12-03
yea i am looking for it to input the password for my ssh server automatically. i agree it is a bit of a security problem if it let me do so but i just wanted to make it easy to run a script and be connected:D, ya know?

---

