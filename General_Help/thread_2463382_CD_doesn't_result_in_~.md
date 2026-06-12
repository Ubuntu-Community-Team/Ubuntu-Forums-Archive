---
title: "CD doesn't result in ~/"
date: 2021-06-09
forum: General Help
---

### Post by NertSkull on 2021-06-09
Strange question, and not a big deal. But normally when you type cd into the terminal you get the prompt

user@host:~

But now on my computer when I type cd I get this instead

user@host:/home/user

It's obviously the same directory, so it's working okay. But I'm sure there's a way to set it to the first style. But I have no idea what to search for to change that.

---

### Post by QIII on 2021-06-09
Is that followed by "#"?

That means you are in super-user mode.  Type "exit" to get back to your normal user mode.

You might be logged in as root, in which case you shouldn't.

---

### Post by &amp;KyT$0P# on 2021-06-09
What shell are you using?  Can you please share your configuration file for it? (If you're using [FONT=Courier New]bash[/FONT] it's [FONT=Courier New]~/.bashrc[/FONT] )

---

### Post by NertSkull on 2021-06-10
> **QIII said:**
> Is that followed by "#"?

That means you are in super-user mode.  Type "exit" to get back to your normal user mode.

You might be logged in as root, in which case you shouldn't.

I should have posted the entirety, sorry, but no, I'm not logged in as root.

[FONT=monospace][COLOR=#000000]user@root:/home/user$ [/COLOR]

[/FONT]
> **halogen2 said:**
> What shell are you using?  Can you please share your configuration file for it? (If you're using [FONT=Courier New]bash[/FONT] it's [FONT=Courier New]~/.bashrc[/FONT] )

Pretty sure I'm using bash.  Here is my bashrc.  Only thing I remember changing is a couple of aliases.

```

[FONT=monospace]1 # ~/.bashrc: executed by bash(1) for non-login shells.
  2 # see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
  3 # for examples
  4 
  5 # If not running interactively, don't do anything
  6 case$-in
  7     *i*);;
  8 . *)return;;
  9 esac
 10 
 11 # don't put duplicate lines or lines starting with space in the history.
 12 # See bash(1) for more options
 13 **HISTCONTROL**=ignoreboth 
 14 
 15 # append to the history file, don't overwrite it
 16 shopt -s histappend                                 
 17 
 18 # for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
 19 **HISTSIZE**=1000
 20 **HISTFILESIZE**=2000
 21 
 22 # check the window size after each command and, if necessary,
 23 # update the values of LINES and COLUMNS.
 24 shopt -s checkwinsize                                           
 25 
 26 # If set, the pattern "**" used in a pathname expansion context will
 27 # match all files and zero or more directories and subdirectories.
 28 #shopt -s globstar
 29 
 30 # make less more friendly for non-text input files, see lesspipe(1)
 31 [-x /usr/bin/lesspipe ] && eval"$(SHELL=/bin/sh lesspipe)"
 32 
 33 # set variable identifying the chroot you work in (used in the prompt below)
 34 if [-z"${debian_chroot:-}"]&&[-r /etc/debian_chroot ];then
 35 **debian_chroot**=$(cat /etc/debian_chroot)
 36 fi
 37 
 38 # set a fancy prompt (non-color, unless we know we "want" color)
 39 case"$TERM"in
 40     xterm-color|*-256color)**color_prompt**=yes;;
 41 esac
 42 
 43 # uncomment for a colored prompt, if the terminal has the capability; turned
 44 # off by default to not distract the user: the focus in a terminal window
 45 # should be on the output of commands, not on the prompt
 46 #force_color_prompt=yes
 47 
 48 if [-n"$force_color_prompt"];then
 49 if [-x /usr/bin/tput ]&&tput setaf 1>&/dev/null;then
 50 # We have color support; assume it's compliant with Ecma-48
 51 # (ISO/IEC-6429). (Lack of such support is extremely rare, and such
 52 # a case would tend to support setf rather than setaf.)
 53 **color_prompt**=yes 
 54 else
 55 **color_prompt**= 
 56 fi
 57 fi
 58 
 59 if ["$color_prompt"=yes];then
 60 PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
 61 else
 62 PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
 63 fi
 64 unset** color_prompt force_color_prompt**
 65 
 66 # If this is an xterm set the title to user@host:dir
 67 case"$TERM"in
 68 xterm*|rxvt*)
 69 PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
 70 ;;
 71 *)
 72 ;;
 73 esac
 74 
[FONT=monospace]75 # enable color support of ls and also add handy aliases
 76 if [-x /usr/bin/dircolors ];then
 77 test-r ~/.dircolors &&eval"$(dircolors -b ~/.dircolors)"||eval"$(dircolors -b)"
 78 alias **ls**='ls --color=auto'
 79 #alias dir='dir --color=auto'
 80 #alias vdir='vdir --color=auto'
 81 
 82 alias **grep**='grep --color=auto'
 83 alias **fgrep**='fgrep --color=auto'
 84 alias **egrep**='egrep --color=auto'
 85 fi
 86 
 87 # colored GCC warnings and errors
 88 #export GCC_COLORS='error=01;31:warning=01;35:note=01;36:caret=01;32:locus=01:quote=01'
 89 
 90 # some more ls aliases
 91 alias **ll**='ls -ahlF'
 92 alias **la**='ls -A'
 93 alias**l**='ls -CF'
 94 alias **svim**='sudo -E nvim'
 95 
 96 # Add an "alert" alias for long running commands.  Use like so:
 97 #   sleep 10; alert
 98 alias **alert**='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '\''s/^\s*[0-9]\+\s*//;s/[;&|]\s*alert$//'\'')"'
 99 
100 # Alias definitions.
101 # You may want to put all your additions into a separate file like
102 # ~/.bash_aliases, instead of adding them here directly.
103 # See /usr/share/doc/bash-doc/examples in the bash-doc package.
104 
105 if [-f ~/.bash_aliases ];then
106  . ~/.bash_aliases                                 
107 fi
108 
109 # enable programmable completion features (you don't need to enable
110 # this, if it's already enabled in /etc/bash.bashrc and /etc/profile
111 # sources /etc/bash.bashrc).
112 if ! shopt -oq posix;then
113 if [-f /usr/share/bash-completion/bash_completion ];then
114  . /usr/share/bash-completion/bash_completion                                 
115 elif[-f /etc/bash_completion ];then
116  . /etc/bash_completion                                 
117 fi
118 fi
[/FONT][/FONT]
```

---

### Post by TheFu on 2021-06-10
The new version of bash has changed a few defaults.
Check the value of the PS1 environment variable.
I have 
```
PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
```
The bash manpage has information about all the different prompt variables.  PS1, PS2, PS3, PS4 and how they can be used.
```
       PS1    The  value  of this parameter is expanded (see _PROMPTING_
              below) and used as the primary prompt string.   The  de&#8208;
              fault value is ``\s-\v\$ ''.
       PS2    The  value of this parameter is expanded as with PS1 and
              used as the secondary prompt string.  The default is ``>
              ''.
       PS3    The  value  of  this parameter is used as the prompt for
              the select command (see SHELL GRAMMAR above).
       PS4    The value of this parameter is expanded as with PS1  and
              the  value  is printed before each command bash displays
              during an execution trace.  The first character  of  the
              expanded  value  of PS4 is replicated multiple times, as
              necessary, to indicate multiple levels  of  indirection.
              The default is ``+ ''.
```

---

### Post by NertSkull on 2021-06-10
> **TheFu said:**
> The new version of bash has changed a few defaults.
Check the value of the PS1 environment variable.
I have 
```
PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
```



Using printenv it looks like I do not have PS1 set.

I set it to match yours in my /etc/environment.  But it didn't change the behavior after logging out/in.

I'm still trying to grasp how to use the PS variables you mentioned, no luck yet though.

---

### Post by TheFu on 2021-06-10
I have never, ever, touched,  /etc/environment in my career.  Defaults are there to protect us.
Only modify your personal files - those in HOME.

---

### Post by NertSkull on 2021-06-10
Good call!  I undid that and modified my .bashrc like I should have.  Still no go.  I noticed it already has some PS1 defined, I tried export PS1 at the top and bottom of the .bashrc and that didn't do much.

---

### Post by GhX6GZMB on 2021-06-10
I've never had cd result in ~/
Normal is ~$

---

### Post by &amp;KyT$0P# on 2021-06-10
> **NertSkull said:**
> Using printenv it looks like I do not have PS1 set.

You check it by running
```
echo "$PS1"
```

Like TheFu said, compare that to the bash manpage, specifically the "PROMPTING" section.

Also can you make sure the output of
```
echo "$HOME"
```
is what you expect?

---

### Post by NertSkull on 2021-06-10
> **ml9104 said:**
> I've never had cd result in ~/
Normal is ~$
Sorry, that's my fault for not catching a type while typing on my phone last night.  Poor form to ruin the post title. 

See below for direct copy/paste

> **halogen2 said:**
> You check it by running
```
echo "$PS1"
```

Like TheFu said, compare that to the bash manpage, specifically the "PROMPTING" section.

Also can you make sure the output of
```
echo "$HOME"
```
is what you expect?


```

[FONT=monospace][COLOR=#000000]dan@indigo:/home/dan$ cd [/COLOR]
dan@indigo:/home/dan$ echo "$PS1" 
${debian_chroot:+($debian_chroot)}\u@\h:\w\$  
dan@indigo:/home/dan$ echo "$HOME" 
/home/dan/ 
dan@indigo:/home/dan$ cd
dan@indigo:/home/dan$
[/FONT]
```[FONT=monospace]

[/FONT]

---

### Post by TheFu on 2021-06-10
> **NertSkull said:**
>  
dan@indigo:/home/dan$ echo "$HOME" 
/home/dan[COLOR="#FF0000"]/[/COLOR]  

The trailing '/' is incorrect.  Check the password entry for the user:
```
$ getent passwd dan
```
Bet it has a trailing / in the HOME directory field.  Try fixing that.  I would use **sudo vipw** for a quick change.

---

### Post by NertSkull on 2021-06-10
> **TheFu said:**
> The trailing '/' is incorrect.  Check the password entry for the user:
```
$ getent passwd dan
```
Bet it has a trailing / in the HOME directory field.  Try fixing that.  I would use **sudo vipw** for a quick change.

Bingo!  That fixed it.  Thanks so much for humoring me.  I appreciate everyone's help and patience with such a trivial problem!

---

