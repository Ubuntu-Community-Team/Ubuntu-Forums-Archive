---
title: "Login/User name"
date: 2008-01-13
forum: General Help
---

### Post by ZacW on 2008-01-13
Well my computer caught a virus like a week ago and we had to reformat my computer to save my hard drive and i had windows xp but i didn't have a cd becuase damn computer people didn't give me one and they closed. so i got ubtanbu 7.10 and i installed it and everything 

well there is a big problem my brother forgot his log name and now we can't log into the software

is there a thing i can type to bypass this or change this or something 

thanks for the help

---

### Post by heindsight on 2008-01-13
you can boot into recovery mode and then look at the file /etc/passwd, by doing:
```
grep "[a-z]*:x:[0-9]\{4\}" /etc/passwd
```
this should give you a list of normal users.

If he's forgotten his password as well, you can use the passwd command (while still in recovery
mode), to change his password:
```
passwd username
```
where username is your brother's username.

EDIT:
Note that the above assumes that you can't log in as any user. If you have another user account (with sudo privileges) 
from which you can log in you can execute the same commands in a root terminal instead of having to boot into
recovery mode.

---

### Post by ZacW on 2008-01-13
grep "[a-z]

when i type that in i get a descrivtive error and like read64 -110 or something liek that

---

### Post by ZacW on 2008-01-13
never mind i got it but what do u mean when we type in the grep code u gave us it says grep etc/passwd no such file 

like am i typin it wrong or what

---

### Post by taurus on 2008-01-13
Just look at the output of this command to see what the login name is.

```
ls -la /home
```

---

### Post by ZacW on 2008-01-13
ok i found my user name but when i type the password its not letting me type it i hit enter after i type the user name and then i type it in and nothig comes or i can't type it won't let me type anything

i tryed changing the pw and yet it won't let me type nothing when i type it does nothing

but when i hit enter it does

so idk whats wrong?

---

### Post by jken146 on 2008-01-13
You don't see anything when you type in a password.  That's normal.  Type it in anyway and press Enter.

---

### Post by ZacW on 2008-01-13
ok we log in and we completed the updates and it says cannot stat /etc/X11/X (No such file or directory) , aborting.

---

### Post by jken146 on 2008-01-13
Press Ctrl+Alt+F1 to get to a terminal, then log in and type ```
startx
```

What does that do?

---

### Post by ZacW on 2008-01-13
when do i hit crtl+alt+f1?

---

### Post by ZacW on 2008-01-13
it didn't work got the same error then it said it refused the connection pretty much idk whats wrong

---

