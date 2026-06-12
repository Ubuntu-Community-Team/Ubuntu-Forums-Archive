---
title: "impossible to create a new user"
date: 2019-02-27
forum: General Help
---

### Post by Gingalone on 2019-02-27
On Ubuntu 16.04 I am trying to add a no-sudo new user.
Firstly I tried 
```
sudo useradd Val
```I was not asked for a pw for the new user and no any other command response, just the prompt.
Then I log out from my account and tried to log in the Val (the just created user) account but the login shell asked for a password... Which password??? I tried just to hit return and got a "wrong password" warning... SO the problem was to change or set a new password for the new user (apparently there was already an unknown one created by the system...) I looked around but all the help and hints were on change the password of a user who was already able to login...
So I deleted the Val new user (the command deluser worked!) and searched again on forums ecc. and, upon advice, tried the command adduser and this time I got; ```
sudo adduser Val
adduser: Please enter a username matching the regular expression configured
via the NAME_REGEX[_SYSTEM] configuration variable.  Use the `--force-badname'
option to relax this check or reconfigure NAME_REGEX.
``` Name Regex? Badname? It looks Ubuntu doesn't like the name Val (but I tried other names with no avail)... maybe Ubuntu doesn't want uppercase letters in usernames? But that doesn't make any sense!
 What about? I suspect to miss something, but why is it so difficult to create a new user in Linux???
Thank you for any help!

---

### Post by Frogs Hair on 2019-02-27
Is that an upper case or lower  case v ?

---

### Post by HermanAB on 2019-02-28
On UNIX systems, never use uppercase in names - including user names, host names and domain names.

One reason being that it a domain name is defined in lower case, its use will be case insensitive.  That is why google.com, Google.Com and GoOgLe.CoM will all resolve.  If the name is defined with even just ONE upper case character, then it must always be written that way.  

I can't imagine that Google would have been very popular as a search engine if it was defined as GoOgLe.CoM.

---

### Post by Gingalone on 2019-02-28
OK; I see... thank you HermanAB and Frogs Hair, no capital letters... New user must be val and NOT Val. Solved, even if I would have preferred Val...
Ciao!

---

