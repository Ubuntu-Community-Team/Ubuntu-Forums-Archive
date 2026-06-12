---
title: "help with permissions"
date: 2007-05-27
forum: General Help
---

### Post by dayfall on 2007-05-27
i'm trying to access a fila named "pap_secrets" through the terminal so i can edit it to connect to the net. i'm logging in as a SU and still can't the right permissions. any ideas?
thx

---

### Post by taurus on 2007-05-27
What's the output of this command from a terminal?

```
ls -la pap_secrets
```

---

### Post by d@r!an101 on 2007-05-27
hey taurus,
dayfall wrote the post for me because i wasent registerd at the time...
now that i am i can say that i typed the command you submited here and the terminal said:
"no such file or directory"... 
im guessing thats not good?

---

### Post by taurus on 2007-05-27
Do you know where **pap_secrets** is located?  You need to be in the same directory to run that command or else you have to include the whole path.

```
ls -la /path_to/pap_secrets
-or-
cd /path_to
ls -la pap_secrets
```

---

### Post by d@r!an101 on 2007-05-27
oh i know where the file is!
its in "computer/filesystm/etc/ppp/"
but the thing is that the terminal's output is "permission denied" 
(plus - there is an X on the icon of "pap-secrets" and when i open its properties it tells me that im not the owner)
and thats after i logged in to root...!
that was the whole problem in the first place sorry for the confusion (:
any thoughts?

---

### Post by taurus on 2007-05-27
```
gksudo gedit /etc/ppp/pap_secrets
```
Please do not log in as root.  If you need to edit something, use either sudo or gksudo.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

