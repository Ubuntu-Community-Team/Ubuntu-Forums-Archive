---
title: "Environmental Varibales"
date: 2008-05-22
forum: General Help
---

### Post by anderskitson on 2008-05-22
I am installing an sdk of a program, and am currently going through the instalation steps for the prereqisites, now the instructions are for windows, but I have the downloads for linux. So what Are they asking me to do here?


 >  Verify that the environment variables ANT_HOME and JAVA_HOME are set and
  that your PATH statement includes the locations of the Ant and Java binaries. For
7
  example., PATH should include C:\apache-ant-1.6.5\bin;
  C:\j2sdk1.4.2_06\bin.

> 
To do this in Windows:
    a. Select My Computer > Properties (from the shortcut menu) >
        Advanced tab.
    b. Click the Environment_Variables... button.
    c.  ANT_HOME and JAVA_HOME must each be listed in one or the other of
        the panels of the dialog box. To add either, below one of the panels, click
        the New button.
    d. In the New User Variable dialog box, add the Variable and Variable
        Value (see example New User Variable dialog box below).
        Examples:
        Variable = ANT_HOME; Variable Value = C:\apache-ant-1.6.5
        Variable = JAVA_HOME; Variable Value = C:\j2sdk1.4.2_06
...........

---

### Post by nick_h on 2008-05-22
You can check the contents of an environment variable with:
```
echo $PATH
```
You can set a variable with:
```
export MYVAR=sometext
```
You could place the definitions in your .bashrc startup file.

---

### Post by anderskitson on 2008-05-22
Sorry Should I Navigate to each one of the bin folders, and make the echo $path command, I hate to be a newbie, I need more explanation on the second part?

This is what is returned for the apache ant bin folder with the echo command
> /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

---

### Post by Despot Despondency on 2008-05-22
Your environment path basically tells your kernel where to look for whatever commands you type in to the terminal, or a program asks to perform. Hence, when you are installing these programs you'll need to add the paths to the files required to run your program to your environment path. 

To look at the places in your current path type the following in to the terminal

```

echo $PATH

```

To add paths to your personal environment path open the file .bashrc, which should be situated in your home folder. It might be under hidden files. Once you've open the file add the lines

```

PATH=/opt/matlab/bin:$PATH 
export PATH

```

where the above example is what I had to do to add matlab to my environment path. You should add your relevant path. This is just for your personal path, other peoples paths will remain the same. Can't remember how to that. Anyway, hope that helps.

---

### Post by anderskitson on 2008-05-22
I have been informed that java allready adds the environmental variables, do you know if apache ant does as well.> **Inxsible said:**
> Well, in that case, you should use the entire command that stchman provided. Once you do that, the _**Java environment variables will be automatically set**_.



---

### Post by Despot Despondency on 2008-05-22
Sorry I haven't got a clue. I'm a newbie myself, hence I've only got 30 odd posts. Couldn't you check that after installation? Check your path after installation and if the necessary paths aren't there then just add them using the information from the previous posts. Hope that helps. Afraid that's about as much as my extremely limited knowledge can provide. :)

---

### Post by anderskitson on 2008-05-22
Thanks, I actually just found out from the apache ant user manual on there site, I should just read more, but these forums are just so great that asking a question is so easy.

---

