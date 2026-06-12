---
title: "Making a launch button for a java application ??"
date: 2006-12-28
forum: General Help
---

### Post by loopymonkey on 2006-12-28
I have this great program called [sunrise]("http://sourceforge.net/projects/sunrisexp")  that I have installed in my home directory / sunrise and this is the code to launch the program from terminal:

```
java -Xmx128m -Djava.library.path=. -jar sunrise-desktop.jar
```

but I want to make a one click button on my menu bar to launch the file.  The file is located in a folder called sunrise though in my home directory.  I'm not a pro at unix and I'm confused how this gets done when it's such a long string in different folder.  :confused: 

Any insight appreciated!  I'm sick of launching terminal, then cd'ing to the sunrise folder and then running that code.    ](*,) 

thanks!

---

### Post by amo-ej1 on 2006-12-28
Simply create a new launcher, give it a name (pick anything) and as a command enter 

```

java -Xmx128m -Djava.library.path=. -jar /home/YOURUSER/sunrise/sunrise-desktop.jar

```

Since the launcher needs to know where it can find the .jar file, you pass the absolute path of the jarfile. (perhaps it's also required to do the for the java-library-path, but you can easily try that. 

And you should offcourse replace YOURUSER etc by the correct path.

---

