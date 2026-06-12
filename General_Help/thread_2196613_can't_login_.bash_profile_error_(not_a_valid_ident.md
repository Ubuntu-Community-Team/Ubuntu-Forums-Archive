---
title: "can't login .bash_profile error (not a valid identifier)"
date: 2013-12-30
forum: General Help
---

### Post by paula-sarkis on 2013-12-30
I'm new to ubuntu so please bear with me. 

I cannot login to ubuntu though my username is correct. After I enter the password, the screen goes black and then the login page appears again. Note that if I type a wrong password I get a message saying that the password I entered is incorrect.

It all started when I created the file .bash_profile.

I typed ctrl + alt + f1. I was able to login and I received the following message:

-bash: export: 'PATH:/usr/local/bin:/usr/bin:/usr/sbin:/sbin' : not a valid identifier.

If I delete the file .bash_profile will I be able to login? If yes, then I will delete it but I need the right commands.


Note that I am using ubuntu 12.04.

Thanks

---

### Post by QIII on 2013-12-30
[I]Moved to [B]General Help.


[/B][/I]The Forum Feedback & Help area is for questions about using the Forum itself.

---

### Post by deadflowr on 2013-12-30
> [COLOR=#000000]If I delete the file .bash_profile will I be able to login? If yes, then I will delete it but I need the right commands.[/COLOR]

Probably, did you do anything else?
And to remove try
```
rm .bash_profile
```
of course not knowing what's going on, I might try renaming the file something else, just in case
```
mv .bash_profile joesburningtires
```
or something like that.
That way, if it wasn't the problem of the login I can rename it back.
I think most people would change it to something normal, like .bash_profile.bak, but I like having fun.

---

### Post by paula-sarkis on 2013-12-30
Thanks for the reply deadflowr.

Do you think if I login from ctrl + alt + f1 I can remane the file?

---

### Post by paula-sarkis on 2013-12-30
[COLOR=#000000]Thanks for the reply deadflowr.[/COLOR]

[COLOR=#000000]Do you think if I login from ctrl + alt + f1 I can remane the file?[/COLOR]

---

### Post by deadflowr on 2013-12-30
Yeah, login as normal in the console session (ctrl+alt+F1)
also make sure you are in the home folder
if you use
```
pwd
```
it should show where you are
normally that's 
/home/username(username being the username for you)
you can also remove or move/change using the files full path, if you want
example
```
rm /home/joe/.bash_profile
```
but if you're in the home folder, the earlier approach would work.

---

### Post by paula-sarkis on 2013-12-30
I was able to rename the file. But still, I'm facing the same problem. I cannot login.

---

