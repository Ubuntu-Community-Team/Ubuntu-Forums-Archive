---
title: "How do I enable WRITE messages for all users?"
date: 2006-12-03
forum: General Help
---

### Post by snakyjake on 2006-12-03
How do I enable WRITE messages for all users (I'm root)?

**I type this command:**
```
# write stacy 
```

**I receive this message:**
```
write: stacy has messages disabled
```

---

### Post by nixclusive on 2006-12-03
The write functionality seems to be enable by default in the 'screen' shell. Try creating a bash script that invokes screen with bash as the login shell. And then add this script to the users default login shell by using chsh.

---

### Post by encikraju on 2006-12-03
hi, i thought this is the right thread.
anyway, i got this problem because i am new to linux.
i cannot copy/cut folders/files because i dont have the permissions.
the owner is root and i logged as user(my desktop's name).
so, anyone? how to change the file permissions.
or should i change the partitions permissions?

---

### Post by taurus on 2006-12-03
```
gksudo nautilus
```

---

### Post by encikraju on 2006-12-03
hi, thanks for your reply.but it seem doesn't help me.
it requires a password and the password i've entered is wrong(i use my user pass).
the terminal give an error and warning.
the root windows popped out.
i'm really new and i've been googling a lot which doesn't help(or i'm so stupid enough).
really really needs help.

---

### Post by taurus on 2006-12-03
Maybe you need to read this...

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by encikraju on 2006-12-03
hi,thanks again.i thinks this is about my misconception.
i've just installed it yesterday.heheh...
the partitions actually are locked(read only using tree viewin window).
when i run again the gksudo nautilus, the root file browser window appeared.
but the partitions which contains the folders that i want to copy isn't there.

---

### Post by taurus on 2006-12-03
The partition which contains the folders is not there because you are currently in root, /root!  You need to navigate it over to your $HOME account, /home/*username*...

---

### Post by snakyjake on 2007-08-11
> **snakyjake said:**
> How do I enable WRITE messages for all users (I'm root)?

**I type this command:**
```
# write stacy 
```

**I receive this message:**
```
write: stacy has messages disabled
```

The solution to the original posted problem is that the remote user must have their terminal/console open.

---

