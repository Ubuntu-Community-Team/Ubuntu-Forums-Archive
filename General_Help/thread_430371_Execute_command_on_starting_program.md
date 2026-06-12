---
title: "Execute command on starting program"
date: 2007-05-02
forum: General Help
---

### Post by jackmc on 2007-05-02
I want to run a command every time I start Amarok. How can I do this?

---

### Post by blackened on 2007-05-02
You can probably do it with a bash script. It all depends on what you're trying to do.

---

### Post by jackmc on 2007-05-02
I want to run

```
remuco-amarok
```

every time I start amarok. Also, I'd like to kill it on exiting amarok (if possible)

---

### Post by blackened on 2007-05-02
Ok, so does Amarok already have to be running in order for it to work?

By that I mean will the program crash or fail to function properly if Amarok is not already running?

---

### Post by jackmc on 2007-05-02
No, I dont think so. Alternatively, I could just add it to startup so that it runs every time I switch the computer on. If that is easier I will do it instead :)

---

### Post by blackened on 2007-05-02
It would work that way, but you could do it with a script just as easily.

```
#!/bin/sh

#Start both programs.
remuco-amarok &
amarok &

#Wait until Amarok closes.
wait %%

#Dirty, but effective. There's probably a better way to close it but I'm lazy.
killall remuco-amarok
```

Make sure you make it executable either with Nautilus or with chmod +x *nameoffile*

I would also suggest making a launcher that points to the script, that way the icon will be purty. :)

---

### Post by jackmc on 2007-05-02
Thanks :)

Looks logical to me (I'm new here)

---

### Post by blackened on 2007-05-02
No worries. Let me know if it works properly.

---

### Post by masala on 2007-05-09
It is not required for Remuco that Amarok is on. However, the dcop-server must be running for Remuco to work (dcop is used to communicate with Amarok). On KDE desktops the dcop-server is probably running anytime. However, in Gnome this may be not true. In this case Amarok needs to get started once before Remuco can be started (Amarok automatically starts the dcop-server).

And yes, there is a smarter way to shutdown Remuco:

```
$ kill -s INT `pidof remuco-amarok`
```

Also the script above does not work (at least for me) because Amarak dispatches from the current shell and runs in a new process (amarokapp) in the background. This means the command 'amarok' in the script finishes after a few seconds and so Remuco is killed also after a few seconds.

This in mind the above script should look this way:

```

#!/bin/sh

#Start both programs.
amarokapp &
sleep 2
remuco-amarok &

#Wait until Amarok closes.
wait %1

kill -s INT `pidof remuco-amarok`

```

---

### Post by Jonne on 2007-05-09
Wasn't upstart designed for that sort of stuff?

---

