---
title: "Username"
date: 2008-03-17
forum: General Help
---

### Post by Winston Forde on 2008-03-17
I lost both my username and password.  I now know how to get my passwpord back.   But please tell me about getting the username as well!!   Please!!

---

### Post by Rocket2DMn on 2008-03-17
You can list the users in the home directory.  Boot into the recovery mode kernel at the GRUB screen and type out 
```
ls /home
```
It will list the folders of all the users on your machine.  If you need to change the password, from that same prompt run
```
passwd *username*
```
Then you can reboot normally with
```
reboot
```

---

### Post by nick_h on 2008-03-17
By default the first user you create will have the uid of 1000, so you can find it using:
```
cat /etc/passwd | grep 1000 | cut -d: -f1
```

---

### Post by aysiu on 2008-03-17
This should help you:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by bodhi.zazen on 2008-03-17
> **nick_h said:**
> By default the first user you create will have the uid of 1000, so you can find it using:
```
cat /etc/passwd | grep 1000 | cut -d: -f1
```

No need to cat -> pipe to grep

```
grep 1000 /etc/passwd | cut -d: -f1
```

---

### Post by nick_h on 2008-03-17
> No need to cat -> pipe to grep
Quite right.  It's just the way I built up the command - the cat first to look at the file,  then the grep to get the line and finally I added the cut to just return the username field.  I suppose I should have taken the time to simplify it afterwards. :)

---

