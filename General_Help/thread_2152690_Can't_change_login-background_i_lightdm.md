---
title: "Can't change login-background i lightdm"
date: 2013-06-08
forum: General Help
---

### Post by lavhmrps on 2013-06-08
Hey, 

My default background-image in the login-window was gone so I did as I've done before
```

lavhmrps@per:~$ su
  Password:
root@per:/home/lavhmrps# xhost +SI:localuser:lightdm
  localuser:lightdm being added to access control list
root@per:/home/lavhmrps# lightdm -s /bin/bash
lightdm@per:/home/lavhmrps$  gsettings set com.canonical.unity-greeter draw-user-backgrounds 'true'


```

but I get this error message
```

(process:419): dconf-WARNING **: failed to commit changes to dconf: The connection is closed

```

What does it mean, and what can I do to fix it?

Thanks

---

