---
title: "I am not able to enter into my account..."
date: 2007-09-27
forum: General Help
---

### Post by madhu542 on 2007-09-27
Hai...

      I am a ubuntu dapper user. In the morning when I start my system after sometime suddenly system hangs. From that onwords I am not able to login into my account , it is giving me the message as "YOUR ADMININSTATOR HAS DISABLED YOUR ACCOUNT".

     Could any plz help me how to access my account.

Thanks.

---

### Post by jamvegan on 2007-09-27
The user in [this thread]("http://ubuntuforums.org/showthread.php?t=555221") discovered that their login shell had somehow been changed to /bin/true, which resulted in them getting the same error message as you.  If you can boot into recovery mode you can check your login shell with the following command:
```
grep username /etc/passwd
```
(where you replace "username" with your actual username.  The output should look something like this:
```
jeff:x:1000:1000:J M,,,:/home/jeff:/bin/bash
```
You'll notice that the very last thing on that line is /bin/bash.  This is Ubuntu's default shell, but your entry could be something else if you use a different shell.  However, if the last field is not a shell at all, that's your problem.  You can fix it by (carefully, after making a backup) editing the line in /etc/passwd.

---

### Post by madhu542 on 2007-09-27
> **jamvegan said:**
> The user in [this thread]("http://ubuntuforums.org/showthread.php?t=555221") discovered that their login shell had somehow been changed to /bin/true, which resulted in them getting the same error message as you.  If you can boot into recovery mode you can check your login shell with the following command:
```
grep username /etc/passwd
```
(where you replace "username" with your actual username.  The output should look something like this:
```
jeff:x:1000:1000:J M,,,:/home/jeff:/bin/bash
```
You'll notice that the very last thing on that line is /bin/bash.  This is Ubuntu's default shell, but your entry could be something else if you use a different shell.  However, if the last field is not a shell at all, that's your problem.  You can fix it by (carefully, after making a backup) editing the line in /etc/passwd.

Thanks for ur reply, 

I am getting this msg at the starting point, when GUI screen is loading. when I type the username and passwd it again comes to the login prompt giving this msg.

---

