---
title: "Menu entry to start a local server in a Terminal and keep the Terminal open"
date: 2021-12-05
forum: General Help
---

### Post by makem2 on 2021-12-05
I would like to achieve the following:

 By clicking on an Applications Menu entry, start a Minecraft server, keeping the  Terminal window open (as a Console). I can then manage the server from  that 'Console Window' when I return to the 'screen'.

I am using an Xfce desktop

 I have tried this script from a .sh file on my desktop until I get it working:

```

#!/bin/bash 
screen
cd /media/terabyte/minecraft/

java -Xms2G -Xmx2G -XX:+UseG1GC -jar spigot-1.17.1.jar nogui

```
But the terminal closes and the server is left running but I cannot control it and must kill it from the task manager.

---

### Post by Tadaen_Sylvermane on 2021-12-05
you may be able to extract what you need from this link? 

[https://minecraft.fandom.com/wiki/Tutorials/Server_startup_script](https://minecraft.fandom.com/wiki/Tutorials/Server_startup_script)

there are also countless minecraft docker images. this is one that i have been working on for my home. i use a custom init script. you might find what you need here if not above.

[https://gitlab.com/jmgibson1981/homescripts/-/tree/master/docker/minecraftserver](https://gitlab.com/jmgibson1981/homescripts/-/tree/master/docker/minecraftserver)

---

### Post by makem2 on 2021-12-05
> **Tadaen_Sylvermane said:**
> you may be able to extract what you need from this link? 

[https://minecraft.fandom.com/wiki/Tutorials/Server_startup_script](https://minecraft.fandom.com/wiki/Tutorials/Server_startup_script)

there are also countless minecraft docker images. this is one that i have been working on for my home. i use a custom init script. you might find what you need here if not above.

[https://gitlab.com/jmgibson1981/homescripts/-/tree/master/docker/minecraftserver](https://gitlab.com/jmgibson1981/homescripts/-/tree/master/docker/minecraftserver)

Thank you, what is 'docker' hostname? It appears to introduce another unknown, 'containers'. All I want to do is keep the Terminal open for further use.

The Terminal (Console) must be available to make changes while the server is running and is also used to stop the server.

---

### Post by Tadaen_Sylvermane on 2021-12-06
Oh yea... I didn't mean to use the script exactly. It would just show the command to run the minecraft in the screen. In this case in my script

```
screen -dmS "$CURRENT" java -jar "$JARFILE" "$JAVAOPTS"
```

$CURRENT is the containers hostname, for you you can name it whatever you want. And the $JARFILE and $JAVAOPTS the java file and options respectively. This is to start it. This will detach from the screen session so you can use the terminal or run headless. There are ways to run commands from the screen command or re-attach screen. In my case I run directly from the screen command.

```
screen -p 0 -S "$CURRENT" -X eval "stuff \"${1}\"\015"
```

Here the ${1} is replaced with whatever command you wish to send.

If you want to keep the terminal open full time then I think you would use the first command minus the -d. Use the -mS though. Check the man pages to confirm.

---

### Post by dragonfly41 on 2021-12-06
Use Yakuake dropdown terminal.  Toggle F12.

---

