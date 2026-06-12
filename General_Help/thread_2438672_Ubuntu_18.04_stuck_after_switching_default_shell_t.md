---
title: "Ubuntu 18.04 stuck after switching default shell to zsh"
date: 2020-03-16
forum: General Help
---

### Post by carlo8 on 2020-03-16
Hi, I just installed the zsh by running

    apt-get install ash

and set it as default by

    chsh -s $(which zsh)

After logging out, I got to the login screen, I type my password but the system gets stuck (just people screen, as it were loading forever).
I tried rebooting many times, but the result is always the same. How can I fix it?

---

### Post by TheFu on 2020-03-16
```
apt-get install ash
```
doesn't install zsh.  So, you set a shell to a non-existent shell.
You'll need to boot from a flash "Try Ubuntu" drive, mount the correct partition somewhere (/mnt/ would be good), and manually edit the /mnt/etc/passwd file, correcting the mistake.  Make it - /bin/bash.  Use sudoedit to edit the file or any other system file.

```
$ man -s 5 passwd
```
explains the format of the passwd file in more detail.

---

### Post by Impavidus on 2020-03-16
Assuming you only changed the user's shell, not root's shell, you can also fix this by booting in recovery mode. Or, if there is another user who can use sudo, that user can fix it.

---

