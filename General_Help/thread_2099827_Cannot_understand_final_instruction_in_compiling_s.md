---
title: "Cannot understand final instruction in compiling software"
date: 2012-12-30
forum: General Help
---

### Post by grey1beard on 2012-12-30
I'm going through a long process of installing a sim package for linuxcnc in Ubuntu 12.04, and don't understand what I have to do to follow the very last instruction !

On the Linuxcnc Documentation, following the "make" instruction, the last instruction is -

>  Add following to your path (such as .profile)

 export PATH=$PATH:[path to the linuxcnc dir]/linuxcnc/scripts/rip-environment

I have no idea where my "path" is, nor what it means, especially the "such as .profile".

After typing the "make" instruction in Terminal, and this having been carried out, the Terminal screen had a small framed entry -

 > Before running the software, set the environment:
    . (top dir)/scripts/rip-environment

I can see some similarities, but again, I've no idea what is meant by "set the environment".

A quiet word in my ear would be very humbly received.

John

---

### Post by thnewguy on 2012-12-30
A user's "path" is a list of directories where the system will look for commands to be run. Typically a user's path includes the directories /bin, /usr/bin and a few other locations. if you open a terminal and type "echo $PATH" you will see a complete list of these directories. This is what allows you to run commands like "ls" or "make" without specifying their complete location, like "/bin/ls" or "/usr/bin/make". 

What the instructions want you to do (though they aren't very clear on the subject) is to edit the .profile file in your home directory and add the line they specify in the instructions. Let's say you installed the software under the /opt directory, you would append the following line to your .profile file:

```

export PATH=$PATH:/opt/linuxcnc/scripts/rip-environment

```

You can edit the .profile file using any text editor, for example
```

gedit ~/.profile

```


Where the instructions say "set the environment", what they mean is set an "environment variable". This is a value the system can refer to later. For example, the PATH parameter you will set is an environment variable. To see a complete list of environment variables run the "set" command. It'll give you a long list of variable the command shell recognizes.

```

set

```

---

### Post by grey1beard on 2012-12-31
Many thanks, thnewguy, for the clear explanation.
Several more steps up the learning curve for me  :)

John

---

### Post by dino99 on 2012-12-31
indeed you'll need to run:

```
sudo gedit ~/.profile
```

---

### Post by fdrake on 2012-12-31
> **dino99 said:**
> indeed you'll need to run:

```
sudo gedit ~/.profile
```


Just breaking your spheres!!! :D

```

gksudo gedit ~/.profile

```
it's lightly prefferd....

also you do NOT need to use super user priv to edit your files in home so just
```

gedit ~/.profile

```should be fine

---

### Post by grey1beard on 2012-12-31
Hmm.
Thanks for help, all, but slightly puzzled still.
I understand what I have to do. It's a question of finding the right place to do it !

I used gedit via the terminal and it opened a small window as per screen shot attached.

As I'm not familiar with coding, please advise - do I add the line *export PATH=$PATH:[path to the linuxcnc dir]/linuxcnc/scripts/rip-environment* (modified with my own path to the linuxcnc directory) after line 22, with the if/fi 'arguments'(?) around it, like the lines 20 to 22 have, or do I insert it between the lines 21 and 22, with fi coming after it ?

Good grief, does that make sense :confused:

John

---

### Post by Cheesemill on 2012-12-31
You can just add it to the end of the file by itself.

---

### Post by grey1beard on 2012-12-31
Have I got this final Path line correct 

> export PATH=$PATH:/Desktop/Axis/linuxcnc/scripts/rip-environment

as I haven't yet got it to run, and this is the most likely error on my part.

(I've set it up in a folder Axis on my Desktop)
John

---

### Post by Cheesemill on 2012-12-31
You need to use the full path:
```
export PATH=$PATH:/home/username/Desktop/Axis/linuxcnc/scripts/rip-environment
```
Replacing username with your actual username.

---

### Post by grey1beard on 2012-12-31
Thanks Cheesemill.
You could have just shouted - I'm over in East Rudham :)

John

---

### Post by grey1beard on 2012-12-31
Thanks everyone, I've finaly got there - see attached - and learnt a great deal in the process :)

Happy New Year

John

---

