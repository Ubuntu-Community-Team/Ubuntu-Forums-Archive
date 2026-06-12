---
title: "Navigate to this Directory?"
date: 2007-07-01
forum: General Help
---

### Post by sk8ron on 2007-07-01
What does it mean when in the instructions to download software to your computer it says 'Navigate to this Directory'?  I know that I have to open the terminal and type in the code but when I do that I get an error message saying that it doesn't exist or something.  What am I doing wrong?

---

### Post by kebes on 2007-07-01
"Navigate to this directory" means either to open your file browser and go there, or use the commandline program (terminal) to go there. On the commandline, if you want to go to the directory "/var/www/" you would type:

cd /var/www/

(and then press enter) You can then continue with the steps described. Sometimes a set of instructions will tell you to make a directory (or unpack something, which generates a directory) and then tell you to "navigate into that new directory." Again you use the "cd" command on the commandline to do that. If you're in the directory "/tmp/" and you want to go into the subdirectory "new" you just type:

cd new

That's it!

If you keep having problems, giving us the specific error message, and the specific instructions you are trying to follow, helps a lot! Good luck!

---

### Post by sk8ron on 2007-07-01
'bash: ./flashplayer-installer: No such file or directory' is my error message,  I am still getting it.  What I did was downloaded the file and it is now on my desktop and then it told me to open the terminal and to type that code.  That's what I did and that was the error message I got.

---

### Post by sk8ron on 2007-07-01
I just got it.  Thanks for the help

---

### Post by jsarran on 2007-12-30
yeah, im trying to install flash player 9 and when i put the directory file in it says 'bash: cd: /install_flash_player_9_linux/: No such file or directory'

---

### Post by ~LoKe on 2007-12-30
> **jsarran said:**
> yeah, im trying to install flash player 9 and when i put the directory file in it says 'bash: cd: /install_flash_player_9_linux/: No such file or directory'

Try this:
```
cd install_flash_player_9_linux
```

---

### Post by jsarran on 2007-12-30
same thing, thanks tho

---

### Post by ~LoKe on 2007-12-30
> **jsarran said:**
> yeah, im trying to install flash player 9 and when i put the directory file in it says 'bash: cd: /install_flash_player_9_linux/: No such file or directory'

> **jsarran said:**
> same thing, thanks tho

Try..
```
locate install_flash_player
```

---

### Post by aktiwers on 2007-12-30
Did you remember to unpack the file you downloaded?

---

### Post by jsarran on 2007-12-30
yes! i didn't extract file thanks!:lolflag:

---

