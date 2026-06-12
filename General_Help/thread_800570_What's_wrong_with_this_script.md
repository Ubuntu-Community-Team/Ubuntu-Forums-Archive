---
title: "What's wrong with this script?"
date: 2008-05-20
forum: General Help
---

### Post by knottshawk on 2008-05-20
I've got a script here that's supposed to log me into my proxy server... here's the script:

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

### Post by sardion on 2008-05-20
> **knottshawk said:**
> I've got a script here that's supposed to log me into my proxy server... here's the script:

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


You're not going to get that to work.  If you want to login to an ssh server without typing the password, you'll have to make a (passwordless) ssh key.

---

### Post by knottshawk on 2008-05-20
You want to tell me *why* it's not going to work? There are sample scripts all over the internet showing it working.

Is there something specific there that won't work?

---

### Post by bingoUV on 2008-05-20
Put expect in the title. Anyone with experience with expect will pay attention then. Right now it is attracting general shell script enthusiasts.

---

