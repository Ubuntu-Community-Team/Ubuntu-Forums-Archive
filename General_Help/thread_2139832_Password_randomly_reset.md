---
title: "Password randomly reset"
date: 2013-04-27
forum: General Help
---

### Post by ajw3 on 2013-04-27
I have a Ubuntu 12.10 Dell Inspiron 6000, and my parents know the password, so I have to ask them whenever I want to get an application. Today, I asked my dad to type in the password to get it, and it said that his password was wrong. He tried two more times, then got my mom to put in the password. Her's also did not work. They went to the user accounts, and tried to unlock it so that they could change the password, but that did not accept the password. I tried terminal, and a bunch of other things, but nothing would accept the password. The password has never been changed on the computer, so I am really wondering what happened, and how I can fix it.

---

### Post by lisati on 2013-04-27
The first thing to check is to see if you've accidentally activated caps-lock. If that doesn't help there are options which we can guide you through.

---

### Post by ajw3 on 2013-04-27
I got them to type in the password with and without caps lock turned on, and neither one worked.

---

### Post by nevle on 2013-04-28
Hi I am also having password problems (seems i dont have one!) This link is supposed to show you howto re set your password-
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
Didn't work for me but you may have more luck.

---

### Post by nevle on 2013-04-28
OK, tried again with link above and by changing the mount command to
mount -rw -o remount /
got it to work.
hope this helps

---

### Post by ajw3 on 2013-04-28
Yes it did. Thank you!

---

