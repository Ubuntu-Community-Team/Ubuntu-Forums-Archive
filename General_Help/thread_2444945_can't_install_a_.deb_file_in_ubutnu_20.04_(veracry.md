---
title: "can't install a .deb file in ubutnu 20.04 (veracrypt)"
date: 2020-06-06
forum: General Help
---

### Post by ronjjjg8885 on 2020-06-06
hello
i don't know what is the problem.
i've downloaded this file:
[https://launchpad.net/veracrypt/trunk/1.24-update4/+download/veracrypt-1.24-Update4-Ubuntu-20.04-amd64.deb](https://launchpad.net/veracrypt/trunk/1.24-update4/+download/veracrypt-1.24-Update4-Ubuntu-20.04-amd64.deb)
but i don't understand how to install it.

if you can help - thanks!
attached is what i get in the terminal[ATTACH=CONFIG]286117[/ATTACH]

---

### Post by ronjjjg8885 on 2020-06-06
is this the solution?
[https://itsfoss.com/cant-install-deb-file-ubuntu/](https://itsfoss.com/cant-install-deb-file-ubuntu/)

---

### Post by CelticWarrior on 2020-06-06
```
sudo dpkg -i <package>
```

---

### Post by vmpx on 2020-06-18
Go to the folder where you have downloaded the file and execute:
```
sudo apt install ./veracrypt-1.24-Update4-Ubuntu-20.04-amd64.deb
```

---

### Post by ronjjjg8885 on 2020-06-19
thanks
at the end the link helped me to solve this

---

