---
title: "firefox only runs with sudo [Resolved]"
date: 2007-02-09
forum: General Help
---

### Post by r.stiltskin on 2007-02-09
SOLVED

I just installed Xubuntu edgy eft on an old IBM Intellistation E Pro (Pentium III).

I can't run Firefox as an ordinary user.

I can run it OK from a terminal using
```
sudo /usr/bin/firefox
```
but if I just click on the firefox panel icon, or click on firefox in the applications menu, or try to run it from the terminal as my ordinary user, nothing happens.  No error messages, NOTHING.

What could be causing this?

---

### Post by barney_1 on 2007-02-09
hmmm.... could be a permissions problem.  What is the output of this command:
```
ls -l /usr/bin/fir*
```

I get:
```
lrwxrwxrwx 1 root root 22 2007-01-23 21:06 /usr/bin/firefox -> ../lib/firefox/firefox
```

If you don't have full read/write/execute permission for that file (rwxrwxrwx at the beginning of the output) try changing that with:
```
sudo chmod 777 /usr/bin/firefox
```

---

### Post by r.stiltskin on 2007-02-09
No, I already checked that.

That link (/usr/bin/firefox) already has full read/write/execute permissions:
```
lrwxrwxrwx 1 root root 22 2007-02-09 09:02 /usr/bin/firefox -> ../lib/firefox/firefox
```

As you can see it points to /usr/lib/firefox/firefox.

/usr/lib has 7-5-5 permissions
/usr/lib/firefox has 7-5-5
and /usr/lib/firefox/firefox has 7-5-5

I don't think that any of those should be writeable by anyone other than root so that doesn't seem to be the problem.

---

### Post by llamakc on 2007-02-09
Create another user and login as the second user. See if the problem persists.

---

### Post by r.stiltskin on 2007-02-09
OK -- solved -- totally stupid reason.

I had kept my home directory from two previous (debian) installations and used the same username.  But the ownership of some of the existing files & subdirectories had been changed to a user NUMBER from a previous installation, even though they were sitting in the home directory of the correct (old & new) user NAME.  (Actually, I think this might have happened when I installed Debian over an older Debian setup.)

So I had a .mozilla directory that I couldn't write to.

---

