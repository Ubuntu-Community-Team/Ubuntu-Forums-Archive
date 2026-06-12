---
title: "Terminal problems"
date: 2008-05-09
forum: General Help
---

### Post by S_U on 2008-05-09
when i enter the command

```
sudo
```

it requires a password but when i try and type it wont let me, in other words as i am pressing keys nothing appears on screen

---

### Post by rohitsb on 2008-05-09
Hi,

The password is hidden on the screen. Rest assured that if you are able to type "sudo", your keyboard is being detected and the password characters are being read from the standard input stream.

This provides an added level of security so that onlookers are not able to see the length of the password. This is similar to other OS such as MVS where security is of prime concern.

---

