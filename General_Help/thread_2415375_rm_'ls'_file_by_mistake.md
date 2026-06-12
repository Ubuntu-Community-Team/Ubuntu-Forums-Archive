---
title: "rm 'ls' file by mistake"
date: 2019-03-25
forum: General Help
---

### Post by erised12 on 2019-03-25
I remove my ls file in /bin by mistake. And then I use debugfs to recover the ls file I deleted, but the recoverd file can't be executed./bin/ls: cannot execute binary file: Exec format error. Thanks a lot for helping me.

---

### Post by again? on 2019-03-25
Permissions..
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] ls -l /bin/ls**
-rwxr-xr-x 1 root root 133792 Jan 18  2018 /bin/ls
```


ls is in coreutils
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] dpkg -S /bin/ls**
coreutils: /bin/ls
```

You could try to reinstall...
```
sudo apt install --reinstall coreutils
```

---

### Post by erised12 on 2019-03-25
great thanks, reinstalling coreutils works for me. 
but it seems this "ls" file recovered from debugfs needs more than permission, because I have used chmod 755 previously but it still doesn't work.

> **guber2 said:**
> Permissions..
```
**[COLOR=#006400]glen@Bionic:~$[/COLOR] ls -l /bin/ls**
-rwxr-xr-x 1 root root 133792 Jan 18  2018 /bin/ls
```


ls is in coreutils
```
**[COLOR=#006400]glen@Bionic:~$[/COLOR] dpkg -S /bin/ls**
coreutils: /bin/ls
```

You could try to reinstall...
```
sudo apt install --reinstall coreutils
```

---

### Post by again? on 2019-03-25
Glad it's fixed...but debugfs is beyond my pay grade.

---

### Post by Impavidus on 2019-03-25
Most likely your /bin/ls was already damaged when you recovered it.

---

