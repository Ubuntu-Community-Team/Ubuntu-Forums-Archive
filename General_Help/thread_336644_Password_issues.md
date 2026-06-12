---
title: "Password issues"
date: 2007-01-11
forum: General Help
---

### Post by Jekento on 2007-01-11
i have been having tons of password and user name issues with ubuntu. Such as sometimes my password wont work at login, and i make sure i am typing it right dont worry. if i restart sometimes my password works. or in the terminal i type in su or sudo, and it asks for a password. the password doesnt work, so i havent been able to install anything because i cant get root. the password to log in as root would be the same as my user password wouldnt it?am i just going crazy? thanks guys.

---

### Post by firebadger on 2007-01-12
Perhaps you have a dodgy key on your keyboard that you need for your password.

---

### Post by aysiu on 2007-01-12
Can you explain what you mean by "password doesn't work"? Does it actually say your password is incorrect? In the terminal there is no visual feedback when you're entering your password. It's still taking your password, though.

Also, you may be typing your password correctly now, but is it possible you didn't type it correctly when you first set it up? Try resetting the password by rebooting into recovery mode and typing ```
passwd jekento
reboot
```

Finally, you cannot log in as root by default (this can be changed). Read more here:
[http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)

---

### Post by Jekento on 2007-01-12
Yea i did realize it doesnt show the password in the terminal. but yes, it actualy tells me it is wrong although i just logged into linux with the same password. 

Thanks for a reply by the way, highly appretiated.

---

