---
title: "[SOLVED] sudoers - no access - help!"
date: 2008-07-07
forum: General Help
---

### Post by prof2019 on 2008-07-07
I am having real trouble editing my /etc/sudoers file. As a newbie, I read man pages, sudo help, visudo, and so forth. But I still am not allowed access to the sodoers file. The system immediately generates a .tmp file of sudoers. Can anyone help or explain?

---

### Post by VMC on 2008-07-07
> **prof2019 said:**
> I am having real trouble editing my /etc/sudoers file. As a newbie, I read man pages, sudo help, visudo, and so forth. But I still am not allowed access to the sodoers file. The system immediately generates a .tmp file of sudoers. Can anyone help or explain?

If you want to view it do this:

```
sudo cat /etc/sudoers
```

What exactualy are you trying to do. To edit type this:

```
gksu gedit /etc/sudoers
```

---

### Post by prof2019 on 2008-07-07
Thanks, I can edit it with gksu but its a read only and I cant save it. I/m trying to alter my passwd req's.

---

### Post by sisco311 on 2008-07-07
try:
```
export EDITOR=nano
sudo -E visudo
```Ctrl+o, Enter = save
Ctrl+x = exit
Read this:[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)
If you have any questions,feel free to ask.

---

