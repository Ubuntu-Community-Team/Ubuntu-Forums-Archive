---
title: "Clisp causes big problem!"
date: 2006-11-05
forum: General Help
---

### Post by Zalbor on 2006-11-05
If I try to run clisp, and then stop the program, the process called lisp.run is still running. I can try to kill it all I want, but it never stops. Eventually it weighs down the processor and makes the system slow.
I need to use a lisp interpreter, and the only other one I can find is gcl, which is way too heavy and not as easy to use as clisp. What can I do?

If I try to "killall -v lisp.run" it returns "Killed lisp.run(8772) with signal 15" but the process is still running!

EDIT: I noticed that it only happens if I exit the program by clicking the X on the terminal window. So I just have to remmeber to exit it with Ctrl+D or the (quit) command. But still, it's something that ought to be corrected...

---

### Post by DaveBorealis on 2006-11-05
Hello Zalbor,
Out of curiosity, what happens if you try:
```
killall -vg -9 lisp.run
```

Dave

---

### Post by Zalbor on 2006-11-05
Yes, that kills it! Thank you!
I thought killall sent the kill signal by default, and was puzzled why it didn't work... But looking to see what -9 was I see it sent the term signal. That makes sense.

---

### Post by DaveBorealis on 2006-11-05
Glad to hear that it worked!  I've had NFS-related zombies that I haven't been able to kill other than with a reboot.  My guess is that some parent process that spawned either them or a parent of them was alive and keeping them open, but I just couldn't figure out where or who they were...although I didn't spen much time looking as I was in a rush and found it easier just to ignore them until the next reboot sent them to zombie heaven.  (Or hell?)

Dave

---

### Post by incubus on 2006-11-07
Hey Zalbor,

I use clisp myself, but an alternative is SBCL which is also available in the repositories.

I tried to get the same error as you're getting, but clisp seems to be behaving here.  Which desktop system are you using, out of curiosity?

best,
incubus

---

### Post by Zalbor on 2006-11-07
I'm using Gnome. I guess it could be a bug in gnome-terminal, but then other programs would be behaving the same.

---

