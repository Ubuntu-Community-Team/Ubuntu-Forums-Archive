---
title: "Azureus shutdown on shutdown"
date: 2005-10-02
forum: General Help
---

### Post by FlipFlop on 2005-10-02
I'm trying to find a way to make Azureus shutdown tidily when issuing "shutdown -r now"

Currently that just kills the java thread and next time Azureus starts it complains about not having been closed nicely.

This appears to be beyound my google-fu.

FlipFlop.

---

### Post by mlomker on 2005-10-02
I haven't done this, but I'd imagine that you could create a shutdown script in /etc/rc0.d that would kill azureus before your Xwindows session is killed.

---

### Post by PaganHippie on 2005-10-02
But you don't just want to kill Azureus, you want it to shut down gracefully, correct?

---

### Post by FlipFlop on 2005-10-02
Exactly.

Like having the system select File->Exit somehow.

I guess it isn't a huge big problem .. It's not like i need to restart my linux server all that often.

---

### Post by PaganHippie on 2005-10-02
Truth be known, I'd like to know the answer to your question, too.  As things are, I just make a point of manually shutting Azureus down before shutting down Linux.

For all the automation, sometimes there's just no substitute for user action.  ;)

---

### Post by mlomker on 2005-10-02
Actually, the default for the kill command is a graceful exit.  

The problem is that the system shutdown scripts might be doing a **kill -kill** and that is not graceful.  You could look at the man page for kill.  It's the difference between **kill -term *pid*** and **kill -kill *pid***.

---

### Post by FlipFlop on 2005-10-03
That worked :)

I just added "killall java" somewhere in the sysv shutdown process and saw no more complaining from Azureus.

---

### Post by Vuen on 2006-02-15
Can you describe how? I tried doing this but it doesn't work.

I made a file in /etc/init.d called killjava, chmod 755, owner root, containing the following text:

```
#! /bin/sh

killall java

exit 0
```

I then made a link to it in both /etc/rc0.d and /etc/rc6.d called K01killjava, so that it would do it before anything else.


When I run the script or a link to it out of the terminal, it works perfectly:

nick@Nick:/etc/rc6.d$ ./K01killjava

Azureus gracefully exits, and starts up the next time I run it with no complaints. But when I actually shut down or restart the system, it doesn't work. I get the same error and it sits for 10 minutes while it rechecks my active torrents.

Why isn't it running this script when my computer shuts down? Is there a way to make it wait until Azureus is completely shut down before it restarts?

---

### Post by ariel on 2006-11-14
Has anyone fixed this puzzle? I don't want to see the "has not shutdown tidily" slider anymore!!

Can someone explain in which script "killall java" is needed?
Thanks

---

### Post by ariel on 2006-11-17
For the records, the **latest beta** of Azureus v3 (now known as Vuze, you can get it here: [http://azureus.sourceforge.net/index_CVS.php](http://azureus.sourceforge.net/index_CVS.php)) includes an option to get rid of the annoying error message.

  Options > Interface > Alerts > Suppress alerts

If like me you don't like the new look of Vuze, you can easily go back to the v2.x interface by following their wiki instructions.

---

### Post by squirrelix on 2007-02-25
Uh, I am having this problem too, and it gets rather annoying. Has anyone been able to fix this?

Many thanks
-- Squirrelix

---

### Post by ariel on 2007-04-06
I still have to see a solution for this. However, during this time the Deluge  client has matured. Time for a client change when moving to Feisty I guess...

---

