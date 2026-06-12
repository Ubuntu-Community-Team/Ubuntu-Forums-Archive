---
title: "[SOLVED] HELP!!! X Window System Error with aMULE! HELP!"
date: 2008-01-18
forum: General Help
---

### Post by heatblazer on 2008-01-18
I`ve started my PC and I clicked on my aMule icon... It doesen`t start. I`ve stardet it with the command prompt - amule and here what it says:
 (Details: serial 404 error_code 11 request_code 149 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

I`ve typed "amule --sync" and:

Checking if there is an instance already running...
No other instances are running.
HTTP download thread started
The program 'amule' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 1148 error_code 11 request_code 149 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

By the God! I`m not running more amules! What is going on?! Please help!

---

### Post by fyo on 2008-01-18
Try looking at one of the DOZENS of identical posts, dude.

Seriously, help yourself... it's a lot faster.

---

### Post by andrea.dolcini on 2008-01-18
ok but  where to find these posts?
Sorry for bugging but i'm a beginner an i'd love to solve this problema asap.

Thanks

And :KS

---

### Post by Ebuntor on 2008-01-18
> **andrea.dolcini said:**
> ok but  where to find these posts?
Sorry for bugging but i'm a beginner an i'd love to solve this problema asap.

Thanks

And :KS

[http://ubuntuforums.org/showthread.php?t=671272&highlight=amule](http://ubuntuforums.org/showthread.php?t=671272&highlight=amule)

That's one of many threads. It seems that it's a Xorg security update that is causing the problem. 

According to [this thread]("http://ubuntuforums.org/showthread.php?p=4159471") the update has been pulled from the servers and a fix is on the way.  I strongly advice against downgrading any packages as it might cause more problems.

There are many/all Java based apps that are affected so I assume it's pretty high priority, shouldn't take long before there's a patch.

---

### Post by heatblazer on 2008-01-18
1000 thanx are not enough, Edbuntur. Let`s hope that they will fix that bug. T

---

### Post by heatblazer on 2008-01-19
Today I saw there was an important upgrade and it was the fix of the x-org. server. Now my aMule is working. Thanx again :) Now the admins can close the topic :):guitar:

---

### Post by Ebuntor on 2008-01-19
> **heatblazer said:**
> Today I saw there was an important upgrade and it was the fix of the x-org. server. Now my aMule is working. Thanx again :) Now the admins can close the topic :):guitar:

You're welcome. I downloaded the same fix a few hours ago, all back to normal. No need to close the thread I think but you could sign the topic as "fixed", the option is under "thread tools" I believe.

---

