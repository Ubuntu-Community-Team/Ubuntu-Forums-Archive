---
title: "What these characters do in linux:   ./"
date: 2006-11-11
forum: General Help
---

### Post by JBull on 2006-11-11
Can someone explain what typing ./  does in linux? 
For example ./configure
or ./tkdegrib

Apparently it makes a file executable?

My problem is that I have installed a package from source and everything seem to go alright, a couple warning messages but no errors.  But the installation did not create an executable file.  Specifically, there is a file called /home/degrib/bin/tkdegrib that requires typing ./tkdegrib to execute.  Typing tkdegrib results in "bash: tkdegrib:  cammond not found"  Is the installation incomplete?   Or is this normal for some applications?

/home/degrib/bin$ls -l tkdegrib

-rwxr-xr-x 1 root root 1916248 2006-11-10 23:55 tkdegrib

---

### Post by FaBi3ttO on 2006-11-11
```
./
```
This caracters allow you to run an executable file located in the current directory.
Have you tried to run that file using sudo?
Hope it helps


Fabio Pozzi

---

### Post by taurus on 2006-11-11
```
./configure
```
means execute configure in current directory.  The reason you have to be in /home/degrib/bin to run tkdegrib because /home/degrib/bin is not in your path!  Once you put /home/degrib/bin in your path, you can run tkdegrib anywhere you want.  You can put that in your path by editing ~/.bashrc.

```
nano -w ~/.bashrc
```
Then, add this line to it...

```

PATH=$PATH:/home/degrib/bin:.

```
Either log out and back in again or run this command to source it.

```
source ~/.bashrc
```

---

### Post by deanlinkous on 2006-11-11
./ simply means the current directory that you are working in
So if you want to run a command in  /home/degrib/bin/ then you either need to navigate to that directory and then do a ./tkdegrib or do the whole path  /home/degrib/bin/tkdegrib

---

### Post by Peepsalot on 2006-11-11
a single period "." refers to the current directory.
a double period ".." refers to the directory above the current one(aka the parent directory)
a tilde "~" refers to the current user's home directory (ex. "/home/peepsalot" for me)
a slash "/" with nothing preceding it refers to the root directory of your filesystem.

When you run a command in terminal, the shell has to find the executable you are referring to before it can run it.  

If you do not specify the directory of the executable, it checks your PATH environment variable for a list of directories.  It looks in each directory for the command and runs it if it finds it.
Here is some info about path:
[http://www.linuxheadquarters.com/howto/basic/path.shtml](http://www.linuxheadquarters.com/howto/basic/path.shtml)

You can run this command in terminal to see what yours is set to:
```
env | grep PATH
```

By default, the current directory is not included in the path, which means the console will not normally execute files in your current directory unless you tell it explicitly tell it to run from that directory

So you tell it "." for the path, and you have to include the slash "/" otherwise it will think the period is part of the file name.

Another semi-related tip: "hidden" files are files whose name begins with a period "."  If you run ls, it will not normally display the hidden files.  The -a option "ls -a" will force it to display all files including the hidden ones.

---

