---
title: "Warning unsafe paste"
date: 2019-11-12
forum: General Help
---

### Post by xadder on 2019-11-12
After upgrading to 19.10, I get  a small window "Warning unsafe paste" whenever I try to copy-paste between terminals. This needs extra clicks to "paste anwyay", and I really don't want this. I found one suggestion to turn this off here: [https://www.fosslinux.com/496/how-to-disable-unsafe-copy-paste-warning-while-using-terminal-in-elementary-os.htm]("https://www.fosslinux.com/496/how-to-disable-unsafe-copy-paste-warning-while-using-terminal-in-elementary-os.htm"), but this needs additional package installation (dconf-tools). Is there really no simple way to switch off this new "feature".

---

### Post by milesweb on 2019-11-12
Try to run this command in terminal to disable:  

```
gsettings set org.pantheon.terminal.settings unsafe-paste-alert false
```

  and then this to re-enable it:

  ```
gsettings set org.pantheon.terminal.settings unsafe-paste-alert true
```

---

### Post by xadder on 2019-11-12
Thanks! Well, your suggestion didn't work:

No such schema “org.pantheon.terminal.settings”

but then I realised I should have mentioned I am using Xubuntu, hence xfce4-terminal. When I started to check that I saw the box "Show unsafe paste dialog" in the edit-preferences settings, and that solved my problem :-)

---

