---
title: "Login error after power loss"
date: 2012-11-08
forum: General Help
---

### Post by Harry.k on 2012-11-08
Continuation of [http://ubuntuforums.org/showthread.php?t=2081827](http://ubuntuforums.org/showthread.php?t=2081827)
but just to recap, i installed Ubuntu on a 40gb Lacie USB hdd. There was some lightning yesterday, and the power went off while i wasn't around. as  in the other question, it didn't suspend or hibernate. Just went off after the battery died. I boot it today and it takes like forever to reach the login screen. After i enter my pwd, i cant get in. the login screen just stays like that. The cursor can move, and i can switch to tty login. At the tty login, the prompt for username comes, but the screen is flooded by one error message that repeats every second. I can go upto the part where i enter the password and it shows packages to be updated and new mail notifications, but the command prompt never comes. the error message continues to flood the screen. It goes like this:

```
[807.496796] end_request: I/O error, dev sda, sector 22077640
[Different number.Another number] end_request: I/O error, dev sda, sector 22077640
[Different number.Another number] end_request: I/O error, dev sda, sector 22077640
[Different number.Another number] end_request: I/O error, dev sda, sector 22077640
```
and so on. I can access the files on the hdd from my "break glass in case of emergency" backup ubuntu flash  drive and  fsck doesn't show any error. I spent too long customizing it to format it. PLEASE HELP!

---

### Post by Wim Sturkenboom on 2012-11-08
I suggest you try to determine the make of the HD (Western Digital, Seagate, ...) and download that manufacturer's diagnostic tools and burn it to CD; maybe even LaCie has something like that.

Next boot from it to see if it reveals any problems with the HD.

---

### Post by Harry.k on 2012-11-08
I'm downloading seatools for windows. I'll post back in a few minutes with the results.

---

### Post by Harry.k on 2012-11-09
Nope. seatools shows no error.

---

