---
title: "Bash can't find script but does exist"
date: 2016-12-11
forum: General Help
---

### Post by jhaaglund on 2016-12-11
So I've just installed Ubuntu 16.04 and having a very odd technical problem. Bash scripts worked fine yesterday but now when I try to run a script I get the following.

```
user@terminal:~$ ls -l ~/helloworld.sh
-rwxr-xr-x 1 user user 32 Dec 10 19:22 [my home path]/helloworld.sh
user@terminal:~$ .[my home path]/helloworld.sh
bash: .[my home path]/helloworld.sh: No such file or directory
```

---

### Post by spjackson on 2016-12-11
> **jhaaglund said:**
> So I've just installed Ubuntu 16.04 and having a very odd technical problem. Bash scripts worked fine yesterday but now when I try to run a script I get the following.

```
user@terminal:~$ ls -l ~/helloworld.sh
-rwxr-xr-x 1 user user 32 Dec 10 19:22 [my home path]/helloworld.sh
user@terminal:~$ .[my home path]/helloworld.sh
bash: .[my home path]/helloworld.sh: No such file or directory
```

Welcome to the forums.

Based on your output from ls, I conclude that this should work:
```

~/helloworld.sh

```
If you mean that you are typing something like:
```

./home/user/helloworld.sh

```
then that won't work because of the erroneous leading dot. You could do this instead:
```

/home/user/helloworld.sh

```
and that would work, but ~/helloworld.sh would be more normal.

---

### Post by jhaaglund on 2016-12-12
Hi, thanks for that. It appears that the leading dot was the problem, trouble with using material from tutorials online without understanding it fully I suppose.

---

### Post by kpatz on 2016-12-12
The dot represents the current directory you're in, so if you're in your home directory, ./helloworld.sh would work.

The issues you were having were because you were using the dot and also adding the path.  You can have one or the other but not both.

So, all of these will work:

```

/home/your_username_goes_here/helloworld.sh
~/helloworld.sh
./helloworld.sh  (if you're in your home directory at the time)

```

---

### Post by yetimon_64 on 2016-12-12
As noted the leading "." (period mark) mixed with the absolute path was the problem this time. 

But storing a script in a location not in your profiles "path" (like directly in your home folder in this case) can cause bash to not be able to find a script as well without the use of an absolute path to the file name or by using just the filename with a leading period mark while in the folder holding it. 

If you want to be able to use just the script name and not the absolute path or a leading period mark you can create a "~/bin" (/home/$USER/bin) folder and after a log out/log in any scripts stored there can be activated by just typing their name in the terminal. After a "log out/log in" the location ~/bin is included in your profiles path. 

If you stored the file "helloworld.sh" there, eg at "/home/<yourusername>/bin/helloworld.sh", then activating it is as easy as typing "helloworld.sh" (without the quotes) in the terminal and pressing the enter button. 

Just note if you do use a ~/bin folder any subfolders to it won't automatically be added to the path but can be easily added with an export command in the users ~/.profile file.

---

### Post by Keith_Helms on 2016-12-12
> **yetimon_64 said:**
> 
Just note if you do use a ~/bin folder any subfolders to it won't automatically be added to the path but can be easily added with an export command in the users ~/.profile file.

Unless of course, you add the following to your .profile: :)

```
# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
    for bindir in `ls -1 "$HOME/bin"`
    do
          binpath="$HOME/bin/$bindir"
          if [ -d "$binpath" ]; then
             PATH="$binpath:$PATH"
          fi
    done
fi
```

Oh, and yes I know that directory names with spaces and certain special characters in them wouldn't work for this code.

---

### Post by yetimon_64 on 2016-12-12
> **Keith_Helms said:**
> Unless of course, you add the following to your .profile: :)

```
# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
    for bindir in `ls -1 "$HOME/bin"`
    do
          binpath="$HOME/bin/$bindir"
          if [ -d "$binpath" ]; then
             PATH="$binpath:$PATH"
          fi
    done
fi
```
Nice neat looking bit of coding. I'll have to experiment further with that idea :smile:.

I've never tried that instead I've always added subfolders to the path with the export command or when I got too many used the .bashrc/bash_aliases code modified to create a .profile_export file.

eg. from my ~/.profile file ...```

if [ -f ~/.profile_export ]; then
    . ~/.profile_export
fi
```

The first few lines from ~/.profile_export file ...
```
## Custom export commands for user created $PATH (users path)
export PATH=$PATH:$HOME/.screenlayout
export PATH=$PATH:$HOME/bin/Console
export PATH=$PATH:$HOME/bin/Console/Apps

```
Here I currently have about 24 subfolders of ~/bin exported to the path along with other locations in my home folder like ".screenlayout". I also add any export commands for custom environment variables to this file eg.
```
## Custom export commands for user created system variables.
export DESK=$HOME/Desktop
```

---

### Post by Keith_Helms on 2016-12-12
I haven't messed with that code in a long time.  Here's an updated version that will handle both multiple levels of subdirectories and directory names with spaces in them:

```
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
    while IFS= read -d $'\0' bindir; do
        PATH="$bindir:$PATH"
    done < <(find -L "$HOME/bin" -mindepth 1  -type d -print0)
fi

```

I needed the -L option for find because my bin directory is a symbolic link to a different mount point.

---

