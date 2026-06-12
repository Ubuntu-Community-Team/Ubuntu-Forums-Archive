---
title: "[Solved]  Xfce launcher will not run .sh script"
date: 2013-03-15
forum: General Help
---

### Post by cj360 on 2013-03-15
So I've been trying to get a game to run from it's .sh script that starts when I click on a launcher. The game is PokeMMO and the .sh script for it runs fine, if I run it in terminal from that folder. If I create a launcher in the panel of my desktop and try it the terminal flashes once and closes or says:
```
/home/andrew/Downloads/PokeMMO-Client/PokeMMO.sh: 2: java: not found
```

And the launcher has this for the command:
```
xfce4-terminal -H --command="/home/andrew/Downloads/PokeMMO-Client/PokeMMO.sh"
```

I'm on xubuntu 11.10 with xfce (lastest .v I belive). Not sure what other info I should add so yeah.

---

### Post by sisco311 on 2013-03-15
Try to change the current working directory to the directory where the script is located before you run it. 
```
cd /home/andrew/Downloads/PokeMMO-Client/ && ./PokeMMO.sh
```

---

### Post by schragge on 2013-03-15
When you launch the terminal with a command, ~/.bashrc doesn't get executed. This means that any changes to the environment you put there (PATH, CLASSPATH, JAVA_HOME) won't be carried over to the script.

---

### Post by cj360 on 2013-03-16
After trying sisco's advice I get a ```
Failed to execute command "cd /home/andrew/Downloads/PokeMMO-Client/ && ./PokeMMO.sh".
```  Same thing if I try just point to the script with  .[path-to script]

And schragge, since I have ```
# Java PATHs
export JAVA_HOME=/opt/java/64/jdk1.6.0_34
export PATH=$PATH:$JAVA_HOME/bin

# Android tools
export PATH=${PATH}:~/android-sdk/tools
export PATH=${PATH}:~/android-sdk/platform-tools
export PATH=${PATH}:~/bin
```   In my bashrc I need to re-decalre the java paths in the launcher?


Edit-  I tried adding a plain path to the script in the launcher and terminal flashes open for a second and then immedatly closes. But the script is fine when I run it in terminal from the pokemmo folder in thunar and terminal.

---

### Post by schragge on 2013-03-16
xfce4-terminal has an option *--working-directory*. You can try
```
xfce4-terminal --working-directory=/home/andrew/Downloads/PokeMMO-Client -Hc '/home/andrew/Downloads/PokeMMO-Client/PokeMMO.sh'
```

As for your paths from *~/.bashrc*, try to copy those lines to *~/.xsessionrc* (create the file if it doesn't exist). You need to re-login for the change to take effect.

---

### Post by cj360 on 2013-03-19
Same reaction, I see terminal open for a second and it immediately closes. Even after adding the lines to my new ~.xsessionrc and rebooting.

---

### Post by cj360 on 2013-03-19
Edit- fixed it! Instead of using the .sh script I just pasted the contents of it into the launcher and it's working directory into the working directory box obviously:

```
 command: java -Xmx512M -ea -Xbootclasspath/p:./libs/jsr166.jar -cp ./lib/*:PokeMMO.exe com.pokeemu.client.Client
working directory: /home/andrew/Downloads/PokeMMO-Client/
```

Thanks to the people above that helped and replied!

---

