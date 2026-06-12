---
title: "problem getting software"
date: 2007-12-21
forum: General Help
---

### Post by udyrfrykte on 2007-12-21
I just switched to ubuntu, and I'm a little confused. I've been looking for a c++ compiler to use, so I downloaded g++ from synaptic package manager. I applied changes, It says that the program was installed, but now I don't know how to actually run the program.

Is there a command in the terminal I need to run before I can use it?

---

### Post by taurus on 2007-12-21
You actually want the build-essential package.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install build-essential
gcc -v
```

---

### Post by udyrfrykte on 2007-12-21
Ok, I ran those, and it told me that "build-essential is already the newest version"

and with he last command I got "gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)"

So I have the package correct? But still when I got to applications>programming I see nothing, or any other place for that matter.

---

### Post by taurus on 2007-12-21
Now, you need to actually write a g++ program and then use the g++ compiler to compile it.  

```
g++ *filename.cpp*
```
I am not sure what exactly you are looking for here?

---

### Post by Sef on 2007-12-21
> But still when I got to applications>programming I see nothing, or any other place for that matter.

System > Preferences > Main Menu > Programming > click on the box next to what you want to show up in the applications menu.

---

### Post by udyrfrykte on 2007-12-21
Ok I went to System > Preferences > Main Menu > Programming, and I saw no g++


I'm just trying to actually open the g++ program after installing it. 
I browsed under usr/share/doc/ g++ (and all related folders) And couldn't find an .exe or anything to run it. This is the first day I've used ubuntu, and I still don't know what I'm doing.

---

### Post by shawnrgr on 2007-12-21
the build-essentials/g++ package that you installed is really just the compiler. That will not show up in the application menu. Its a command line tool. If you were to install some development software like an ide (anjuta, geany, eclipse) it would show up in the menu. You can write the code with them and they would be able to incorporate the compiler. This of a compiler like a dos command. say 'ipconfig' it doesn't show up in the start menu but other applications can run that function.

---

### Post by udyrfrykte on 2007-12-22
> **shawnrgr said:**
> the build-essentials/g++ package that you installed is really just the compiler. That will not show up in the application menu. Its a command line tool. If you were to install some development software like an ide (anjuta, geany, eclipse) it would show up in the menu. You can write the code with them and they would be able to incorporate the compiler. This of a compiler like a dos command. say 'ipconfig' it doesn't show up in the start menu but other applications can run that function.

Thanks shawnrgr, I thought that g++ was an IDE, and thats where my problem was.

---

