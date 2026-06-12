---
title: "Different sudo passwd ?"
date: 2007-01-23
forum: General Help
---

### Post by anaconda on 2007-01-23
Is it possible to have normal password for logging in and something else for sudo password?

I can't help other people seeing my sudo password, because I constantly have people standing behind me when I write my sudo password...

The only way I can think of is to enable root account, and use "su" which would then ask root password.. and because graphical root logins are not allowed it wouldn't matter that much that other people know my root password....  or to have root terminal always open in case I need root powers..

So is it possible to have different sudo password than the main one?  If not then it is a big security risk..

---

### Post by bodhi.zazen on 2007-01-23
> **anaconda said:**
> Is it possible to have normal password for logging in and something else for sudo password?

I can't help other people seeing my sudo password, because I constantly have people standing behind me when I write my sudo password...

The only way I can think of is to enable root account, and use "su" which would then ask root password.. and because graphical root logins are not allowed it wouldn't matter that much that other people know my root password....  or to have root terminal always open in case I need root powers..

So is it possible to have different sudo password than the main one?  If not then it is a big security risk..

You have a big security risk either way :(

But, yes the way to do what you are asking is to enable root by setting a password.

```
sudo passwd
```

You now can su to root, and if you like disable or limit sudo.

BUT YOU NEED TO SOLVE YOUR SOLVE> other people seeing my sudo password, because I constantly have people standing behind me when I write my sudo password...

Modify your work environment, whatever, but this is a big problem.

And DO NOT> have root terminal always open in case I need root powers..

Always use root as little as possible and always exit the root shell immediately after use. You should not need root access all that much ???

---

### Post by yopnono on 2007-01-23
> **anaconda said:**
> Is it possible to have normal password for logging in and something else for sudo password?

I can't help other people seeing my sudo password, because I constantly have people standing behind me when I write my sudo password...

The only way I can think of is to enable root account, and use "su" which would then ask root password.. and because graphical root logins are not allowed it wouldn't matter that much that other people know my root password....  or to have root terminal always open in case I need root powers..

So is it possible to have different sudo password than the main one?  If not then it is a big security risk..

What you really want is to set the sudo password to something different from you user password?
sudo pass = abc123
user pass = 123456

---

### Post by anaconda on 2007-01-23
> **yopnono said:**
> What you really want is to set the sudo password to something different from you user password?
sudo pass = abc123
user pass = 123456

Yep. That is true. Is it possible?

And thanks "bodhi.zazen", but I can't change the enviroment. (it would be the best solution)  And if there isn't any other solution I will enable my root account and use it instead of sudo...

---

