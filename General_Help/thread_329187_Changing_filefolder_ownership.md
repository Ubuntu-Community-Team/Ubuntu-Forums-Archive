---
title: "Changing file/folder ownership"
date: 2007-01-01
forum: General Help
---

### Post by Keldek on 2007-01-01
Hello, I'm attempting to change ownership of all my wine installs, the current owner for all files, folder, subfolders & files is root. I would like to change them all so I don't have to sudo -s via terminal every time I want to run a game.

So far, I'm able to change the ownership of a single file or folder using:

```
sudo chown system_username /location_of_files_or_folders
```

The problem I'm having is that this command only changes ownership of a single file/folder. Is there any way I can change the ownership so that the change will be applied to all subfolders & files?

---

### Post by moma on 2007-01-01
$  [COLOR="SeaGreen"]sudo chown -R $USER:$USER  location_of_files_or_folders[/COLOR]

Of course you can replace $USER with any user name.  $USER contains the value of current login user (you!).

---

### Post by bluenova on 2007-01-01
If you need to find more options about a command you can put 'man' infront of the command like:

man chown

(letter 'Q' to exit)

You can then see all the options such as like:

       -R, --recursive
              operate on files and directories recursively

---

### Post by Keldek on 2007-01-01
thanks a ton, worked perfectly :)

---

