---
title: "trying to rememeber how to navigate in the CLI"
date: 2015-05-08
forum: General Help
---

### Post by mattig89ch on 2015-05-08
Hidy ho all,

It's been a while since i seriously used the cli in any linux distro.  And I could use some help with backing out of directories

I'm trying to get to the /ect folder, to edit a file in there (trying to join my ubuntu box to a practice domain server).  Now I know the directory exists, but everytime I try to go to it directly it says it can't find the /ect folder.  I wanted to back out of where I was, and go all the way up the folder tree in the cli, then start drilling down to where I need to be in that direction.  But I cannot remember the command to back out of the current directory I'm in.

So, whats the command to go to the next lvl up in the folder tree from where I am now?

---

### Post by sisco311 on 2015-05-08
The directory you are looking for is /etc not /ect:
```
cd /etc
```

To navigate to the root directory use:
```
cd /
```
To navigate one level up in the directory tree:```
cd ..
```

Check out [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal) for other basic commands.

---

### Post by Dennis N on 2015-05-08
up one level: **cd ..**

```
dmn@Sydney:~$ cd ..
dmn@Sydney:/home$ cd ..
dmn@Sydney:/$
```

up two levels in one command: **cd ../..**

---

### Post by mattig89ch on 2015-05-08
ha!  thanks all!

one more question for you, I know you just can't tell the cli to open a file by saying the file name.  You have to specify what program to open the file with. Do I simply say "filename.extension programname" to run it?  or do I have to put the full path of the program to open the file inside the program?

---

### Post by Dennis N on 2015-05-08
To open a file with a certain application from the command line, use the file name after the application. You don't need the full path to the application unless it is not in a standard location for applications, but you would use a path with the file, unless you are in the same directory as the file when you give the command.  Applications installed by the package manager are placed in standard locations. Type $PATH in terminal to see those locations.

```
dmn@Sydney:~$ mousepad anyfile.txt
```

would open anyfile.txt in a new window with mousepad. anyfile.txt would have to be in the current working directory. When you close that window, you are returned to the terminal command line.

---

### Post by mattig89ch on 2015-05-11
ok, so I did have the order wrong, but I had the right idea.  Thanks for that, is there a specific program that acts like notepad on linux?  Something I can open just about any text file with?

---

### Post by Lars Noodén on 2015-05-11
You can open a text file with gedit, kate or leafpad, if you have one of them.  gedit is there by default in Ubuntu.  If you want the system to take a guess then you can try gnome-open.

```

gnome-open somefile.txt

```

---

### Post by dino99 on 2015-05-11
For the lazy's like me, i've set lot of aliases inside bashrc :p
[http://stackoverflow.com/questions/28205697/setting-a-pathname-as-an-alias-in-the-bashrc-file](http://stackoverflow.com/questions/28205697/setting-a-pathname-as-an-alias-in-the-bashrc-file)

---

