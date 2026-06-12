---
title: "Sudo and .bashrc"
date: 2008-05-23
forum: General Help
---

### Post by theodorekon on 2008-05-23
I have exported a few PATHs in my user .bashrc so as to run some programs without having to give the full path and it works fine. Although I have also put the same PATHs in my root .bashrc it doesn't seem to find the PATHs given there when I run the commands with sudo. Is there a special .bashrc for sudo or is anything else I can do??

Thanks in advance

---

### Post by kerry_s on 2008-05-23
hmmm, not sure what sudo uses. i think there's /etc/bash.bashrc which is suppose to be global.

---

### Post by mali2297 on 2008-05-23
I suggest that you set the PATH variable in **/etc/profile**.

---

### Post by theodorekon on 2008-05-23
I'm afraid none of the above worked. Any other suggestions??

---

### Post by pointone on 2008-05-23
```
sudo -E <command>
```

...to preserve the environment.

---

### Post by n-alexander on 2008-05-23
> **theodorekon said:**
> I have exported a few PATHs in my user .bashrc so as to run some programs without having to give the full path and it works fine. Although I have also put the same PATHs in my root .bashrc it doesn't seem to find the PATHs given there when I run the commands with sudo. Is there a special .bashrc for sudo or is anything else I can do??

Thanks in advance

sudo doesn't use root's bashrc. There is /etc/environment, which is global, if you don't mind other users sharing that setting

---

