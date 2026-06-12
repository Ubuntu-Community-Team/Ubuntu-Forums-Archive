---
title: "Help me change bash prompt and use aliases using sudo"
date: 2006-12-18
forum: General Help
---

### Post by dannyboy79 on 2006-12-18
Hi there, I am a newbie for all intensive purposes. I would like to change my bash prompt and add some aliases. When I look around for my .bashrc file within my home dir it didn't exist so I created one and added my aliases per a website. then I exited putty and logged in again. Now whats weird is that it kind of works? I want my aliases for mv, rm, and cp to work when I am logged in as root (NOT OFTEN DON'T WORRY!!!), when I am logged in as me, and when I am logged in as me using sudo. I have been able to get the first 2 figured out my simply adding the aliases I wanted to every .bashrc, profile, or bash_bashrc file I could find. Which were in like /root/, /etc/skel/, and /etc/, but it still doesn't work when I use sudo? Can anyone help me with this?


Next thing: Why are there so many places for the bash preferences?  i did a locate on .bashrc and this is what I found:
/etc/skel/.bashrc
/etc/bash.bashrc
/root/.bashrc

then I did a locate on profile, this is what I found:
/etc/profile

a search on .profile:
/root/.profile


and then even .bash_profile
/etc/skel/.bash_profile

and they all have tons of the same stuff. I would like my prompt to be username@hostname:working directory (NOT THE ENTIRE PATH) I know I know, change the lowercase w to a W. I did that in all the places so I did figure that out. Well, I also would like to make it so that when I log in as root, it's red! 

Any help with all of this I would really appreciate it. I did search in these forums and they kind of help and also in gogle but just kind of a lot of weird text and not a clear definititon on where to put it! Oh yeah, 1 more thing, I want the top of my xterm to be the same and when I looked within /root/.bashrc I found this line:
# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"'
    ;;
*)
    ;;
esac\
but notice there is no lowercase w to change??? What do I do here?

Thanks a million.

---

### Post by bodhi.zazen on 2006-12-18
LOL dannyboy79

These files are hidden, so in nautilus you need to "show hidden files" or in a terminal type 

```
ls -a
```

Now your files:

.bash_profile is used for login shells only (were you see a log in prompt ...)
Mose people put a single line in there```
source ~/.bashrc
```

/etc/skel/ is the "source" for your system. When you create a new user, the system uses /etc/skel/.bashrc to create a /homw/new_user/.bashrc. Edit these fiels if you want to change this behavior for all new users ....

The configuration file for root is /root/.bashrc

So, add or edit the prompt you want in ~/.bashrc for your user and /root/.bashrc for root

Here is what I use for a prompt:> For users add the color of your choice:
PS1='\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$' #Green

PS1='\[\033[01;34m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$' #Blue

For root add this to /root/.bashrc
PS1='\[\033[01;31m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$' #Red

Now if you sudo su you will have a red prompt to remind you that you are ROOT.

For additional tips see here : [http://www.ubuntuforums.org/showthread.php?&t=204382](http://www.ubuntuforums.org/showthread.php?&t=204382)

---

### Post by dannyboy79 on 2006-12-18
> **bodhi.zazen said:**
> LOL dannyboy79

These files are hidden, so in nautilus you need to "show hidden files" or in a terminal type 

```
ls -a
```

Now your files:

.bash_profile is used for login shells only (were you see a log in prompt ...)
Mose people put a single line in there```
source ~/.bashrc
```

/etc/skel/ is the "source" for your system. When you create a new user, the system uses /etc/skel/.bashrc to create a /homw/new_user/.bashrc. Edit these fiels if you want to change this behavior for all new users ....

The configuration file for root is /root/.bashrc

So, add or edit the prompt you want in ~/.bashrc for your user and /root/.bashrc for root

Here is what I use for a prompt:

For additional tips see here : [http://www.ubuntuforums.org/showthread.php?&t=204382](http://www.ubuntuforums.org/showthread.php?&t=204382)


i didn't say I looked in nautilus, i stated that I did a locate (which is done in the terminal) and I put in .bashrc and I didn't have one in my home directory??? Don't know why?? Also, I do know that when using ls in the terminal it doesn't show hidden files, which are files that have a "." in the begining of them but thanks anyway. Thank you for answering my questions but you didn't answer all of them. How do I get the terminal in Xubuntu and Gnome to show only the current working directory and not the entire path but after thinking about this I changed my mind, I actually want it to show the entire path at the top of the terminal, I am only asking to learn something here, when I looked within /root/.bashrc, it contains a line about putting the prompt within the top of the terminal window (in the border so to speak) and it doesn't use the same way that the normal prompt uses, that's why I pasted what it has in there about the terminal preference. Can you explain this?

Also, you did explain what /etc/bash.bashrc is for?

what is /root/.profile for?

how do I get my aliases to work when I use sudo when I am logged in as myself? for instance, I want an alias that is interactive mode for when I do sudo mv or sudo cp or sudo rm. so I put alias cp='cp -i'. and it appears to work when I am logged in using sudo -i as root and it appears to work when I am myself, but when I sudo it doesn't work! I have added the aliases to everywhere that I can think of (basically all the files that I am asking about!).

thanks again for help me with the red prompt for when logged in as root. and for your other help but if you can answer these last questions I would appreciate it.

---

### Post by ayoli on 2006-12-18
hi
/etc/bash.bashrc is here to display a hint about sudo until you have used successfully sudo for the first time and another utility using command-not-found package that i dont know.
/root/.profile is used to load a ~/.bashrc for root if it exists
i tried to cp my .bashrc to /etc/bashrc then i changed my /root/profile to:
```
if [ "$BASH" ]; then
    if [ -f /etc/bashrc ]; then
        . /etc/bashrc
    fi
fi

```
then as user i remove my .bashrc from my user homedir and replace it by a link to /etc/bashrc like that:
```
cd $HOME && ln -sf /etc/bashrc .bashrc
```
so, like that root and my user have the same bashrc and all aliases work for both of them, but when i tried:
```
sudo ll /etc
```
where ll is an alias to ls -lh in my /etc/bashrc
it didn't work.
my explaination is sudo search for this command in $PATH and ignore aliases.

_edit:_ to confirm that i did:
```
[00:04:48@root.zone]:~ ># vi /usr/local/bin/ls-alias-test
```
```
#!/bin/sh

ls -lh $1
```
```
[00:06:24@root.zone]:~ ># chmod a+x /usr/local/bin/ls-alias-test 
```
then again in a shell as user:
```
sudo ls-alias-test /etc
```
and i worked :)
hope that answer to a part of your questions.

---

### Post by bodhi.zazen on 2006-12-18
> **dannyboy79 said:**
> How do I get the terminal in Xubuntu and Gnome to show only the current working directory and not the entire path but after thinking about this I changed my mind, I actually want it to show the entire path at the top of the terminal, I am only asking to learn something here, when I looked within /root/.bashrc, it contains a line about putting the prompt within the top of the terminal window (in the border so to speak) and it doesn't use the same way that the normal prompt uses, that's why I pasted what it has in there about the terminal preference. Can you explain this?

No, I am not sure on this one. XFCE and gnome use different terminal applications and configuration will be different.

I will try to look at that and re-post with more information ....

Alot of that should be in the menu options for your terminal and I am not sure it has to do with .bashrc

> Also, you did explain what /etc/bash.bashrc is for?

what is /root/.profile for?

/etc/bash.bashrc is a system wide configuration file for bash

From the bash man page:> When bash is invoked as an interactive login shell, or as a non-interactive shell with the --login option, it first reads and executes commands from the file /etc/profile, if that file exists. After reading that file, it looks for ~/.bash_profile, ~/.bash_login, and ~/.profile, in that order, and reads and executes commands from the first one that exists and is readable.

When an interactive shell that is not a login shell is started, bash reads and executes commands from /etc/bash.bashrc and ~/.bashrc, if these files exist.

Login = Starts with a Login:
you enter your user name and pw ....

Non-login = terminal or script.

Interactive = terminal (you enter commands)

Non-interactive = bash script (you enter commands in the script, but bash runs the script without interaction from you, unless of course you program interactivity into the script .... )

As a user ~ = /home/user_name
For root   ~ = /root

> how do I get my aliases to work when I use sudo when I am logged in as myself? for instance, I want an alias that is interactive mode for when I do sudo mv or sudo cp or sudo rm. so I put alias cp='cp -i'. and it appears to work when I am logged in using sudo -i as root and it appears to work when I am myself, but when I sudo it doesn't work! I have added the aliases to everywhere that I can think of (basically all the files that I am asking about!).

Put these aliases in /root/.bashrc

> thanks again for help me with the red prompt for when logged in as root. and for your other help but if you can answer these last questions I would appreciate it.

Bash and bash configuration is complex and I hope I did not confuse your further. In addition I have no idea of your knowledge base and so assumed in my first answer less knowledge then you possess, sorry for that assumption.

Here is a nice referance: [Bash Reference Manual](http://www.delorie.com/gnu/docs/bash/bashref_toc.html#SEC_Contents)

---

### Post by bodhi.zazen on 2006-12-18
> **ayoli said:**
> hi
/etc/bash.bashrc is here to display a hint about sudo until you have used successfully sudo for the first time and another utility using command-not-found package that i dont know.
/root/.profile is used to load a ~/.bashrc for root if it exists
i tried to cp my .bashrc to /etc/bashrc then i changed my /root/profile to:
```
if [ "$BASH" ]; then
    if [ -f /etc/bashrc ]; then
        . /etc/bashrc
    fi
fi

```

...

Ayoli : Good to see you. Always good to run across someone knowledgeable with bash and bash scripting ....

---

### Post by ayoli on 2006-12-18
> **bodhi.zazen said:**
> Ayoli : Good to see you. Always good to run across someone knowledgeable with bash and bash scripting ....
:)

---

### Post by bodhi.zazen on 2006-12-18
Add this to your .bashrc:
> # Set title of terminal to host name and working directory
# add "set title" to your .vimrc and title will change to file name when vim is opened !
host=$(uname -n)
if [ "${TERM}" = "xterm" -o "${TERM}" = "xterm-color" ]
then
   if [ -z "${BASH}" ]
   then
      echo "\033]2;${host}\007\033]1;${host}\007"
   else
      export PROMPT_COMMAND=\ 'echo -ne "\033]2;${host}:${PWD}\007\033]1;@${host}:${PWD}\007"'
   fi
fi

Then vim (or editor of choice) .vimrc

Add this line:```
set title
```

Now when you open a terminal (gnome or XFCE) your title will change to host:working directory.

When you open a file with vi (vim) the title will change to the working file name.

Enjoy 8)

---

