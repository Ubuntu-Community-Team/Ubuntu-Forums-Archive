---
title: "Setting Environment Variables"
date: 2007-02-19
forum: General Help
---

### Post by harshad on 2007-02-19
Hi,

I am trying to do some Java development work. For that  I need to modify the PATH environment variable and set a new ABC_HOME environment variable.

1) I looked for a GUI in Ubuntu to work with environment variables. But there isn't one.

2) In most web resources the way to set environment variables is 
```
set PATH=/mydirectory:${PATH}
```
```
export PATH
```

I tried that and it doesn't work. I did an echo ${PATH} and noticed that there was no change in the PATH variable.

3) So i ran
```
export PATH=/mydirectory:${PATH}
```
and then did an echo. 
The PATH variable was now modified. However when i opened a new terminal window. I again got the old PATH without /mydirectory 

4) To add a new variable I tried the SET and EXPORT option but it didn't work. However running
```
sudo gedit /etc/bash.bashrc
```
followed by adding the line
```
ABC_HOME=/mydirectory 
```
```
PATH=${ABC_HOME}/bin:${PATH}
```
in this file, did work. 

I do not know if this is the correct approach, but it does seem to work. It's strange that Linux doesn't have a standard way or GUI to set environment variables. 

What is the right way to add and edit environment variables? :confused: 

Is there a GUI for environment variables planned for a future Ubuntu release? 

thanks,
harshad

---

### Post by yabbadabbadont on 2007-02-19
You need to put those changes in your ~/.profile and/or ~/.bash_profile

What I do is to put them into ~/.bash_profile and then make ~/.profile a symbolic link to ~/.bash_profile

Example:```
/home/bubba $ ls -ld .*profile*
-rw-r--r-- 1 bubba bubba 236 2007-02-13 03:05 .bash_profile
lrwxrwxrwx 1 bubba bubba  13 2007-02-13 03:05 .profile -> .bash_profile
/home/bubba $ cat .bash_profile 
# /etc/skel/.bash_profile

# This file is sourced by bash for login shells.  The following line
# runs your .bashrc and is recommended by the bash info pages.
[[ -f ~/.bashrc ]] && . ~/.bashrc

[[ -d ~/bin ]] && export PATH=~/bin:$PATH

```
As you can see, I've added my ~/bin directory to my path.  I hope this helps.

---

### Post by sdide on 2007-02-19
in your ~/.bashrc 

add the line 

export PATH=${PATH}:/mydirectory

you can do that by:
 
$ echo "export PATH=${PATH}:/mydirectory" >> ~/.bashrc

---

### Post by harshad on 2007-02-19
Thanks yabbadabbadont and sdide.

How do these compare -

1) editing /etc/bash.bashrc

2) editing ~/.bashrc 

3) editing ~/.profile 

4) editing ~/.bash_profile


What's the standard way? Something I can recommend and write about?

I wasn't aware that ~ stood for home directory. Thanks for that addition.

---

### Post by yabbadabbadont on 2007-02-19
> **harshad said:**
> 1) editing /etc/bash.bashrc
This makes the path change for every user of that computer, not just you.  If you are the only user, then no problem.

> **harshad said:**
> 2) editing ~/.bashrc This is read every time a new shell is created even if it isn't a "login shell".  So every time you open a terminal window, or a new tab in a terminal, your ~/.bashrc file is read.  Putting your path change here probably won't hurt, but I believe that your path will grow each time you open a new shell.

> **harshad said:**
> 3) editing ~/.profile This is the traditional file that is read when a user logs in.  (In Unix systems anyway)  I'm not sure how bash treats it.  To be safe, I just make this a symbolic link to my ~/.bash_profile.

> **harshad said:**
> 4) editing ~/.bash_profileThis is the file that is read by bash when a new "login shell" is created.  Usually this means that the contents of this file are only read once when you first login.  This is generally considered the correct place to make any custom addtions to your environment variables.

---

### Post by Ramses de Norre on 2007-02-19
~/.bashrc will be the most efficient, as pointed out in the previous post.
The export line you told about works too but as you can read in the man page it sets the env var for the current shell and all subshells, but not for supershells, so if you run gnome-terminal from the terminal you exported the env var in, the env var will be set in that second shell too. But if you use a launcher the new shell is launched from your login shell which is above the one you exported the env var in hence it will not be set there.

---

### Post by harshad on 2007-02-21
Thanks for all the help.

If I insert the line 
JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun-1.5.0.08
in all these files 

1) /etc/bash_bashrc
2) ~/.bashrc
3) ~/.bash_profile

And then run echo ${JAVA_HOME} in the terminal, I do get the correct JAVA_HOME value. 

However if I invoke a script from the terminal and the script tries to use the JAVA_HOME value, it doesn't work. 

echo ${JAVA_HOME} within the script returns empty string.

So if I try to run the Tomcat server using ```
sh catalina.sh
``` . I get the message **Neither the JAVA_HOME nor the JRE_HOME environment variable is defined**

So every time I wish to run a script I first have to add the JAVA_HOME line to the top of the script to get it to work.

Any idea how this script - environment variable problem could be resolved?

---

### Post by maher on 2007-02-21
try to add the following to /etc/profile

```

#JAVA and TOMCAT 4
JAVA_HOME=/usr/java/j2sdk1.4.2_11
CLASSPATH=.:/usr/java/j2sdk1.4.2_11/lib/tools.jar
CATALINA_HOME=/usr/tomcat/jakarta-tomcat-4.1.31


```

Of course you will have to change the different paths according to your environment
once the changes made, you must be root in order to execute the following command:

source /etc/profile

good luck

---

### Post by mannheim on 2007-02-21
> **harshad said:**
> Thanks for all the help.

If I insert the line 
JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun-1.5.0.08
in all these files 

1) /etc/bash_bashrc
2) ~/.bashrc
3) ~/.bash_profile

And then run echo ${JAVA_HOME} in the terminal, I do get the correct JAVA_HOME value. 

However if I invoke a script from the terminal and the script tries to use the JAVA_HOME value, it doesn't work. 


You also need to insert```
export JAVA_HOME
``` in order for the variable to passed to the environment of other processes launched from the shell.

If you use gnome, then a good alternative is to put these lines in a file** ~/.gnomerc** :
```
JAVA_HOME=whatever
export JAVA_HOME
```
This way, the environment variable will be present in all processes that are part of your gnome session (including Terminal and scripts launched from there).

---

