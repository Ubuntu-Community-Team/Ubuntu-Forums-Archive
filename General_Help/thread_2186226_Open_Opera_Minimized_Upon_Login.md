---
title: "Open Opera Minimized Upon Login"
date: 2013-11-06
forum: General Help
---

### Post by BrodieB on 2013-11-06
I'm trying to have Opera open minimized upon login, for email use. Any help would be appreciated (13.10 - Unity).

I'm not very technical but I got this far:

cd /usr/lib/opera; . opera; cd /usr/bin; . xterm -e xdotool search --name "Speed Dial - Opera" windowminimize

In a .sh file which opens on login via Startup Applications. As it stands, this successfully opens Opera upon login. The second part was me trying to have it then minimize, but it only works via terminal and not login.

Any ideas? (Please/Thanks?)

---

### Post by jamesisin on 2013-11-06
I'm trying to understand your code.

First, why does this:

cd /usr/lib/opera; . opera

... behave differently from this?

```
/usr/lib/opera/opera
```

This appears to act the same as your code (and simpler, which is probably better):

```
/usr/lib/opera/opera -sharedir /usr/lib/opera/
```

(It doesn't auto-kill the terminal though.)

Something similar might hold true for your next command.

---

### Post by jamesisin on 2013-11-06
I think this will open Opera behind everything else (not the same I know).

```
/usr/lib/opera/opera -sharedir /usr/lib/opera/ --remote 'lower()'
```

---

### Post by BrodieB on 2013-11-06
Thanks for the help. But I tried your code in both Startup Applications and in the .sh file and neither opened Opera upon login (for whatever reason).

---

### Post by jamesisin on 2013-11-07
I suppose you could try it in your current (odd to me) format.  So something like this:

```
cd /usr/lib/opera; . opera --remote 'lower()'
```

---

