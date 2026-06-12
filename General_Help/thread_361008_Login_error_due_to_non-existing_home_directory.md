---
title: "Login error due to non-existing /home directory"
date: 2007-02-13
forum: General Help
---

### Post by Michellangelo on 2007-02-13
Hi everyone!

I just finished installing Ubuntu 6.10. It runs very nice and I played a bit with it. During installation I've been asked to choose an username and a password needed in order to access Ubuntu later. So far, so good. I choose **administrator** as username.
After installation, i was able to login as administrator without any problems. Now it starts my problem:

I wanted to change my username from **administrator** to **admin**, leaving the existing password unchanged. I did that in the menu on top of the screen:*System*, *Preferences*, *Users/User groups* (if I remember well).
The problem is that when I changed my username, Ubuntu asked me if I want to change my /home directory too and it gave me a list of options. When I opened it, **/admin** was listed as an option, so I thought that this is what I should choose since my new username is the same.

Ok so far, I logged out and I've tried to login again with my new username and guess what: ERROR!
This is the exact error message:

```
"Your home directory is listed as: '/home/admin' but it does not appear to exist. Do you want to login with the /(root) directory as your home directory?
It is unlikely anything will work unless you use a failsafe session."
```

If I choose YES I have the following error message after which the whole process starts again:

```
"User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File shoud be owened by user and have 644 permissions. User's $HOME directory must be owened by user and not writable by other users."
```

I've tried to change the session to a failsafe one, but nothing. Same result. It seems to me that I need to rename the **'/home/admin'** to **'home/administrator'** like it was before, or something like that, but I don't know exactly how. All what I know is that I need to use the *$sudo* and then *chown* commands after I reboot in recovery mode.

Could you please guys poit me into the right direction? 
I would much appreciate if you could just tell me what to do.

Thanks a lot!

---

### Post by Maestro23 on 2007-02-13
This thread will help you: [http://www.ubuntuforums.org/showthread.php?t=352547&highlight=User%27s+%24HOME%2F.dmrc+file+is+being+ignored.+This+prevents+the+default+session+language+from+saved.+File+shoud+be+owened+by+user+have+644+permissions.+%24HOME+directory+must+other+users.%26quot%3B%26quot%3B](http://www.ubuntuforums.org/showthread.php?t=352547&highlight=User%27s+%24HOME%2F.dmrc+file+is+being+ignored.+This+prevents+the+default+session+language+from+saved.+File+shoud+be+owened+by+user+have+644+permissions.+%24HOME+directory+must+other+users.%26quot%3B%26quot%3B)

---

### Post by Michellangelo on 2007-02-14
Thanks Maestro!

I've seen the thread before and I've tried it myself but something's not working. Below I'm quoting a possible solution from the thread that you sent me to:

[I]at the login point, choose failsafe terminal as your session. type in '/home' so that you are just outside your home directory. 
right, i'm going to assume that your username is DeeK for this purpose.

change your username to what it should be (ie DeeK).

now type in 'sudo chown DEEKEEK DeeK' (NOTE: DEEKEEK should say DeeK semicolon DeeK, but i can't write that in this forum because the "" is substituted for a stupid smilie). then type in 'sudo chmod 700 DeeK'.

now go back to your login point and login normally.

the dmrc file error is nothing to do with th the dmrc file. its because your home directory permissions have somehow got mixed up.

the important thing to remember is that your home directory (ie /home/DeeK) must have the correct permission to allow you to access it.[/I]


When I try to do that (to type in /home) it just tells me right from the start that 

```
/home is a directory
```

and that's it. If I try with
```
sudo chown test:test
```
it tells me that an operand is missing after **test:test**
Then I've tried to add a new user just like DeeK did:
```
sudo useradd -m -G users -s /bin/bash test
```
but after that I have no choices of a password or something similar. I then type **exit** and then I restart the Ubuntu. When back into the normal login screen what am I supposed to login as: **users**, **test**, etc? And if so, since I didn't choose a password, what's my password?

Honestly, I don't really get it! How can I make the user **admin** to log in using the **/administrator** directory instead of the non-existing **/admin**???

Anyone had the same problem? Maybe I'm new, but why Ubuntu gave me the choice of a non-existing directory in the first place?

Please help me!
Thanks a lot!

---

