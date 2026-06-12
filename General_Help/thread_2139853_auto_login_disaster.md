---
title: "auto login disaster"
date: 2013-04-28
forum: General Help
---

### Post by nevle on 2013-04-28
Hi, recently upgraded to 12.10 and decided to have auto login to my computer. Went to settings>users put in my password and then hit change password and entered no password. Shut down restarted auto logged in all good BUT the computer no longer recognises ANY password, cant change it back, cant sudo, locked out. Rebooted to recovery mode and tried to change through root shell, computer says nooo.. "authentication token manipulation error" password unchanged. Any suggestions please.

---

### Post by deadflowr on 2013-04-28
You'll need to reset your password

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by nevle on 2013-04-28
followed those instructions- received error "authentication token manipulation error". password unchanged.

---

### Post by nevle on 2013-04-28
Hi this link
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
has the command- 
mount -o rw, remount /
which didn't work for me
mount -rw -o remount /
did work for me so my password has been reset back to what it was.
thanks to all, problem fixed.

---

### Post by coffeecat on 2013-04-28
> **nevle said:**
> Hi this link
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
has the command- 
mount -o rw, remount /
which didn't work for me

Have another look. You put a space between "rw," and "remount" which should not be there.

---

### Post by nevle on 2013-04-28
OOps,sorry my mistake., thanks for your help.  I think it was the comma that threw me.

---

