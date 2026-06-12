---
title: "How do you get fortune to run at bootup"
date: 2005-05-05
forum: General Help
---

### Post by crazybill on 2005-05-05
How do you get the command ***fortune** * to run on Ubuntu Linux at bootup when logging in by a remote terminal, such as putty?

By fortune, I mean the the command
```
**$ /usr/games/fortune **   
```
which  prints to screen a random saying  when the command "fortune" is typed 
(if...
 **/usr/games** is put into the environmental variable **$PATH** or if*** fortune*** is copied to a location in **$PATH** such as:
```
**# cp /usr/games/fortune  /usr/bin/fortune**
```
...)

example:
```

**root@ubuntu3:/usr/games # fortune**
If this were Ada, I suppose we'd just constant fold 1/0 into

    die "Illegal division by zero"
             -- Larry Wall in <199711100226.SAA12549@wall.org>

```

---

### Post by Professor X on 2005-05-05
You could set up a cronjob that writes a fortune to your /etc/issue.net (the file containing the welcome message a user from a remote box will see).  Let me know how it goes.

---

### Post by crazybill on 2005-05-06
I don't think that will work. 
This is what comes up in the remote terminal after login:
```
Linux ubuntu4 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686 GNU/Linux
``` 
However, the contents of /etc/issue.net  is 
```
root@ubuntu4:/etc # cat issue.net
Ubuntu 5.04 "Hoary Hedgehog" %h

```

---

### Post by Xerampelinae on 2005-05-06
Why not just add the fortune command to your .bash_profile ?  (or similar file if you use a different shell)

Edit:  Ohhh... you want it to display before someone's logged in.  The previous guy had a decent idea.  You probably just have to uncomment the banner line in /etc/ssh/sshd_config line, so that it read the issue.net file.

---

### Post by crazybill on 2005-05-06
I figured it out myself. I will post the solution in the HOW TO section.

However, basically, you just modify the bash.bashrc file placing fortune at the end.

---

