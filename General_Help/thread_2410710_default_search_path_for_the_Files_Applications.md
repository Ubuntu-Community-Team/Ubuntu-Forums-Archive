---
title: "default search path for the Files Applications"
date: 2019-01-19
forum: General Help
---

### Post by gianluca3 on 2019-01-19
well,

the title tells all, do you know how to set the default search path for the Files Applications?

the default behavior, pressing crtl+F is to search from the current path including the subdirectories, i would like to start always from home.

thanks in advance.
g.

---

### Post by TheFu on 2019-01-20
PATH is for programs that have their permissions set to executable in the permissions.
There is a default path already setup.  You can see it with 
```
echo $PATH
```

Add a line like this:
Assuming your shell is set to bash,  You can set it in your ~/.bashrc
```
export PATH=$PATH:$HOME/bin
```  That would add the userid's HOME directory/bin to the program search path at the end.  Directory order matters, but you can always provide a full-path to any specific program to have it run.  This environment variable and the other 10 or so that are very important in Unix are covered in any basic Unix/Linux command line class or book.

You can check what shell your userid is using by running 
```
getent passwd thefu
```
and you can change your default shell to be a different one, with **chsh**. Beware, only approved shell programs can be used.
Any changes to the environment, like PATH, require a logout/login to become effective for the entire session.  If you just need the change for 1 program/shell, then you can modify it quickly and run the program.

As for searching the system for files in a general way, there are many different tools for that.  Some examples are:
**locate** - searches a precreated DB based on parts of a filename and access granted by file/directory permissions.
**find** - searches the file system based on the options to the command. Very powerful, but slow. Complex commands like find can be very confusing. [https://explainshell.com/](https://explainshell.com/) is helpful to see how the different options fit for a specific solution.
**recoll** - searches based on names and contents of files. Must be setup, indexes can become huge. Fast, like google

There are other tools like recoll, but IMHO, recoll is pretty awesome at what it does, assuming you are willing to blow 25% of the file storage on the indexing.

Or did I misunderstand the question completely?

---

### Post by vanadium on 2019-01-22
By design, search starts in the current folder. If you want to find something elsewhere, first press <Alt>+<Home> then start searching. That involves one extra keystroke.

---

### Post by gianluca3 on 2019-02-03
thanks to both of you, sorry for the late reply, I thought I subscribed to this thread with immediate notification but clearly not and I opened ubuntuforum today for other reasons... 

my question was replied by vanadium thanks, thanks also to you TheFu, I didn't know about recoll, I iwll give a look at it

best
g.

---

