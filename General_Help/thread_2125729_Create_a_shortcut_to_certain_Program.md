---
title: "Create a shortcut to certain Program"
date: 2013-03-14
forum: General Help
---

### Post by Bladeforce on 2013-03-14
Hi, I am trying to run an emulator from the command line called B-em ([http://b-em.bbcmicro.com/](http://b-em.bbcmicro.com/))
Now I have it compiled but to run it I have to type this in a terminal
./b-em

Could anybody explain to me how I can run this from a shortcut please. I have tried just adding this command in a new shortcut but it doesnt run and I have also tried just putting "b-em" in the exe part but still doesnt run. Any help please? :)

---

### Post by Impavidus on 2013-03-15
If your b-em command is somewhere in your PATH you can run it from the terminal and from a launcher with b-em. It apears this is not the case, as you have to start it with ./b-em. In your launcher you'll have to put the whole path before the command. Replace b-em by /path/to/b-em.

---

### Post by Bladeforce on 2013-03-15
Hi thanks, having rooted around I have an executable in my usr/bin directory called b-em but when i try to run it it just craps out but when i run ./b-em from a terminal it runs fine. So if I make a shortcut with the command /usr/bin/b-em it just doesnt run. I suppose a command /usr/bin/./b-em would make it go mad :) I'm struggling how to make this shortcut with the command ./b-em

---

### Post by Impavidus on 2013-03-15
If you run the command with ./b-em, from what directory do you do that? That must be the directory where the executable is present. While still in that directory, please post the output of these commands, so that I get an idea of what may go wrong (because something is not what you think it is):```

pwd
ls -l | grep "\<b-em\>"
ls -l /usr/bin | grep "\<b-em\>"

```
Copy-paste this into your terminal to get everything exacly right.

Besides, /usr/bin/./b-em and /usr/bin/b-em are exactly equivalent.

---

### Post by andrew.46 on 2013-03-15
> **Bladeforce said:**
> Hi thanks, having rooted around I have an executable in my usr/bin directory called b-em but when i try to run it it just craps out 

Is there an error message?

---

### Post by Bladeforce on 2013-03-15
Hi again when i run those commands i get this

-rwxrwxr-x 1 root   root     3102273 Mar 15 00:33 b-em

Now it seems even ./b-em is erroring out

When i run either b-em or ./b-em i get a an error Aborted (Core Dumped) in the terminal window yet it compiled fine and I had it running yesterday. Maybe I was running it from the source directory I cant remember

---

### Post by Impavidus on 2013-03-15
You only gave the last one. Can you give the output of all of them? I want to know in which directory you are when the program starts (and then crashes) with ./b-em. And also, can you give me the output of```
echo $PATH
```I apologise if I'm insulting your intelligence, but I found that too often people don't know what they're doing.Next, I just assumed this is a program you just start from the terminal, but maybe it's a program that has to run in a terminal? That can make quite a difference.

And finally, I see that now it also runs (but crashes) with b-em (without the ./). Dd you change anything to make that happen?

---

### Post by Bladeforce on 2013-03-15
When I put the first command in I just get nothing and when i enter echo $PATH I get this

/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/lib/jvm/java-7-oracle/bin:/usr/lib/jvm/java-7-oracle/db/bin:/usr/lib/jvm/java-7-oracle/jre/bin

Also I just tried using getlibs on the b-em file and it says I have all dependencies installed


EDIT and a big EDIT!!
My fault I moved the exe to the usr/bin directory so i could run it from a terminal anywhere but I had to put it in a new Folder with its system roms. Also b-em wants to wrtie a config file to the same directory as the exe so being in the usr/bin dir was not a good idea and was probably why I was getting the error, it's all working now.

Many many thanks for your help

---

### Post by Impavidus on 2013-03-16
Well, I've still no idea what you where doing but I'm glad you worked it out yourself.

Is the "Mark thread as solved" function working again?

---

