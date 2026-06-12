---
title: "Shell Script with curl works on terminal but not as menu launcher."
date: 2020-01-07
forum: General Help
---

### Post by Portaro on 2020-01-07
Hello friends I have a question that at this time I can't find the solution about why this script work if I put the command path in terminal but dont work when I try to launch as launcher menu.

I also put this same question on this forum but we cant find a solution &#8594; [https://www.linuxquestions.org/questions/linux-general-1/shell-script-with-curl-works-on-terminal-but-not-as-menu-launcher-4175667112/](https://www.linuxquestions.org/questions/linux-general-1/shell-script-with-curl-works-on-terminal-but-not-as-menu-launcher-4175667112/)

The scritp is a simple script that I use to see weather directly on terminal and I use curl command to connect to the wttr.in service and put the data of weather on terminal.

This is the script &#8594;

```
#!/usr/bin/env bash curl https://wttr.in/chaves
```

I put this code script on a file in one path &#8594; /home/joao/.config/tempo.sh

If I launch it directly on terminal (open lxterminal and put /home/joao/.config/tempo.sh) he works

But when  put this as a launcher on menu when I click on th icon menu only opens the terminal and do nothing.

I already try many combinations of code in the launcher file and never works.

Example &#8594;

```
[Desktop Entry]Name=tempo
Exec=bash -c /home/joao/.config/tempo.sh
Comment=
Icon=
NoDisplay=false
Type=Application
Terminal=true
Categories=Utility;
```

```
[Desktop Entry]Name=tempo
Exec=lxterminal -x sh -c "/home/joao/.config/tempo.sh; read foo"
Comment=
Icon=
NoDisplay=false
Type=Application
Terminal=true
Categories=Utility;



```

I already see permissions to execute and read file etc ...

Never works.

Thaks for any help.

---

### Post by TheFu on 2020-01-07
Try
```

#!/bin/bash 
/usr/bin/curl   [https://wttr.in/chaves](https://wttr.in/chaves)
```

Would be smart to specify the exact output directory+filename.  i don't use curl enough to know the options by heart. You can look them up as easily as I can.

In script, always fully specify the full-path to any commands. Always.

The first line of a script requires a special format.  Any beginning Linux book will explain that.  Here's one: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)

I know zero about newer Lubuntu and less about .desktop files. I did use LXDE on 14.04.  Probably should ask the LUbuntu distro people any specific questions about that based on the exact release you run.  After 18.04, they changed from LXDE to LXQt.  [https://lubuntu.net/](https://lubuntu.net/)

---

### Post by Portaro on 2020-01-17
Dont work, thanks for your help.

---

### Post by CatKiller on 2020-01-17
You don't need to launch an additional terminal or shell. Just using *Terminal=true* is sufficient. You would need something to keep the terminal open so you can see the output.

This works fine:

```

#!/bin/bash 
/usr/bin/curl https://wttr.in/chaves
read

```

```

[Desktop Entry]
Name=tempo
Exec=/home/joao/.config/tempo.sh
Type=Application
Terminal=true

```

---

### Post by Portaro on 2020-01-18
I already try this &#8594;

> #!/bin/bash /usr/bin/curl "https://wttr.in/chaves"
read -p "Press any key to continue"

> [Desktop Entry]Name=tempo
Exec=lxterminal --command="/bin/bash --init-file /home/joao/.config/tempo.sh"
Comment=
Icon=
NoDisplay=false
Type=Application
Terminal=true
Categories=Utility;




O this line (Exec=lxterminal --command="/bin/bash --init-file /home/joao/.config/tempo.sh")  and in the script I also try different types of command and changes and nothing work. The terminal simply open and do nothing. I have help in ther forums of other users and they comment to e that the command and script works well on their systems with other terminals like in Gnome, the problem can be caused by lxterminal so im investigate on lxterminal docs.

---

