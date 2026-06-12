---
title: "Command line?"
date: 2007-01-03
forum: General Help
---

### Post by haxer on 2007-01-03
Hello i wounder is its possible to list all users on my computer with command from terminal windows?:-k

---

### Post by melancholeric on 2007-01-03
who

nevermind, that just show's who's logged in.

---

### Post by haxer on 2007-01-03
Yeah but i need to see which users are on my computer lost my username cant remembet it :-k

---

### Post by melancholeric on 2007-01-03
cat /etc/passwd | less

edit again: you'll get lots of useless junk with that too, but atleast your username should be there.

---

### Post by haxer on 2007-01-03
Thanks:)

---

### Post by moma on 2007-01-03
Your login name
$ logname 
$ whoami
$ echo $USER 
$ id

All users that are logged in
$ users 

List all defined users that can logon.
$ cat /etc/passwd | awk -F: '$3 == 0 || $3 > 500 { print $0 }'
or 
$ grep /bin/bash /etc/passwd

---

### Post by mcduck on 2007-01-03
all normal users (except root) have their home directories inside /home, so simple 'ls /home' will give you user names ;)

---

### Post by haxer on 2007-01-03
also great thanks :)

---

