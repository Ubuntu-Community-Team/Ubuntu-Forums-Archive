---
title: "Program launched from script keep closing"
date: 2008-03-04
forum: General Help
---

### Post by superdif on 2008-03-04
Hi all,
I have some problem with some script I created and I hope you can help me figure it out.

I created a script that should launch World of Warcraft (thru wine) and renice it to -15 (since despite having good hardware, it does not run well).

The script is called 'launchwow' and it contains:
```
#!/bin/sh
cd /archive/scripts/
(env WINEPREFIX="/home/marco/.wine" wine "C:\Games\World of Warcraft\WoW.exe" &)
sleep 10
kdesudo ./nicewow
```

'nicewow' is another script that contain the following code:
```
#!/bin/sh
renice -15 `ps axl | grep WoW.exe | grep -v grep`
```
I had to keep this code in another script because I could not pass it directly to kdesudo (strangly I can pass it to normal sudo).

If I launch 'launchwow' from the console (meaning opening Konsole, launch the script and keeping Konsole open), it works correctly, but if I try to create a desktop icon, World of Warcraft opens but immediately close.

I tried to enable "Run in Terminal" and "do not close when program exit" on the desktop icon, but the output does not indicate any problem.

I'm using Kubuntu 7.10 64 bits and wine 0.9.55.

Any idea?

---

### Post by superdif on 2008-03-04
Well ... before officially posting this request I should have read those raccomended posts that shows up when you write a post. :-/

While I was writing this post the forum software suggested me this other post (that obviously fixed my issue):
[http://ubuntuforums.org/showthread.php?t=45638]("http://ubuntuforums.org/showthread.php?t=45638")

---

