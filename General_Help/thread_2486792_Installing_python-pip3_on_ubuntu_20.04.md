---
title: "Installing python-pip3 on ubuntu 20.04"
date: 2023-05-10
forum: General Help
---

### Post by giobaxx on 2023-05-10
Installing python3-pip in ubuntu 20.04 via apt from the official ubuntu repos we are having some strange behaviour because pip3 is installed in */user/local/bin/pip3* instead of */user/bin/pip3*.


is not a a standard installation because we joined a Domain via an Active Directory (AD) Bridging which enables non-Windows systems to be joined to AD and add some restriction via PAM and we run some hardening but we started to have this issue with ubuntu 20.04.


what may have been changed which cause pip3 to install to */usr/local/bin* at first i thought was a different behaviour from ubuntu 18.04 but testing the same installation with no Domain and no Hardening pip3 is installed on */user/bin/pip3* so we did something but what can be happened? what could have influenced apt to install the package in */usr/local/bin*?

---

