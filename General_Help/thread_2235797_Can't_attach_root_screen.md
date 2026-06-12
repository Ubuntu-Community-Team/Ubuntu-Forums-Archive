---
title: "Can't attach root screen"
date: 2014-07-23
forum: General Help
---

### Post by Mr. Universe on 2014-07-23
I'm writing some scripts to automate running a minecraft server but I'm  having trouble with screen. I'm running the server jar in a screen from a  service but once I'm logged in I cannot reattach the screen.

```
akbkuku@S-D-UBUNTU:~$ ps aux | grep minecraft-server
root      1270  0.0  0.0  24208  1256 ?        Ss   07:46   0:00 SCREEN -dmS minecraft-server java -Xms512M -Xmx1G -jar ./minecraft-server.jar
root      1272  0.8  5.5 3300368 453732 pts/0  Ssl+ 07:46   0:24 java -Xms512M -Xmx1G -jar ./minecraft-server.jar
akbkuku  14252  0.0  0.0  15952   924 pts/27   S+   08:34   0:00 grep --color=auto minecraft-server
akbkuku@S-D-UBUNTU:~$ sudo screen -r minecraft-server
There is no screen to be resumed matching minecraft-server.
```

[Here's the script]("https://github.com/AkBKukU/MinecraftServerSuite")

---

