---
title: "Java 3D and 3D Minesweeper? - Can't get it to run"
date: 2007-08-31
forum: General Help
---

### Post by RudolfMDLT on 2007-08-31
Hi there,

I can't get this program to run!
[http://www.nada.kth.se/~joh/minesweep3d/](http://www.nada.kth.se/~joh/minesweep3d/)

Here is an extract from the help file:

> There exist 2 different development trees 
stable and devel.
To run the game you need to be under Linux or Solaris.
I've included an installation of java3d for both platforms.
To run the game just source buildenv.sh, written for tcsh.
After that cd in to devel/1.3/ and type java3d MineSweep3D.
If you run on some other platform you need to have the java3d api installed.
After you have installed the api, just cd in stable/1.2 and type
java MineSweep3D. That should do it. 
We have noticed that on some windows system we get warnings but its safe to ignore it.
Also note that the source is included in this release.
We have also included documentation in javadoc style.


when running buildenv.sh I get this:

> rudolf@rh:~/Desktop/mine3d_12$ ./buildenv.sh
./buildenv.sh: line 3: setenv: command not found
./buildenv.sh: line 4: setenv: command not found
./buildenv.sh: line 5: setenv: command not found
./buildenv.sh: line 7: setenv: command not found
./buildenv.sh: line 8: setenv: command not found
./buildenv.sh: line 9: setenv: command not found
./buildenv.sh: line 10: setenv: command not found
./buildenv.sh: line 12: alias: java3d: not found
./buildenv.sh: line 12: alias: `java -Djava.library.path': invalid alias name

and actually trying to run the game:

> rudolf@rh:~/Desktop/mine3d_12$ java ./stable/1.2/Mine
Exception in thread "main" java.lang.NoClassDefFoundError: //stable/1/2/Mine
rudolf@rh:~/Desktop/mine3d_12$ java ./stable/1.2/MineSweep3D
Exception in thread "main" java.lang.NoClassDefFoundError: //stable/1/2/MineSweep3D
rudolf@rh:~/Desktop/mine3d_12$ java ./stable/1.2/MineSweep3D.class
Exception in thread "main" java.lang.NoClassDefFoundError: //stable/1/2/MineSweep3D/class
rudolf@rh:~/Desktop/mine3d_12$      

Please help me to get this working! :)


Thanks!

Rudolf

---

### Post by tszanon on 2007-08-31
Starting at the end: in order to run a java program, what you write after "java" really matters. If the developers instructed to enter that directory stable/1.2 before running the program, then you must do it (or put the complete path to the desired class in the CLASSPATH, but that's another story).

It seems that you don't have the package java3d installed. I think you have to download it from [http://java.sun.com](http://java.sun.com).
About setenv: I don't know this command. I'll see what I can find out.

---

### Post by RudolfMDLT on 2007-08-31
> **tszanon said:**
> Starting at the end: in order to run a java program, what you write after "java" really matters. If the developers instructed to enter that directory stable/1.2 before running the program, then you must do it (or put the complete path to the desired class in the CLASSPATH, but that's another story).

It seems that you don't have the package java3d installed. I think you have to download it from [http://java.sun.com](http://java.sun.com).
About setenv: I don't know this command. I'll see what I can find out.

Hi! thanks for the reply! :)

setenv is a command in the sh file that I try to run it. I have opened up the file and had a look, not anything that I can see/or understand... noob :(.

I've been to the java website but I can only find a Java 3D API?

---

### Post by tszanon on 2007-08-31
> **RudolfMDLT said:**
> setenv is a command in the sh file that I try to run it. I have opened up the file and had a look, not anything that I can see/or understand... noob :(.
Sorry, I still haven't had the time to research this one. But it's not strange, I've seen it before, somewhere...

> **RudolfMDLT said:**
> I've been to the java website but I can only find a Java 3D API?
This one wasn't very intuitive. I had to access [http://java.sun.com](http://java.sun.com), then click in the upper menu: Technologies > Java SE, then in the Technologies tab, under the graph, there is the section Desktop Components, which list Java3D ([https://java3d.dev.java.net/](https://java3d.dev.java.net/)). Scroll down the page and you will find the section Downloads. There is also the API, so you can know how to use it. :)

---

