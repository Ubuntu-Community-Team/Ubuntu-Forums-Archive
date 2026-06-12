---
title: "question on linked folders"
date: 2013-01-11
forum: General Help
---

### Post by g.a. on 2013-01-11
hello,

i have the habit to link the folders i'm using more frequently on my desktop. when i open the folder under nautilus the command to go up one node send me to the desktop.

is it possible to " easily jump" from the linked folder to the original one in nautilus?

if not, any suggestion for a script that does it?

thanks in advance,
g.

---

### Post by zombifier25 on 2013-01-11
What do you mean by the "original" one? If the Home folder, then it should be in the left bookmark bar.

---

### Post by g.a. on 2013-01-11
i has been unclear.

the folder in

```
~/Desktop/nicename
```

is the link of

```
~/personal/nicename
```

when i'm in the linking folder (the one under desktop) is there a command to "jump" to the linked folder?

i would like to do it both in nautilus or from the shell

thanks
g.

---

### Post by bab1 on 2013-01-11
> **g.a. said:**
> hello,

i have the habit to link the folders i'm using more frequently on my desktop. when i open the folder under nautilus the command to go up one node send me to the desktop.

is it possible to " easily jump" from the linked folder to the original one in nautilus?

if not, any suggestion for a script that does it?

thanks in advance,
g.

The link resides in the Desktop directory and therefore the "command to go up one node" is relative to the Desktop directory rather than the destination of the link (the file it's pointing to).

---

### Post by vanadium on 2013-01-11
A "link" like you create is really aimed at customizing your file system at a deeper level: a link behaves most of the cases as a true folder.

To get the behaviour you want, you should create launchers instead. Unfortunately, while such launchers were common in the old gnome 2 desktop, easy access to create launchers on your desktop is disabled in Unity. You still could work around it creating your .desktop file manually.

In Unity, the more "supported" way to get quick access to your folders, is to create the traditional nautilus bookmarks. These also will appear on the right-click menu of the laucher's home folder icon. In addition, searching in Dash would be quick if directory search would work reliably, which it doesn't (many times, a directory I know is there does not show in the Dash).

---

### Post by g.a. on 2013-01-12
i found that the shell command to retrieve the target folder is

```
pwd -P
```

i'm a newbue and i naively though to use the following

```
pwd -P | cd
```

the pipe should send the output of the first command as input for the second right? so why it does not work? it does not do anything.

I also tried to write a short script but i do not understand the use of the variables. any help is appreciated. this is my tentative

```

# jump to the target folder
#!/bin/bash

t=`pwd -P`
echo "$t"
cd "$t"

```

the echo command is ok but the cd does not change the current directory

best
g.

---

### Post by Impavidus on 2013-01-12
```
pwd -P | cd
``` doesn't work because cd reads the new directory from the command line argument, not from standard input.
The script doesn't work because to execute it a new instance of bash is started. The new bash changes to the new directory, but the old one doesn't. This can be demonstrated using this script:```

#!/bin/bash
echo "The old path is:"
pwd
a=`pwd -P`
echo "Changing dir to $a"
cd "$a"
echo "The new path is:"
pwd
```The script will tell you it has changed directory, but you will stay in the old dir. To change dir you can use the command```
cd "$(pwd -P)"
```The quotes are only necessary if your directory names contain spaces or other strange characters. Else using the classical```
cd `pwd -P`
``` requires less typing.

---

### Post by zombifier25 on 2013-01-12
So, what links are we talking about? Links with the command "ln -s", or .desktop links?

---

### Post by g.a. on 2013-01-15
thanks for the reply

```
cd `pwd -P`
```

works fine from shell. if you have any hint to create a script under nautilus I will appreciate it as well.

best
g.

---

