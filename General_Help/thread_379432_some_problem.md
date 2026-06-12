---
title: "some problem"
date: 2007-03-08
forum: General Help
---

### Post by Syncman on 2007-03-08
hi, i am new to this environment (linux).
im looking for windows alternative so i choose and download kubuntu edgy. i got problem and i cant figure out how to connect my dsl. The only things i found is the kppp dialer (i know it's for dial up) i tried browsing thru the help files (search:pppoe) i found one but doesn't giveout a lot of info.

And one more thing, what's the password for root or administrator???. network connection ask for it but i ended up guessing the password.

---

### Post by etank on 2007-03-08
> And one more thing, what's the password for root or administrator???. network connection ask for it but i ended up guessing the password.
Reply With Quote

Ubuntu disables the root user account by default. When an application is asking for a password like that you just use your own. To do tasks as root use sudo. 

For example:
```
sudo aptitude upgrade
```

Here is a doc to support this. [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

As far as dsl is concerned I am not sure. Are you using a router? Are you wired or wireless?

---

### Post by Syncman on 2007-03-08
hi, i figure out how to connect via pppoe i use sudo pppoeconf

thanks btw for the reply :)

---

