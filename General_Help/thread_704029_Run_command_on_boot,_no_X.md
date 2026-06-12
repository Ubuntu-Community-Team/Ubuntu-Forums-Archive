---
title: "Run command on boot, no X"
date: 2008-02-21
forum: General Help
---

### Post by PinkFloyd102489 on 2008-02-21
Ive got the commands put into rc.local but they arent executing properly. Im trying to start my IRC server and the Services that go along with it. Here are the commands.

```

./Unreal3.2.7/unreal start
./services/anoperc start

```

I tried putting exec in front of each line, but that didnt help either. Im thinking that the "start" bit is throwing both of them off, as it doesnt appear in the command on boot.

---

### Post by Rocket2DMn on 2008-02-22
You should have the programs run from another script, probably in a screen session.  
You could also try adding "&" to the end of the line to send the process to the background, but having screen helps so you can attach to it.
```
/bin/su -c "/usr/bin/screen -A -m -d -S *screen_name* /etc/init.d/*script_file*" -l *username_to_run_under*
```
I use something like this to boot a counter-strike server on a Fedora Core machine (but it's the same idea).

---

### Post by bodhi.zazen on 2008-02-22
Use the full path

./ = current directory

---

