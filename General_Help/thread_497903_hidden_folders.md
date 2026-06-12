---
title: "hidden folders"
date: 2007-07-10
forum: General Help
---

### Post by d_xtremw on 2007-07-10
I Was just wondering is there any way to hide certain folders or at least lock them with passwords to keep ppl out??

---

### Post by fragos on 2007-07-10
Placing a "." as the first character of any folder or file name will it hidden.  Access to any file or folder can be limmited.  Right click any file and select Properties and then the Permissions tab.  If you choose to create a special group you'll need to use System-> Administration-> Users and Groups.

---

### Post by bodhi.zazen on 2007-07-10
Easy way :

Hidden with a . in the front

Keep out with permissions

so ..

```
mkdir .supersecret
chmod 700 .supersecret
```


Hard way ~ Use encryption

[http://www.howtoforge.com/truecrypt_data_encryption](http://www.howtoforge.com/truecrypt_data_encryption)

[http://www.ubuntuforums.org/showthread.php?t=148600](http://www.ubuntuforums.org/showthread.php?t=148600)

---

### Post by d_xtremw on 2007-07-10
aight and if i wanna get it back what wuld i hafta do? using the "." method

---

### Post by pingpongboss on 2007-07-10
You'd just press CTRL+H to temporarily show hidden files/folders in nautilus

---

