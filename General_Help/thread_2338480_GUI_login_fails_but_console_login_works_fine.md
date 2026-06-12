---
title: "GUI login fails but console login works fine"
date: 2016-09-28
forum: General Help
---

### Post by aajax on 2016-09-28
Newly installed ubuntu 16.04 boots up and displays login screen.  When correct password entered the login prompt is displayed again without any message.  When incorrect password is entered login prompt is displayed again with message saying the password is invalid.  Using CTL+ALT+F1 to obtain console session the login works correctly.  Conclusion is that there is nothing wrong with the password but GUI login fails.

Now what?

---

### Post by steeldriver on 2016-09-28
From the console session 

Make sure your filesystem isn't full:
```

df -h

```

Check the ownership and permissions of your home directory and X session authority files:
```

ls -ld ~/

ls -ld ~/.{ICE,X}authority

```

Look for any X session errors:
```

tail ~/.xsession-errors

```

---

### Post by ajgreeny on 2016-09-28
Is this your first boot or have you already been able to login in the past and suddenly lost the ability?

From your command-line login can you run command ```
ls -la >home.txt
```which will create a home.txt file which hopefully you can either study, looking for any ownership other than aajax aajax (or whatever your username is) in the list, other than one line near the top showing ```
drwxr-xr-x   4 root   root   4.0K Apr 26  2015 ../
```which is the /home folder owned by root, of course.

Note the line for .Xauthority as that can cause the sort of problem you are seeing.  It should be owned by you and show permissions **-rw-------**
If you see anything else come back again and we'll look further.

---

### Post by Bashing-om on 2016-09-28
p=13550873#post13550873
Wed Sep 28 22:51:37 UTC 2016
oist response spinning spinning spinning . 
stopeed the page and reload the page
forum advises a duplicate post ->
reply did not post !

still trying to post my reply in the thread.

[INDENT][INDENT]UNgood sloppyation, huh ?
[/INDENT][/INDENT]

---

### Post by aajax on 2016-09-30
.Xauthority was owned by root.  Changing that does allow login.  Many thanks!

---

### Post by ajgreeny on 2016-09-30
Have you by any chance ever used sudo for a GUI application, such as **sudo nautilus**?

If you have, do not do so again as that can cause exactly the sort of problem you have seen.
Except, of course update-manager and other similar apps which sort this out automatically using pkexec commands, if you must run GUI apps as root use **gksudo** instead, or even **sudo -H**, both of which are safe to use.

---

