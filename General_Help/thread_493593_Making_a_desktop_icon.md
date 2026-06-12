---
title: "Making a desktop icon"
date: 2007-07-05
forum: General Help
---

### Post by ataiger on 2007-07-05
I installed RealPlayer 10 by a deb package found here: [https://help.ubuntu.com/community/RealplayerInstallationMethods](https://help.ubuntu.com/community/RealplayerInstallationMethods)

cuz the player doesnt work well without the option
```
export GTK_IM_MODULE=xim
```

I made a file named "realplay" under my home folder and entered some bash commands
```
export GTK_IM_MODULE=xim
realplay
```
so that when I type "bash ~/realplay" in terminal, the player runs well.

I tried making a desktop icon and entered "bash ~/realplay" for command. but this doesnt work. when I doubleclick the icon, nothing happens. is there anyone who can help me with this one?

ps. if you are using Feisty and have some time, plz read [http://ubuntuforums.org/showthread.php?t=492815](http://ubuntuforums.org/showthread.php?t=492815) and help.. :(

---

### Post by mannheim on 2007-07-05
Did you try changing the command in the launcher to "bash /full/path/to/your/script/realplay" ?

I think that should work. But the "right way" is to make your script executable (using "chmod +x realplay") and then just entering "/full/path/to/realplay" as the command for the launcher. For this to work, you may also need to add the line "#! /bin/bash" to the top of your script.

---

### Post by fragos on 2007-07-06
It could be that ~ won't work in this case.  try replacing ~ with "/home/(user name).  Does your script have the bash header "#!/bin/bash" as the first line?  Also I'd try placing your script in /usr/local/bin so it can be located for execution.  Do "echo $PATH" and you'll see where the system looks for executables.

---

