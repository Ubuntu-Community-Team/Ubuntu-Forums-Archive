---
title: "configuring .bashrc for java"
date: 2005-05-05
forum: General Help
---

### Post by mbdayton on 2005-05-05
I've decided to start learning programming and I've chosen java as a starting point.  I'm having trouble editing .bashrc so that I can run java programs.

I'm adding these lines at the end of my .bashrc file:

PATH=/usr/java/j2sdk1.4.0/bin$PATH;    export PATH
CLASSPATH=.;    export CLASSPATH

---

### Post by Takis on 2005-05-05
Presumably your question is "why aren't these lines working", yes yes?

Try
```
export PATH=/usr/java/j2sdk1.4.0/bin:$PATH
export CLASSPATH=.
```

---

### Post by Professor X on 2005-05-05
This should fix it

```
export PATH=$PATH:/usr/java/j2sdk1.4.0/bin
export CLASSPATH=<location of jar files>
```

Oops.  Looks like I was beaten to it.  :razz:

---

### Post by mbdayton on 2005-05-05
Thanks I'm giving both those options a try right now.  
Are there any good resources where I can learn more about the bash config file, or config files in general?  It seems like there is a lot you can do with them.

---

### Post by mbdayton on 2005-05-05
It still ain't working.  Is there a specific place I need to put these lines of code?  I'm just tacking them onto the end of .bashrc.

BTW.  This is the error message I get when I try and run a java program in bash:

bash: javac: command not found

or 

bash: java: command not found

---

### Post by mendicant on 2005-05-05
You may have to edit ~/.bash_profile and add (or uncomment) the lines that say:

```

if [ -f ~/.bashrc ]; then
    source ~/.bashrc
fi

```

depending on where you're trying this.

Also, do an echo $PATH to see if it contains the correct path, then check the directory in $PATH to see if it contains javac.

---

### Post by Takis on 2005-05-05
[QUOTE=mbdayton]It still ain't working.  Is there a specific place I need to put these lines of code?  I'm just tacking them onto the end of .bashrc.

BTW.  This is the error message I get when I try and run a java program in bash:

bash: javac: command not found

or 

bash: java: command not found[/QUOTE]


This may seem a little silly, but did you start a new terminal after editing .bashrc...?

---

### Post by mbdayton on 2005-05-05
By uncomment, do you mean remove the # that's in front of them?

---

### Post by mendicant on 2005-05-05
[QUOTE=mbdayton]By uncomment, do you mean remove the # that's in front of them?[/QUOTE]

Right.

---

### Post by mbdayton on 2005-05-05
Woo hoo!  I just learned something!

---

### Post by mbdayton on 2005-05-05
Prepare to give me a digitial slap.

I ran echo $PATH and got and saw that Jsdk1.4.0_08 was indeed in my path.  As I looked in the directory for javac I noticed that the file is actuall Jsdk1.4.2_08.  What a difference a number can make.

I guess its because I was initially referring to a book on how to configure .bashrc and it used an older version of the java sdk as its example.

Well, thanks for the help.

---

