---
title: "Password none now I can't authenticate"
date: 2014-06-06
forum: General Help
---

### Post by herman2 on 2014-06-06
I was given a computer with a new install of Zorin.  I accidentally changed the password to none, now I can't change it back.  And I can't authenticate, either.

I did some research and found this solution, but it didn't work.  At boot up I selected  recovery mode.  Then from the menu that came up I chose "root".  I then entered the command

```
mount -rw -o remount /
```

Then I typed in 

```
passwd <username>
```

and got the response that <username> doesn't have a password.

I also tried

```
passwd
```

which allowed me to enter a new password and it was accepted, but the problem still persists.

I pretty new to Linux, so apparently I know just enough to be dangerous.

---

### Post by deadflowr on 2014-06-06
I have never found that mount command to work right.:confused:
Try this one
```
mount -o rw,remount /
```
run
```
ls /home
```
to verify the right username.
the do the passwd command.
I think if you run simply passwd without a username it defaults to give root a password, which won't help.
So remember to add your username.

---

### Post by herman2 on 2014-06-06
```
ls /home
```

revealed that the first letter of the username is not capitalized.  That was my problem all along.  Thanks.

---

