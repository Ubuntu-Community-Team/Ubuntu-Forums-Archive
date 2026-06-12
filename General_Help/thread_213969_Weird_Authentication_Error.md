---
title: "Weird Authentication Error"
date: 2006-07-12
forum: General Help
---

### Post by arthurbarnhouse on 2006-07-12
when I try to login as su in terminal I keep getting authentication error.  However, when I try to use something like synaptic which requires my password, it works just fine.  Does anyone have any idea what might be going on?

---

### Post by Malac on 2006-07-12
Are you still able to raise to root privileges with su or is it not working at all.
There is an authentication bug apparently that shows this message but you can still get to root privileges.

Please forgive if the next bit is too obvious.
If you are not getting to root privileges with su are you typing ```
sudo su
```
as you need to authenticate to get to root.

Hope this helps.

---

### Post by arthurbarnhouse on 2006-07-12
doesn't seem to be working at all.  Using su in terminal prompts the password, but the password doesn't seem to work I keep getting a failure.

And pelase be as obvious as you can.  I'm new to Linux.

---

### Post by user1397 on 2006-07-12
ubuntu does not use su or the root user account by default, instead it uses sudo.  for more info, read this: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by arthurbarnhouse on 2006-07-12
OK Then.  Thanks.

---

