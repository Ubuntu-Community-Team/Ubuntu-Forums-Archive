---
title: "Get Ubuntu Version"
date: 2007-09-01
forum: General Help
---

### Post by cyracks on 2007-09-01
Hi,

I'm writing a program and for the program to work correctly I need to get ubuntu version. The only file on my disk which gives me just that is located at /etc/issue. Man pages tells me this file is "pre-login message and identification file". So my question is; where is written which version of ubuntu the user is running.

regards

---

### Post by SPr on 2007-09-01
> **cyracks said:**
> Hi,

I'm writing a program and for the program to work correctly I need to get ubuntu version. The only file on my disk which gives me just that is located at /etc/issue. Man pages tells me this file is "pre-login message and identification file". So my question is; where is written which version of ubuntu the user is running.

regards

Hi,

try either
uname -a
or
cat /etc/lsb-release

HTH

---

### Post by cyracks on 2007-09-01
Thx for quick reply. /etc/lsb-release is probably what I need.

---

