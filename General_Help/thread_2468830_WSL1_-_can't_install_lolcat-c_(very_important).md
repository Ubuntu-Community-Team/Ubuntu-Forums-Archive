---
title: "WSL1 - can't install lolcat-c (very important)"
date: 2021-11-11
forum: General Help
---

### Post by steve234 on 2021-11-11
Hi everyone,

I am carrying out the important task of installing [lolcat-c]("https://github.com/jaseg/lolcat") (the gem / pip versions are deprecated).

I can't use snap as this Ubuntu instance is running via WSL1 on a Win10 machine (no systemd).

I cloned the lolcat-c git repo, entered the working directory and have tried various combinations of ```
make
``` ```
make install
``` ```
make && make install
``` with and without ```
sudo
```. 

I thought I was getting somewhere (1) installing gcc, and (2) changing permissions to get round various "permission denied" errors. Namely: 


[LIST]
[*]Adding myself to the "staff" group; 
[*]Changing ownership of ```
/usr/local/bin/lolcat 
```and```
 /usr/local/bin/censor
```to my user 
[/LIST]

I've now run into a problem I can't fathom (I've read ```
man make
``` but can't see anything on point) The commands simply return a couple of commands / directories:

```
USER@MACHINE:~/lolcat$ make  
make: Nothing to be done for 'all'.                                                                                

USER@MACHINE:~/lolcat$ make install     
install lolcat /usr/local/bin/lolcat 
install censor /usr/local/bin/censor  
```

Make doesn't seem to be exiting with any flags - Anyone know what is going on?

---

### Post by Holger_Gehrke on 2021-11-11
Congratulations, you're done. If make outputs 'make: Nothing to be done for 'all', then all the files that might need compiling have already been compiled on a previous run of make. Similarly the output of 'make install' tells you that make copied 'lolcat' and 'censor' to /usr/local/bin/. You should now be able to run the compiled programs. 'lolcat ~/lolcat/lolcat.c' should output the source code of lolcat in all the colours of the rainbow. 

Holger

---

### Post by steve234 on 2021-11-11
> **Holger_Gehrke said:**
> 'lolcat ~/lolcat/lolcat.c' should output the source code of lolcat in all the colours of the rainbow. 
Holger

Thanks Holger - unfortunately not:

```
$ lolcat ~/lolcat/lolcat.c
-bash@ /usr/games/lolcat: No such file or directory
```

---

### Post by Holger_Gehrke on 2021-11-11
Hmm, that is strange. Check that there is an executable named 'lolcat' in /usr/local/bin/ ('ls -l /usr/local/bin/lol*' should have something like '-rwxr-xr-x' in the first column, meaning readable and executable by everybody, writeable only by the files owner). Also check whether /usr/local/bin is in the PATH ('echo $PATH' ; PATH is an environment variable containing a colon-separated list of all directories where the system looks for executable files). As a last resort you could  execute the executable which should still be in the directory containing the source ('~/lolcat/lolcat ~/lolcat/lolcat.c' ; if you give a path to an executable the shell will execute the program whether it's in the PATH or not.).

On a real Ubuntu this program just works, but WSL is to Linux as WINE is to Windows ...

Holger

---

