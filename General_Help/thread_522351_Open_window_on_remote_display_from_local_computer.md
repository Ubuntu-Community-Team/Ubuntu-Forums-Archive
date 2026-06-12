---
title: "Open window on remote display from local computer"
date: 2007-08-10
forum: General Help
---

### Post by newlinux on 2007-08-10
I know how to log into a remote server and display applications on the local display by forwarding X through ssh. However how do I open a window on a remote display?

e.g. I'm on computer A. Remote display is computer B.

If I am physically at A how do I display something on B's display? I used to do this using xhost more than a decade ago, but I don't think this is how this done now...

I'm mostly just curious.

Any thoughts appreciated and pardon my ignorance.

---

### Post by thelinuxguy on 2007-08-10
Try
```

export DISPLAY=localhost:0

```
before launching the applications to have their windows appear on the remote desktop. 
If you get XAuthority related errors, take a look at this thread: [http://ubuntuforums.org/showthread.php?t=405756](http://ubuntuforums.org/showthread.php?t=405756)

---

### Post by newlinux on 2007-08-10
I should clarify a bit. I can from local computer A connect (ssh) to remote computer B and have something display on computer B's display by doing :

-display :0
or --display :0

depending on the app or

export DISPLAY=:0

But how can I display an app run from computer A on computer B's display? Maybe this isn't possible anymore, but years ago I swear I used to do this using xhost on UNIX platforms...

I'll look into the XAuthority thread. Thanks.

---

### Post by thelinuxguy on 2007-08-11
Then maybe you are looking for xmove. It requires that xmove be running before you start the X clients.

```

apt-cache show xmove

```

There was a similar question at  [this thread]("http://ubuntuforums.org/showthread.php?t=453306") but the result was not posted.

---

