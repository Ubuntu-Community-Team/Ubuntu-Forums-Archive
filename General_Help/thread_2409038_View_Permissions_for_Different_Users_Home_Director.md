---
title: "View Permissions for Different Users Home Directory"
date: 2018-12-27
forum: General Help
---

### Post by nuttboxer2 on 2018-12-27
How can I view the home directory permissions for a user other than the one I'm logged in as?  The user does not have a password set.

---

### Post by deadflowr on 2018-12-27
```
ls -l /home
ls -l /home/username
```
change username to the users name.

---

### Post by nuttboxer2 on 2018-12-27
Not sure what designates a code block here, markdown doesn't seem to work...

Code:
ls -l /home/serviio
ls: cannot access '/home/serviio': No such file or directory

The directory does exist
Code:
cat /etc/passwd
serviio:x:999:999::/home/serviio:/bin/false

---

### Post by spjackson on 2018-12-27
> **nuttboxer2 said:**
> Not sure what designates a code block here, markdown doesn't seem to work...

[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
> 
Code:
ls -l /home/serviio
ls: cannot access '/home/serviio': No such file or directory

That means what it says: the directory does not exist. Why did you skip the first step? 
> 
```

ls -l /home 
```

> 
The directory does exist
Code:
cat /etc/passwd
serviio:x:999:999::/home/serviio:/bin/false
That shows what the user's home directory is declared to be. It does not show that it exists.

---

### Post by nuttboxer2 on 2018-12-27
I skipped the first step because it's going to show me the home  directory for logged in user, not the user I want to see the home  directory for(see post title).  I was under the impression the error was  also due to not being the correct user, and did not realize passwd was  declaring only.  Used:
```

sudo mkhomedir_helper serviio

```
And now my home directory exists.  Thanks for pointing out those issues!

---

### Post by Impavidus on 2018-12-27
> **nuttboxer2 said:**
> Not sure what designates a code block here, markdown doesn't seem to work...

Code:
ls -l /home/serviio
ls: cannot access '/home/serviio': No such file or directory

The directory does exist
Code:
cat /etc/passwd
serviio:x:999:999::/home/serviio:**/bin/false**

The fact that this user uses /bin/false as command interpreter also tells us this is not an ordinary user. Those special users that never actually log in often have non-existent home directories.

---

