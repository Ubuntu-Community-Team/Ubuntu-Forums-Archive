---
title: "Probleme about changing password"
date: 2018-08-21
forum: General Help
---

### Post by raprezy on 2018-08-21
Hello
I come to you for help, I wanted to change my password (because I do not remember it anymore), I used the system recovery as  saying internet, I used the boot system with the commands : passwd "username", and asking me for the new password Unix, when I type something nothing is shown (they said it's normal) but suddenly when I try another password : authentication token Manipulation error

Please help me

---

### Post by steeldriver on 2018-08-21
Hello and welcome to the forums

"authentication token Manipulation error" usually means the system can't write the new password hash to the shadow file

If you are using the recovery shell, make sure that you remount the filesystem in read-write mode before trying to change the password:

```

mount -o rw,remount /

```

There are clear visual instructions here: [How to reset your password in Ubuntu](http://www.psychocats.net/ubuntu/resetpassword)

HTH

---

