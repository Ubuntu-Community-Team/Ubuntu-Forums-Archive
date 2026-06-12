---
title: "Sudo confirmation fail"
date: 2014-02-26
forum: General Help
---

### Post by sniper8752 on 2014-02-26
I login as admin2 successfully, and when I run sudo command, it asks my password for the account.  so I type it in, and it rejects it for admin2.  I've tried several times, for several different commands, and have tried logging in and out.  How can I fix this?

[ATTACH=CONFIG]250701[/ATTACH]

---

### Post by jeanjd63 on 2014-02-26
Can you give the return for :
**id**

---

### Post by sniper8752 on 2014-02-27
[ATTACH=CONFIG]250735[/ATTACH]

---

### Post by deadflowr on 2014-02-27
Boot into recovery mode.
Select networking.
When it comes back to the main recovery mode page, go to root shell
enter
```
passwd admin2
```
make a new password, confirm it and type exit.
try it now.

---

### Post by sniper8752 on 2014-02-27
I was able to do a passwd admin2 while logged in as admin2, and change it.  Is that okay?

---

### Post by deadflowr on 2014-02-27
> **sniper8752 said:**
> I was able to do a passwd admin2 while logged in as admin2, and change it.  Is that okay?

Did it complain?

And more over, did it help?

---

### Post by sniper8752 on 2014-02-27
Nope, still says the password is wrong.  Not sure why I can login as admin2, but when it wants the admin2 password for sudo, it fails....

---

### Post by deadflowr on 2014-02-27
Then try the method I posted.
when you enter the recovery mode the file system is mounted read only, but when you enter the enable networking it runs the networking stuff and then remounts the file system read-write.(A rather odd behavior, but it works well this way)
You can also remount the file system with the mount command
enter the root shell and run
```
mount -o rw,remount /
```

This might help
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by jeanjd63 on 2014-02-28
Hello 
What is the contains of the file sudoers ?
If you have a user accepted by sudo you can do :
**sudo  cat  /etc/sudoers**
else in root (as the post #8) :
**cat  /etc/sudoers**

---

### Post by sniper8752 on 2014-02-28
> **deadflowr said:**
> Then try the method I posted.
when you enter the recovery mode the file system is mounted read only, but when you enter the enable networking it runs the networking stuff and then remounts the file system read-write.(A rather odd behavior, but it works well this way)
You can also remount the file system with the mount command
enter the root shell and run
```
mount -o rw,remount /
```

This might help
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
Tried this, and it did not work.  Same problem.

---

### Post by sniper8752 on 2014-02-28
> **jeanjd63 said:**
> Hello 
What is the contains of the file sudoers ?
If you have a user accepted by sudo you can do :
**sudo  cat  /etc/sudoers**
else in root (as the post #8) :
**cat  /etc/sudoers**

I did this in recovery, and this is what I got.
[ATTACH=CONFIG]250762[/ATTACH]

---

### Post by jeanjd63 on 2014-02-28
This seems ok
Have you an another user admin? 
If no you can in root create one :
[B]
adduser *nom_use*r
adduser *nom_user *sudo
[/B]
and try tu use sudo commands with this user

---

### Post by sniper8752 on 2014-02-28
> **jeanjd63 said:**
> This seems ok
Have you an another user admin? 
If no you can in root create one :
[B]
adduser *nom_use*r
adduser *nom_user *sudo
[/B]
and try tu use sudo commands with this user
Perfect - thanks!

---

