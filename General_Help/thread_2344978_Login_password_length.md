---
title: "Login password length"
date: 2016-11-29
forum: General Help
---

### Post by ray42 on 2016-11-29
By default the user password is 8 characters long. How do I change this to six characters?

---

### Post by kingneutron on 2016-12-01
[https://help.ubuntu.com/lts/serverguide/user-management.html](https://help.ubuntu.com/lts/serverguide/user-management.html)
[h=3]Minimum Password Length[/h]
   	By default, Ubuntu requires a minimum password length of 6 characters,  as well as some basic entropy checks. These values are controlled in the  file /etc/pam.d/common-password, which is outlined below.

---

### Post by ray42 on 2016-12-06
Thank you. How do you change permissions for this file?

---

### Post by courtney2 on 2016-12-07
I wouldn't change the permissions, that can open up potential security risks. If you want to edit the file, use the sudo command to edit it so you get super user privileges

---

### Post by ray42 on 2016-12-07
Ok have done this but not allowing me to change password to 6 chars.

```
[COLOR=#333333][FONT=UbuntuMono]password        [success=1 default=ignore]      pam_unix.so obscure sha512 minlen=6[/FONT][/COLOR]
```

Also tried 

```
[COLOR=#333333][FONT=UbuntuMono]password        [success=1 default=ignore]      pam_unix.so obscure sha512 min=6[/FONT][/COLOR]
```

I edit in gedit, then save. Logout and back in, then in  try to change password in setting but still does not allow 6 characters.

Also got an error when editing the file:

```
[FONT=Verdana]sudo gedit /etc/pam.d/common-password[/FONT]
[FONT=Verdana]
[/FONT]
[FONT=Verdana]** (gedit:3914): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-position not supported[/FONT]
```

Despite this it did edit the document.

---

