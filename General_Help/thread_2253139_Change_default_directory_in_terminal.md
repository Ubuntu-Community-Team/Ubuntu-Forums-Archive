---
title: "Change default directory in terminal"
date: 2014-11-17
forum: General Help
---

### Post by jack113 on 2014-11-17
Is there a command in ubuntu to make the default directory a different folder so i don't have to type cd filename every time i open the terminal?

---

### Post by nerdtron on 2014-11-17
The default folder location is your /home/username directory.

You can change that:
```
cd
pwd
 HOME=/tmp/folder
export HOME
cd
pwd

```

Now that would be temporary. You need to add HOME variable entry on your .bashrc file to make it persists on reboots.

---

### Post by coldcritter64 on 2014-11-17
If you want to open in, for example, your Downloads folder (change the address you want to open terminal at for your purposes).

1. 
```
gedit ~/.bashrc
``` this will open a file in gedit, the one that controls gnome terminal.

2. On a new line at the end of the file add the cd command, alter the next path to where you want opened.
```
cd ~/Downloads
```Save the file and exit.

Note the ~ symbol represents you users home folder /home/<username> only. So in my example the terminal will open in /home/<username>/Downloads.

To revert the changes open ~/.bashrc in an editor, delete the added cd command, save the file and exit. Any changes to ~/.bashrc will take place in the next terminal opened, any already open terminals need to be restarted for the effects to take place.

---

### Post by Habitual on 2014-11-18
if it's gnome-terminal (sorry I don't use Ubu)
```
gnome-terminal --working-directory=/path/to/some/directory
``` used to work. ;)

---

