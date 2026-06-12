---
title: "Login fails after changing /etc/environmet and /etc/profile"
date: 2013-06-20
forum: General Help
---

### Post by msgeo on 2013-06-20
Hi everyone!
I’m working on some programs that need some environment variables to be defined.
So I’ve changed /etc/environment and also etc/profile.
But unfortunately I wrote something wrong there.
Now on the login page when I type my password it goes black and then returns to the login page.
Login with any user including guest fails.
I can login with crtl+alt+f1 but have no idea what should I do there.
May you please help me?
Thanks.
[http://nec.besaba.com/up/a7cdfad1a5aa.jpg](http://nec.besaba.com/up/a7cdfad1a5aa.jpg)

---

### Post by lykwydchykyn on 2013-06-20
If a user's X session crashes, the errors are typically recorded in ~/.xsession-errors, so log in from the terminal and have a look at that file to see what the problem might be.

---

### Post by msgeo on 2013-06-20
Thanks.
But I can&#8217;t use any command in terminal
It just keep saying that '' the command could not be loaded because e.g. '/bin' is not included in the PATH environment''
 
As I sad I&#8217;ve changed environment and profile in etc folder and I&#8217;ve also added some new addresses into PATH 
Now I want to restore those files or at least make environment file empty.

---

### Post by steeldriver on 2013-06-20
The default /etc/environment just contains the following afaik

```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
``` 

To fix it, you should be able to do

```

export PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"

echo PATH=\"/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games\" | sudo tee /etc/environment

```

(the first command just gives you a working path so that you can execute the second command without specifying /bin/echo, /usr/bin/tee etc) 

To fix your .profile, you can get a fresh copy from /etc/skel

```

cp ~/.profile ~/.profile.bak
cp /etc/skel/.profile ~/.profile

```

---

### Post by msgeo on 2013-06-21
> **steeldriver said:**
> 

```

export PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"

echo PATH=\"/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games\" | sudo tee /etc/environment

```

(the first command just gives you a working path so that you can execute the second command without specifying /bin/echo, /usr/bin/tee etc) 

[/CODE]

**WOW**...thank you. it worked =D>:popcorn:

---

