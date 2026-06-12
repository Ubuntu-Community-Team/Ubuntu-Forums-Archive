---
title: "export proxy, sick of ding it every time I want to use wget!"
date: 2006-11-10
forum: General Help
---

### Post by Isoss on 2006-11-10
Hey
I am behind a proxy, and I can't use wget unless I run ```
export http_proxy=http://proxy:port 
```
that I must run every time I want to use wget for installing keys or anything else. isn't there a way, edit some file or something so I won't have to do it over and over again?

Thanks

---

### Post by DougC on 2006-11-10
Stick it in your ~/.profile for just your ID or in the /etc/profile as system wide setting.

---

### Post by Isoss on 2006-11-11
can u please tell me how? both files contain bash scripts! I know some bash, but I don't know how you are suggesting I would stick that there!

---

### Post by Isoss on 2006-11-15
Hello! anyone can tell me how I can do that?

---

### Post by skymt on 2006-11-15
Actually, the correct place for it is in "~/.bashrc", which is run whenever you start bash. .profile and /etc/profile are only run when bash is run as a login shell, i.e. when you log in with a VT or ssh, or use a malfunctioning xterm.

---

### Post by KLineD on 2006-11-15
```

gedit ~/.bashrc

```

At the end of the file, paste the line you have. Save it and you are done.

---

### Post by Isoss on 2006-11-21
Hey, thanks, I guess it worked .. but I have to do some tests though .. anyway, I'd like to know what /etc/profile and ~/.bashrc are written for?

thanks

---

### Post by KLineD on 2006-11-23
> **Isoss said:**
> Hey, thanks, I guess it worked .. but I have to do some tests though .. anyway, I'd like to know what /etc/profile and ~/.bashrc are written for?

thanks

.bashrc is the file that gets loaded when bash (the shell) is executed. It stores configuration and you can specify some commands and bash will execute those at startup

---

