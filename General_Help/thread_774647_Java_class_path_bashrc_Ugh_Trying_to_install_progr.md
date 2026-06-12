---
title: "Java class path? bashrc? Ugh? Trying to install program. Help!"
date: 2008-04-29
forum: General Help
---

### Post by plvral on 2008-04-29
I'm trying to install this Java program called Jmusic ( [http://jmusic.ci.qut.edu.au/index.html](http://jmusic.ci.qut.edu.au/index.html) ) and I'm having trouble with the instructions:

"Place the *jmusic.jar* file and *inst* directories in your Java class path. This is usually done by editing your shell .*rc file (in OS X for example edit or create a ~/.cshrc file or in Linux a ~/.bashrc file) and add the location of the jMusic directories to the class path environment variable."

Say what? Ummm, I wish I was told what to enter in the terminal, but alas, no such luck. Does anyone know what exactly I have to do? The code for the Java class path? Code for the bashrc file? 

Any help would be great!

---

### Post by mali2297 on 2008-04-29
Let's say that you have extracted the downloaded archive in your home folder, so that you now have a subfolder *jMusic* there. Then open .bashrc in an editor (it's a hidden file in your home folder) and add the line
```

export CLASSPATH=.:$HOME/jMusic/jmusic.jar:$HOME/jMusic/inst/

```
into it. Open a new terminal to utilise the changed environment variable.

---

