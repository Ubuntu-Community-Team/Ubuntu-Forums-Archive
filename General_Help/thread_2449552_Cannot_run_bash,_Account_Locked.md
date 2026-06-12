---
title: "Cannot run bash, Account Locked"
date: 2020-08-29
forum: General Help
---

### Post by aboka on 2020-08-29
hi, i got into an issue trying to run a bash file with a new user i created with sudo rights. below is how i create the user-

```

useradd -s /bin/bash -d /home/username/ -m -G sudo username
passwd username
chgrp -c username ./root
chmod g+rwx ./root
sudo usermod --expiredate 1 root

```

I add the uername to root bcoz i need to FTP later to the root folder. I then reboot and login with the new user, and run the command below-
```

aboka@opvnpi:~$ sudo bash sss.txt
sudo: account validation failure, is your account locked?

```

I then re-enable root(sudo usermod --expiredate "" root) and then im able to run 'sudo bash sss.txt' with no issue. It seems like when I run the bash, it will use the root account, and that is why it show Account is locked.

Please advice on how to fix it, as it should be using the new user and not root. Thank you.

---

### Post by aboka on 2020-08-29
sorry guys, my own mistake as there is a 'sudo' inside the bash file. removing it fix the issue ;p

---

### Post by TheFu on 2020-08-29
Using plain ftp wth anything connected to root, uid or group, is a bad idea on many levels.
Push a file elsewhere, then sanity check them before moving/transmuting to the final location. Don't trust uploaded files.

---

### Post by aboka on 2020-08-29
> **TheFu said:**
> Using plan ftp wth anything connected to root, uid or group, is a bad idea on many levels.
Push a file elsewhere, then sanity check them before moving/transmuting to the final location. Don't trust uploaded files.

Thanks for the tips, will cp the file to 'my directory' and then SFTP to download them :)

---

