---
title: "How do you start applications in terminal"
date: 2007-05-21
forum: General Help
---

### Post by battleshipterry on 2007-05-21
I am a little new to the Linux world I have been having trouble getting applications to start if they are not in the Ubuntu Applications menu. I go to terminal and type the name and sometimes diffrent applications wont run.(some do some dont).they are installed in Synaptic Package Manager. Sorry for the dumb question. I am just getting into Linux  I tried several years a go with Mandrake and it threw me I don't want to give up on  it this time.Thanks.

---

### Post by wormser on 2007-05-21
You have to specify the path to the program.  So to run a program you need to know where it is at then to run the command by specifing the whole path.  

```
/opt/whatever/command
```

Most system commands can just be run by typing their name like **ls**.  This is because the shell is told where to look for it from the $PATH variable.  

> echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games


The different file locations are separated by colons.  Any program in the files above will run.  You can also add more locations to the $PATH.

Hopefully that helps.  :)

---

### Post by aysiu on 2007-05-21
Well, you can create a launcher if you know the command. Right-click the applications menu and edit the menu.

If you don't want a launcher, you can press Alt-F2 and type the name of the program in the Run dialogue box.

If you don't know the command to launch the program, type ```
which *programname*
``` in [the terminal](http://www.psychocats.net/ubuntu/terminal).

---

### Post by battleshipterry on 2007-05-21
Thanks this gives me something to work with for a while.

Wormser

Great this helped a lot I was able to get a few applications running that I was not able to do before. I did not quite grasp the part 

Quote:
echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games 
The different file locations are separated by colons. Any program in the files above will run. You can also add more locations to the $PATH.

I would assume that it is to define the path to the application I want to run without typing the location of the file but I just did not understand.

AYSIU
I did create a launcher with the /usr/games/programname in  the command box dont know where launcher went after I created it and again I would assume it is like a link or symbolic link to run the application.  if I can only find it.

I must add every time I get a answer for a problem in Linux it generates 2 more why is that.:D

---

### Post by qix on 2007-05-21
All my "launcher-symbolic-links" is located in /usr/bin. If you browse to that directory, you will find a lot of symlinks.

---

