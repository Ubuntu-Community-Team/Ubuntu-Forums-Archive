---
title: "Help with EXPECT script?"
date: 2008-05-20
forum: General Help
---

### Post by knottshawk on 2008-05-20
I've got an expect script here that's supposed to log me into my proxy server... here's the script:

#!/usr/bin/expect -f

spawn ssh -D 1088 -p 80 [email]myname@myipaddress.com[/email]
expect "*password:*"
send -- "mypassword\r"

----------------------------
When I run that script, the output I get is like this:

spawn ssh -D 1088 -p 80 [email]myname@myipaddress.com[/email]
[email]myname@myipaddress.com[/email]'s password: myterminalprompt:~$

So what am I doing wrong?
I've tried many different combinations and styles of the expect and send commands and nothing works.

---

### Post by knottshawk on 2008-05-20
Anyone?

---

