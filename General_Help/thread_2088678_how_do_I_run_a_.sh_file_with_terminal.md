---
title: "how do I run a .sh file with terminal"
date: 2012-11-27
forum: General Help
---

### Post by Kinetos on 2012-11-27
Hi, I was trying to make my minecraft srever run at startup, (it's craftbukkit-1.4.5).  Right now I have the startup applications runing my .sh file to start it:
```
!#/bin/sh
cd /home/[user]/[subfolder]/[folder]
sh bukkit.sh
```
and my bukkit.sh is:
```
#!/bin/sh
 BINDIR=$(dirname "$(readlink -fn "$0")")
 cd "$BINDIR"
 /home/kinetos/java/jre1.7.0_09/bin/java -Xmx6144M -Xms6144M -jar craftbukkit-1.4.5-R0.2.jar -o true
```
but whenever it runs at startup, the terminal doesn't open, and my minecraft server is running without any way for me to run commands as [server].
How can I edit my .sh files to open terminal and keep it running?

Thanks for any help,
~Kinetos

---

### Post by SlugSlug on 2012-11-27
use screen


```
#!/bin/sh
 BINDIR=$(dirname "$(readlink -fn "$0")")
 cd "$BINDIR"
 screen /home/kinetos/java/jre1.7.0_09/bin/java -Xmx6144M -Xms6144M -jar craftbukkit-1.4.5-R0.2.jar -o true
```


then to get to the session use

```
screen -r
```

---

### Post by zombifier25 on 2012-11-27
If you want to keep the terminal open, instead of calling the script directly, try running the terminal first:
```
gnome-terminal --command=/path/to/bukkit.sh
```

---

### Post by Kinetos on 2012-11-27
> **zombifier25 said:**
> If you want to keep the terminal open, instead of calling the script directly, try running the terminal first:
```
gnome-terminal --command=/path/to/bukkit.sh
```

Awesome! That fixed it! Thanks zombifier25!

---

