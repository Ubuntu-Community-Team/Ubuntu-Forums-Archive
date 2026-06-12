---
title: "Ubuntu boots on tty1"
date: 2015-11-09
forum: General Help
---

### Post by radoslav-stefanov2000 on 2015-11-09
Hi everyone!
I decided to change my load page using plymouth manager,but now my laptop boots on tty1.
I have tried ctrl + alt + f7 and the command  startx,but both of them turn my screen black.
My laptop is lenovo v570c and i use ubuntu 14.04.
Thanks!

---

### Post by grahammechanical on 2015-11-09
Linux loads on tty1 and Ubuntu logs in to Linux on tty1 and then Ubuntu should load on tty7. Is Ubuntu not logging in to Linux?

Regards.

---

### Post by radoslav-stefanov2000 on 2015-11-09
No,only tty1 loads and it asks me for username and password and i can type commands only

---

### Post by Bashing-om on 2015-11-09
radoslav-stefanov2000; Hello;

Let's get a bit more insight on what is not happening.

ubuntu uses unity as the (D)esktop (E)nvironment . It's display manager is 'lightdm' and as such the command 'startx' is not applicable in this application.
We control the display manager with a different set of commands.
To get additional insight:
boot to that TTY terminal .. and issue terminal command:
```

sudo service lightdm restart

```
what results ? and what errors does the system report ?

[INDENT][INDENT]a process of learning 
[/INDENT][/INDENT]

---

### Post by radoslav-stefanov2000 on 2015-11-09
Thank you VERY much.I executed the command and now all is ok.

---

### Post by Bashing-om on 2015-11-09
radoslav-stefanov2000; Hey ...

While productive .. was no magic fix !

How now when you reboot ?

[INDENT][INDENT]but, hey, maybe 
[/INDENT][/INDENT]

---

### Post by radoslav-stefanov2000 on 2015-11-09
Unfortunately,the tty1 screen appears again and i need to run the command to continue.
Is there a way to avoid the tty1 screen and "open" directly ubuntu?

---

### Post by Bashing-om on 2015-11-09
radoslav-stefanov2000; Yuk ;

Why am I not surprised.
Yeah, there has to be a fix .. however, unity is a complex system . May take a bit to find the fault.
We start by asking .. when you restart lightdm ... are there any reported errors ( maybe ctl+alt+F1 to return to the TTY and look ) ( alt+F7 returns to the GUI).

And we can look Once the GUI is started and see if the system logs any errors:
```

cat ~/.xsession-errors

```

As another test to determine that the fault is in your profile:
What results when you start the desktop from the guest session ?

[INDENT][INDENT]here there ain't no easy answer
[/INDENT][/INDENT]

---

### Post by radoslav-stefanov2000 on 2015-11-09
The output of the command is:
Script for ibus started at run_im.

And when i shutdown from the guest session,the normal shutdown ubuntu page appears,while when i shut down from my profile,it shows the screen in console version with black background

---

### Post by radoslav-stefanov2000 on 2015-11-09
Ok,i fixed it.
The problem was in Plymouth manager - i switched it to "activate" and changed the load page image,and now it works perfectly.
I also have a beautiful load page :D

Thank you very much!

---

### Post by Bashing-om on 2015-11-09
radoslav-stefanov2000; Great !

You did all the work, I just pushed.

As this situation is now under control :
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

alls well
[INDENT][INDENT][INDENT]that ends well
[/INDENT][/INDENT][/INDENT]

---

