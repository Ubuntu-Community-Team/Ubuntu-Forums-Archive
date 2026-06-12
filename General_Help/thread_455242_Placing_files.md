---
title: "Placing files?"
date: 2007-05-26
forum: General Help
---

### Post by Hendrick on 2007-05-26
Hello

When I go to System-->Admin-->Users and Groups, only two users show up.  One is the one I created when I installed Ubuntu, and the other is "root".

I was trying to put a file into the /opt/ folder (this one program needs to be there), and I got the error that I don't have Permission.  I pretty much don't have permission anywhere except in the /home/ folder.

So I was wondering, how do I get permission to put a file there?  I assume I would have to log into that other "root" account, but I'm not sure how.  When the login screen for Ubuntu comes up when I restart, it says that this isn't the place to login, or something along those lines.

Any help would be appreciated.

Thanks.

---

### Post by Bachstelze on 2007-05-26
You use sudo :

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Hendrick on 2007-05-26
So am I just typing this?

> sudo -i

I did that, but I still can't drag the file to that folder.  Is there a command I have to use in Terminal to move the file then?

---

### Post by Bachstelze on 2007-05-26
If you want to use the graphical file manager with root privileges, do this :

```
gksudo nautilus
```

I wouldn't recommend it but do as you wish...

---

### Post by Hendrick on 2007-05-26
Thank-you.

---

