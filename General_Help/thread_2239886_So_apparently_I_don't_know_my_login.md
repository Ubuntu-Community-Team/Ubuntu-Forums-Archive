---
title: "So apparently I don't know my login"
date: 2014-08-16
forum: General Help
---

### Post by Andrew_Vann on 2014-08-16
I go to boot up my shiny new 14.04 laptop today, and when I log in, the background displays, but nothing else shows up. I search online and see that Unity could have been disabled somehow, and I can fix it via ctrl+alt+F1. I try this, and it asks me for my login. I try using the name above my password from the normal login in, and it tells me incorrect login. I try using the name of my computer, and I get incorrect login again. I know that it's the right password, however. Am I just an idiot who forgot his username and has to do a full re-install or is there some way to fix this without having to do that? I've tried logging in and pulling up the terminal from the blank screen, but I can't get it to pull up.

---

### Post by TheFu on 2014-08-16
You can hack into the system with a live-CD/boot and look at the password file - /etc/passwd - to see the userid.  Be certain to use that and NOT THE FULL NAME part.  Windows-people seem to have trouble with this.

logins are 
* lowercase, 
* 1 word, 
* no spaces

---

### Post by coffeecat on 2014-08-16
I think it's more likely that you are putting in your password wrongly, but whichever, have a look at this link:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

It shows you how to check your username as well as reset the password. Basically, once you are at the root prompt in the recovery shell:

```
ls /home
```

If that shows you were using the correct username, then simply reset the password from the recovery root prompt. I'll retype the commands shown in that link, because some people misread the first one:

```
mount -o rw,remount /
passwd *yourusername*
```

No space between rw, and remount in the first, and substitute your correct username for *yourusername*

---

### Post by Imperium Guard on 2014-08-16
> **TheFu said:**
> You can hack into the system with a live-CD/boot and look at the password file - /etc/passwd - to see the userid.  Be certain to use that and NOT THE FULL NAME part.  Windows-people seem to have trouble with this.

logins are 
* lowercase, 
* 1 word, 
* no spaces
Yep, once you boot into the live cd, you can type: ```
cat /etc/passwd
``` You're looking for something like this: ```
user1:x:1000:1000:User's Full Name,,,:/home/user1:/bin/bash 
```, user1 is the login.

---

### Post by Andrew_Vann on 2014-08-16
Thanks. Got it all resolved. Password was right, didn't have the right username. I stopped using Ubuntu at 12.10, and then I've used windows 7 for a while. I'm just trying to find my feet again. Thanks all.

---

### Post by TheFu on 2014-08-17
Yes - "John Smith" is NOT a valid userid, but "jsmith" is.

Ran into this with a corporate Microsoft Domain Admin - it was 2nd nature for him to use fname/lname and never considered that to be an issue.  I hacked into the system and reset the password 3 times during a LUG meeting - finally, I watched him type "John Smith" and made the correction.

Sometimes we forget what it was like in the beginning and we forget how our history leads us to believe things that are not true - regardless of our beliefs. I insert "my reality" all the time. ;)

---

