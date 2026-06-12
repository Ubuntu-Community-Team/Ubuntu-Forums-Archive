---
title: "Users can su to other users"
date: 2005-10-02
forum: General Help
---

### Post by ultramancool on 2005-10-02
I'm stuck here with a nice security vulnerability: I've given some of my freinds ssh access to my box (I'm using SSH private keys so it doesn't matter if they know my password, they don't have my key :D). Unfortunately some of my freinds also know my password. The problem is here, my freinds could su to my account then sudo from it to get root access. There's no wheel group on ubuntu :( Is there another group I'm supposed to use? Can someone please help me here.

---

### Post by dcraven on 2005-10-02
Uhmm.. Change your password, and don't give it out to your friends. That kind of defeats the purpose of a password. As your user, type this at a command prompt.
```
passwd
```

HTH,
~djc

---

### Post by mlomker on 2005-10-02
> The problem is here, my freinds could su to my account then sudo from it to get root access. 

Give root its own password:

```

sudo passwd root

```

---

### Post by ultramancool on 2005-10-02
[QUOTE=dcraven]Uhmm.. Change your password, and don't give it out to your friends. That kind of defeats the purpose of a password. As your user, type this at a command prompt.
```
passwd
```
HTH,
~djc[/QUOTE]

This is not the answer I was looking for! Passwords can easily suffer brute force attacks! I really don't care that my friends know my password, I would like my box to be secure w/o this!  I found the PAM config file for su in /etc/pam.d/su so i uncommented (and added to) the necessary line:
auth       required   pam_wheel.so group=wheel debug
Unfortunately this failed... However when i told it that all the users in that group could access w/o password, It worked w/o pass. But it still let all the other users in w/pass. Please help me here.

---

### Post by dcraven on 2005-10-02
I gotta say I'm not sure what you want. You want to secure your box, and give out your passwords. Hopefully someone else has a solution, because I don't get it. I'll keep an eye on this thread because I might learn something too.

~djc

---

### Post by matthew on 2005-10-02
Here's a thought: give yourself a new, difficult to guess password. Make sure it does not use any words found in a dictionary, that it has at least one number and/or other symbol somewhere other than the beginning or the end, and that it is at least 6 characters long (8 is better). Then create a new account for your friends to use when they ssh into your computer--an account that has limited access and does not have sudo rights.

Seriously, get in the habit of using better, difficult to guess passwords (not all passwords are really that vulnerable to brute force attacks) and stop giving out your password...or, just get used to the fact that anyone who has your password will have access to sudo and your whole machine.

---

### Post by ultramancool on 2005-10-02
Ok I'll put it this way: I don't like passwords. :D Hell I could do without them if my box had this (standard) security feature! I've created a new thread with a more proper version of this question.

---

### Post by matthew on 2005-10-02
[quote=matthew]Then create a new account for your friends to use when they ssh into your computer--an account that has limited access and does not have sudo rights.[/quote]
It looks like you may have missed this part of my comments. If you ***create a special account just for your friends*** to use when they log on you can limit their access and still have your account/computer secure.

---

### Post by nocturn on 2005-10-03
[QUOTE=ultramancool]Passwords can easily suffer brute force attacks! [/QUOTE]

Yes, but only if you obtain the hash.  If you do not type your password over an insecure channel (telnet) or give users read access to /etc/shadow they cannot brute force your password.

But, do yourself a favour, choose a very good password (at least 10-12 in length, mixed case with numbers and signs).

---

