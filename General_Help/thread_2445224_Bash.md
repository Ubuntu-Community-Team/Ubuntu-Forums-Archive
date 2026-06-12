---
title: "Bash"
date: 2020-06-10
forum: General Help
---

### Post by yegnal on 2020-06-10
At my wits end with this one

Trying to write a script that will not only work on my machine, but if shared too.  In that regard, I would need to refer to the ~/ or home directory in a script.  What I'm learning is that this is virtually impossible.

I've tried:
```

myHome=~
eval myHome=$myHome
#echo $myHome

```

[FONT=inherit]
But at the end of the day, it's not working.  It will echo correctly to the screen, but I'm utterly unable to use these methods to construct a path to files in the home directory, and then cp files from ~/whatever to wherever, which is beyond frustrating.

[/FONT]

---

### Post by VMC on 2020-06-10
```
someone=$(whoami)
```

---

### Post by SeijiSensei on 2020-06-10
Using whoami is good choice.  The $() construct in bash tells the shell to execute the command it finds inside the parentheses and return the result as a string.

Usually systems create "environmental variables" like $USER and $HOME when someone logs in.  
```

seiji@Linux:~$ echo $USER
seiji
seiji@Linux:~$ echo $HOME
/home/seiji

```
Now if you're trying to write a script that would run correctly across all platforms and shells, that's way beyond my abilities. In fact, I'm not sure it's possible.  Even on Linux, you can have different shells with different commands and environments.  In scripts, it's always a good idea to specify bash explicitly like:
```

#!/bin/bash
echo $USER
echo $HOME

```

You can see the entire array of default environment variables with the "printenv" command.

---

### Post by GhX6GZMB on 2020-06-10
NEVER!!! use ~ in a script. It's a convenient shortcut on some keyboards, nothing else. Only a shell can work with ~, most other programs (including the Kernel) have no idea what it is.
The correct way is to use $HOME (environment variable which ~ translates to). Always works.

Cheers.

---

### Post by yegnal on 2020-06-10
When I run a test script 
```

myHome=$(whoami)
myPathVariable='/home/'$myHome'/Documents/'
echo $myPathVariable

```
I get /home/me/Documents/

but when trying to copy I get 
cp: cannot stat '/home/root/Documents

Where does the work root come in ? ! ?.   The script is being run as SUDO, and I can make the copy of the file in a terminal directly no problem, just not working as a script......

---

### Post by yegnal on 2020-06-10
```
myPathVariable=$HOME'/Documents/'
```

echo's correctly in terminal, error as before trying to copy a file.  

Error is: [COLOR=#000000]cp: cannot stat '/home/root/Documents

It's being run as sudo, can't figure what the issue is..
[/COLOR]

---

### Post by yegnal on 2020-06-10
So, a simple test using ```
[COLOR=#000000][FONT=&quot]$HOME'/Documents/'
```
to copy a file works, I'm now guessing because I'm trying to copy to /usr/share/..... I'm getting some issue that even running as sudo is not allowing.

Any guesses...

The permissions are good, I think...

[/FONT][/COLOR]-rwxrwxr-x 1 me   me

do I need to add a sticky bit or something ?

---

### Post by GhX6GZMB on 2020-06-10
As no one knows what you're trying to do, just read post #4 again.

---

### Post by GhX6GZMB on 2020-06-10
Why are you using quotes? Example: $HOME/Documents is the same as ~/Documents

---

### Post by Holger_Gehrke on 2020-06-10
sudo means "**s**witch **u**ser and **do**",  but unless you tell it what user to switch to (by giving the option -u  followed by a username) it will switch to the system administrator which  on Unix-like systems is called root and has '/root/' as the home  directory.

Try this:
```
sudo bash -c 'echo $HOME'
```

If this shows '/root' then either the security policy in /etc/sudoers is set to run sudo as if the -H option is in effect ('Defaults always_set_home')  or sudo is aliased to 'sudo -H'. With the -H option sudo sets HOME to the home directory of the user to which you are switching.

---

### Post by yegnal on 2020-06-10
So how in the world do I accomplish copying a file, in a script, from my $HOME to /etc or /usr, because everything I'm doing is not working.

```

myHome=$HOME/Documents/
myDest=/tmp
myFile='/test.test'


echo $myHome$myFile


cp $myHome$myFile $myDest

```



I need to assign the pathways and the files to variables which works fine unless I try to copy into /usr
There MUST be a way to do this...

---

### Post by yegnal on 2020-06-10
Adding sudo in the script before each cp command did the trick.

---

