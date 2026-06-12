---
title: "PATH saved empty - commands dont work any more"
date: 2016-07-16
forum: General Help
---

### Post by istvan5 on 2016-07-16
I edited /etc/environment 
from 
```
PATH="/home/istvan/apps/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games"
```
and saved with the content
```
PATH=""
```

-> now, I have the big problem, no command works any more (except "avconv" I wanted to see wich library is loaded from)
because the PATH is empty... it was a big mistake..
So I cannot open and correct the PATH=""

how can I solve this ? Should I just restart ? Or it would be a bad idea ?

---

### Post by istvan5 on 2016-07-16
I can navigate to directories with command "cd",
but that's it, now I must somehow navigate to the directory where "sudo", "leafpad" are inside and try the command in this directory ?

---

### Post by steeldriver on 2016-07-16
Just set it back - using the full path to sudo e.g.

```

/usr/bin/sudo nano /etc/environment

/usr/bin/sudo vi /etc/environment

```

---

### Post by DuckHook on 2016-07-16
You just have to invoke each app by using its full path name:```
/usr/bin/sudo /bin/nano /etc/environment
```...then add the missing path values, log out, log back in.

EDIT

ninja'd by steeldriver

@steeldriver

In this case, both *nano* and *vi* must be called with full path too.

---

### Post by istvan5 on 2016-07-16
Thank you for your message !!

I was inside  ~/bin and that could help me... but I don't know how.. 
first "ls" worked, and I tried to use "export PATH" which did not work,
then I tried "sudo", now it worked, and then I tried "leafpad" and this worked too..
I am so happy now ..

---

### Post by steeldriver on 2016-07-16
> **DuckHook said:**
> 
@steeldriver

In this case, both *nano* and *vi* must be called with full path too.

Why? doesn't sudo use its own secure_path? (FWIW I tested my answer after unsetting my own path)

---

### Post by DuckHook on 2016-07-16
> **istvan5 said:**
> Thank you for your message !!

I was inside  ~/bin and that could help me... but I don't know how.. 
first "ls" worked, and I tried to use "export PATH" which did not work,
then I tried "sudo", now it worked, and then I tried "leafpad" and this worked too..
I am so happy now ..Now you have completely confused me. You may just have local paths defined. ~/bin is not accessible to any other users except you and is not a default directory in any case. You should follow steeldriver's and my steps and restore your proper /etc/environment file by populating it with the right values.

---

### Post by istvan5 on 2016-07-16
> **DuckHook said:**
> You just have to invoke each app by using its full path name:```
/usr/bin/sudo /bin/nano /etc/environment
```...then add the missing path values, log out, log back in.

EDIT

ninja'd by steeldriver

@steeldriver

In this case, both *nano* and *vi* must be called with full path too.

Hi ! Thxxx

Do I really need to "logout" and "login" again ?

---

### Post by DuckHook on 2016-07-16
> **steeldriver said:**
> Why? doesn't sudo use its own secure_path? (FWIW I tested my answer after unsetting my own path)Of course. You are right. I forgot that, once sudo is invoked, you are no longer in the user's old environment. :)

---

### Post by DuckHook on 2016-07-16
> **istvan5 said:**
> Hi ! Thxxx

Do I really need to "logout" and "login" again ?Yes. In fact, you may need to reboot. Path variable will change immediately if you export the variable, but not the /etc/environment file.

---

### Post by istvan5 on 2016-07-16
my PATH looks like, this was the original, I copy&paste away, before I changed it...

> PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games"

---

### Post by DuckHook on 2016-07-16
> **istvan5 said:**
> my PATH looks like, this was the original, I copy&paste away, before I changed it...You should now be good to go.

*Please mark thread **solved** using the thread tools at top of thread.*

---

