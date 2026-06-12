---
title: "Installing FullProf_Suite"
date: 2019-07-02
forum: General Help
---

### Post by angelo16 on 2019-07-02
Hi guys. I need some help to install FullProf_Suite on Ubuntu.

I downloaded FullProf_suite from this site:

[https://www.ill.eu/sites/fullprof/php/downloads.html](https://www.ill.eu/sites/fullprof/php/downloads.html)

I followed the following steps

===============================================================
Local Mode (Installation for a single user)
-------------------------------------------
1.- Create a directory in which you want to hold the programs of the FullProf_Suite.
    e.g.: $HOME/FullProf_Suite
2.- For doing that you must execute the following commands:
     -> cd $HOME
     -> mkdir FullProf_Suite
     -> cd FullProf_Suite
3.- Copy the file FullProf_Suite_XXXXNNNN_Lin.tgz (XXXX=Month NNNN=year) in the
    directory just created in step 2
4.- Decompress the file .tgz with the following command:
     -> tar -xzvf FullProf_Suite_XXXXNNNN_Lin.tgz
5.- Modify the configuration file to activate the environment variable FULLPROF (see below)
=============================================================================

_**After this, I got stuck.**_

============================================================================

Activation of the environment variable of the FullProf_Suite
------------------------------------------------------------
1.- Depending of the SHELL of the user the commands are different. The aim is to create the
    environment variable FULLPROF.
    To know what is the shell one is using you should execute the command:
    -> echo $SHELL

    Generally it is one of the following: Bourne (sh, bash), Korn(ksh), C(csh)

2.- From now we suppose we are using the Bourne of bash type. If you have another one you must
    consult how to do the equivalent commands we explain below.

3.- Edit the setting file of the user. In our case it should be in the root directory of
    the user and the name is .bashrc or .bash_profile

4.- Add the environment variable FULLPROF, that has as value the absolute path of the directory
    in which we have installed the programs of the FullProf Suite.

    For instance:
                  FULLPROF=/opt/FullProf_Suite
                  FULLPROF=/usr/local/bin/FullProf_Suite
                  FULLPROF=~/FullProf_Suite

5.- Add the above directory to the PATH variable
                  PATH=$FULLPROF:$PATH
6.- Export the defined variable
                  export FULLPROF
7.- The changes will be effective on opening a new terminal window. To verify that everything is OK,
    just type in your terminal the command:
    -> echo $FULLPROF
    The system will show the directory in which you have installed the programs.
=====================================================================================

_**The problem is that the instructions above were valid on Ubuntu16.04, but not anymore as the .basrc does not exist in my system**_

_Can someone turn on the lights for me ?_




Thanks in advance.



Angelo

---

### Post by TheFu on 2019-07-02
Details matter.   **.basrc** doesn't exist on any systems that I know.

Perhaps you mean **~/.bashrc**?  Also, this file won't help if you don't use bash as your shell.  What shell is being used?  To figure that out, open a terminal and run 'ps'
```
$ ps
  PID TTY          TIME CMD
17944 pts/4    00:00:00 bash
17979 pts/4    00:00:00 ps
```
I'm using bash.

If you are using bash and the  ~/.bashrc file doesn't exist, then make one.  This applies to config files on a Unix systems.  If you need one in a specific location, MAKE IT YOURSELF.

---

### Post by angelo16 on 2019-07-07
Hi, the output for the ps command is the same as yours.

So I only need to create .bashrc  file ?

---

