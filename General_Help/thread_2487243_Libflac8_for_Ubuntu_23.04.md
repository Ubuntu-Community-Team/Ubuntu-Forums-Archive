---
title: "Libflac8 for Ubuntu 23.04"
date: 2023-05-28
forum: General Help
---

### Post by Hewjr100 on 2023-05-28
I need this file to install Gzdoom.  Does anyone know where I can get it.  I only see it in google for Ubuntu Jammy.

Henry

---

### Post by bogaychuk on 2023-06-01
I have the same problem.

---

### Post by bogaychuk on 2023-06-02
I download libflac8 here:
[http://archive.ubuntu.com/ubuntu/pool/main/f/flac/libflac8_1.3.3-2ubuntu0.1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/flac/libflac8_1.3.3-2ubuntu0.1_amd64.deb)
And install it:
sudo dpkg -i libflac8_1.3.3-2ubuntu0.1_amd64.deb
and then installed gzdoom
sudo dpkg -i gzdoom_4.10.0_amd64.deb

---

### Post by Hewjr100 on 2023-06-12
I did that, but did you notice that GzDoom loads real slow, but it does load.

Henry

---

### Post by #&amp;thj^% on 2023-06-12
This one might be better from kinetic
```
wget http://security.ubuntu.com/ubuntu/pool/main/f/flac/libflac8_1.3.4-2_amd64.deb
```
Install the same:
```
sudo dpkg -i libflac8_1.3.4-2_amd64.deb
```
And:
```
sudo dpkg -i gzdoom_4.10.0_amd64.deb
Selecting previously unselected package gzdoom.
(Reading database ... 448720 files and directories currently installed.)
Preparing to unpack gzdoom_4.10.0_amd64.deb ...
Unpacking gzdoom (4.10.0) ...
Setting up gzdoom (4.10.0) ...
Processing triggers for gnome-menus (3.36.0-1.1ubuntu1) ...
Processing triggers for desktop-file-utils (0.26-1ubuntu5) ...
Processing triggers for mailcap (3.70+nmu1ubuntu1) ...

```
If you have used this before then should be good to go.
If not then look in "~/.config/gzdoom" and add any necessary iwads.
```
apt policy  libflac8
libflac8:
  Installed: 1.3.4-2
  Candidate: 1.3.4-2
  Version table:
 *** 1.3.4-2 100
        100 /var/lib/dpkg/status

```
gzdoom:
```

 apt policy gzdoom
gzdoom:
  Installed: 4.10.0
  Candidate: 4.10.0
  Version table:
 *** 4.10.0 100
        100 /var/lib/dpkg/status

```

---

### Post by Hewjr100 on 2023-06-12
Much better.  Thank you.

Henry

---

