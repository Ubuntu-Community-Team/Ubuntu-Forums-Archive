---
title: "A couple of question from determined switcher"
date: 2007-03-26
forum: General Help
---

### Post by I3roknI3ottle on 2007-03-26
Ok first off, Does anyone have a link to a nice grub guide?  I used to have one bookmarked and it told you how to do everything, but somehow lost it.

Next I have a iBook and I'm used to that and windows, and were saving documents (Windows = my documents, Mac = hardrive>then theres the left hand bar with all the option to save and store docs.)  but in Ubuntu I haven't quite figured out where to store personal documents and such as what is the most common method?

Also I have a printer thing saved to my desktop and would like to know how to home into desktop through terminal and install the thing.  It's hplip-1.7.3.run and I was told to CD into the save directory through terminal but I have no clue how to do this.

My Computer
P4 2.8, 512MB, 80GB, 250GB, FX5200 windows xp/ubuntu 6.10

---

### Post by jeffathehutt on 2007-03-26
I'm not sure where to find a good grub manual, but I'm sure there is something on these forums that would help.

Your personal files should be stored in your home directory.  The path would be /home/USER, just replace USER with whatever username you use to log in.  In fact, unless you use sudo, your home directory is the only directory you can write to.

For the printer, use these commands in a terminal (Applications->Accessories->Terminal)
```
cd Desktop
./hplip-1.7.3.run
```

---

### Post by dannyboy79 on 2007-03-26
the grub guide is here. [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
also, the above cd Desktop will only work if you are in your /home/username folder. If the terminal isn't telling you where you are you just type in pwd and it'll tell you. otherwise to cd to any directory no matter where you are just give it an absolute path like, cd /home/user/Desktop (NOTE: in linux capital and lowercase do matter and DO NOT use spaces in linux. It can cause headaches although it is acceptable)

---

### Post by Tomosaur on 2007-03-26
If you want to play around with grub - check the link in my sig :)

All your documents and such should go in your home directory. I personally create a Documents directory in my home dir, and save all my stuff to that. My Music folder and other stuff is also inside my Documents directory. There's no real 'rule' to it though - you can be as organized or as messy as you like :P


Just make sure you don't try and save documents outside your home directory. Your home directory is 'you' - just like your user directory on Windows.

---

### Post by dannyboy79 on 2007-03-26
you can save documens where ever you want, it's your computer, unless of course you have multiple users than maybe you'll want keep stuff in your home dir bu otherwise, pu stuff where you want!!!

---

### Post by 11hjpphty76lkjj on 2007-03-30
Actually the correct way to install hplip is so:

```
sh hplip-1.7.3.run
```

---

### Post by dannyboy79 on 2007-03-30
actually if you are only going to chime in to correct some1 it's only fitting that I correct you. All your command is doing is telling it to run the script using the original Bourne Shell. you can run any script with ./ if you did not put the scripts directory in your PATH, and . (the current directory) is not in the PATH either.

actually just typing in
hplip-1.7.3.run
is the most common way to execute a script assuming that the scripts directory is in your PATH BUT it is only preferred to execute the script like that in a subshell. The variables, functions and aliases created in this subshell are only known to the particular bash session of that subshell. When that shell exits and the parent regains control, everything is cleaned up and all changes to the state of the shell made by the script, are forgotten.

A script can also explicitly be executed by a given shell, as you suggest but generally we only do this if we want to obtain special behavior, such as checking if the script works with another shell or printing traces for debugging:

rbash script_name.sh 

sh script_name.sh 

bash -x script_name.sh

---

### Post by 11hjpphty76lkjj on 2007-03-30
dannyboy79,

You are correct there are several different ways to run a bash file, I don't dispute that--and I am well aware.  However the idea from my perspective is to provide the users of HPLIP with as consistent instruction as possible to limit the amount of support in the future.  

My objective is to provide the easiest and most straight forward and consistent instruction for HPLIP users so as to limit any confusion and make the process as straight forward as possible.

We can both agree that in linux there are any number of ways to do anything, however for most 'new' users having a consistent approach to solving a problem makes the learning curve a tad easier to follow and overall decreases any level of frustration the user may have.

Thanks for your comments.

A

---

### Post by dannyboy79 on 2007-03-30
> **kalosaurusrex said:**
> We can both agree that in linux there are any number of ways to do anything, however for most 'new' users having a consistent approach to solving a problem makes the learning curve a tad easier to follow and overall decreases any level of frustration the user may have.
If you are in fact trying to inform "new" users of a consistent approach than why would tell them to use sh and then the script name when you know for sure that that will NOT work in all cases if the "new" user just downloads the script to their computer. The main reason why NOT to use sh and then the script name is because invoking a Bash script by sh scriptname turns off Bash-specific extensions, and the script may therefore fail to execute. So if you want to inform "new" users something to run a script than you should inform them of the way that will work in most cases. I am still very new to linux but after reviewing the HPLIP.run file it appears that the only reason that HPLIP works this way is because the file has script="./hplip-installer" right in the beginning of it. That file must get exported and chmod'd to be executable when you first first run the self-extracting and self-executing .run file.

---

