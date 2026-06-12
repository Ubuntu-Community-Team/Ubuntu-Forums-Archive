---
title: "Gnump3d failing to start..."
date: 2007-05-13
forum: General Help
---

### Post by homerj742 on 2007-05-13
Hey guys, I'm getting an error, everytime I want to restart gnump3d. Definitely not working. I'm not sure what's going on...

```
 sudo /etc/init.d/gnump3d restart
Restarting gnump3d: start-stop-daemon: warning: failed to kill 6071: No such process
gnump3d.

```

---

### Post by tgoose on 2007-05-13
Just a forewarning: I might not be the best to listen to about this because my gnump3d has issues with starting up too, and I have no idea why!

That said, is it actually accessible before you type this command? i.e. does [http://localhost:8888](http://localhost:8888) (or [http://localhost:8080](http://localhost:8080), I forget which the default is) show anything in Firefox?

If not, try 

```

ps -A | grep gnump3d

```

If that doesn't show anything, try

```

sudo /etc/init.d/gnump3d start

```

and that should get it at least running, although I think you're then in the same boat as me because I have to do that every time I reboot and I have no idea why.

If the ps command does show something, note down the number it gives you at the beginning and run
```

sudo kill (whatever number it is)

```

and then

```

sudo /etc/init.d/gnump3d start

```

---

### Post by homerj742 on 2007-05-13
Hey! That worked! thank you. I wonder what happened? The last server setup I had went really smoothly, no issues at all.

---

### Post by homerj742 on 2007-05-16
Damn, after a reboot, it stopped working again, and the above isn't working :(

---

