---
title: "how to edit $path"
date: 2013-12-31
forum: General Help
---

### Post by engine on 2013-12-31
```
put ... line into your .bashrc or .profile file in ~/
``` is a familiar suggestion, but I don't have either a .bashrc or a .profile in my root :-{ and yes, I am listing all hidden files. Hints and tips welcome; I don't think I've ever remembered the instructions from one (infrequent) change to the next.

Lubuntu 12.04.3 LXLE &#8210; just installed it off a cover CD to try out, though I suspect there will be a more recent release to upgrade to.

---

### Post by deadflowr on 2013-12-31
.bashrc and .profile are in the users home folder.
the ~ = /home/user.
if you run from a terminal
```
cat ~/.bashrc
```
you should get the output for the bashrc file.

Of course, if you're running as root, then that is probably a different can of worms.
root has it's own home folder, completely separated from the normal users home folder.
/root, it is normally locked for normal users.

---

### Post by vasa1 on 2013-12-31
I prefer editing /etc/environment.

---

### Post by bab1 on 2013-12-31
> **vasa1 said:**
> I prefer editing /etc/environment.

This edits all users paths.  You should use ~/.bashrc for your own personal path additions.

---

### Post by engine on 2014-01-01
```
cat ~/.bashrc
```
returns
```
cat: /home/ngn/.bashrc: No such file or directory
```

Following the easy, go with the flow installation proposed by the DVD, there is no separate root user configured; for sudo operations, I just need to authenticate with my own password.

---

### Post by kajoky on 2014-01-01
I think, if you do not have a .bashrc in your home folder, you could create it and put in the $PATH that you need.
Maybe copy the $PATH from /etc/environment and modify that as needed for your situation.

---

### Post by deadflowr on 2014-01-01
> **engine said:**
> ```
cat ~/.bashrc
```
returns
```
cat: /home/ngn/.bashrc: No such file or directory
```

Following the easy, go with the flow installation proposed by the DVD, there is no separate root user configured; for sudo operations, I just need to authenticate with my own password.

I don't understand. Did you configure the root user to be used?
By default, root is locked in Ubuntu.
The first user you create during installation gets administration rights to do system level work.

---

### Post by bab1 on 2014-01-01
> **engine said:**
> ```
cat ~/.bashrc
```
returns
```
cat: /home/ngn/.bashrc: No such file or directory
```

Following the easy, go with the flow installation proposed by the DVD, there is no separate root user configured; for sudo operations, I just need to authenticate with my own password.

So what is in the home directory of this user?   How was this user created?   Post the output of this```
ls -al ~
```

There is a copy of the .bashrc at:  /etc/skel/.bashrc.  This file is installed when you create any mortal (human) user.

---

### Post by engine on 2014-01-05
ls -al ~returns
```

drwxr-xr-x 36 ngn  ngn   4096 Jan  5 13:58 .
drwxr-xr-x  3 root root  4096 Dec 31 12:20 ..
-rw-------  1 ngn  ngn    847 Jan  2 20:45 .bash_history
drwx------  9 ngn  ngn   4096 Jan  1 13:13 .cache
drwxr-xr-x 20 ngn  ngn   4096 Jan  1 14:05 .config
drwxr-xr-x  3 ngn  ngn   4096 Dec 31 12:20 .conky
-rw-r--r--  1 ngn  ngn   2915 Dec 31 12:20 .conkyrc
drwx------  3 ngn  ngn   4096 Dec 31 12:31 .dbus
drwxr-xr-x  2 ngn  ngn   4096 Dec 31 12:20 Desktop
-rw-r--r--  1 ngn  ngn     26 Jan  5 13:58 .dmrc
drwxr-xr-x  2 ngn  ngn   4096 Jan  1 14:04 Documents
drwxr-xr-x  3 ngn  ngn   4096 Jan  5 14:38 Downloads
drwxr-xr-x  2 ngn  ngn   4096 Jan  1 11:58 .fontconfig
drwxr-xr-x  4 ngn  ngn   4096 Jan  5 13:58 .gconf
drwxr-xr-x 24 ngn  ngn   4096 Jan  1 12:03 .gimp-2.8
-rw-r-----  1 ngn  ngn      0 Jan  1 13:14 .gksu.lock
drwxr-xr-x  4 ngn  ngn   4096 Jan  2 20:35 .gnome2
drwx------  2 ngn  ngn   4096 Dec 31 14:51 .gnome2_private
drwxr-xr-x  3 ngn  ngn   4096 Dec 31 12:20 .gnome-commander
drwx------  2 ngn  ngn   4096 Dec 31 15:04 .gnupg
-rw-rw-r--  1 ngn  ngn    282 Jan  1 13:53 .gorillarc
-rw-------  1 ngn  ngn      0 Dec 31 18:15 .goutputstream-G1IC9W
drwxrwxr-x  2 ngn  ngn   4096 Dec 31 14:50 .gstreamer-0.10
drwxr-xr-x  7 ngn  ngn   4096 Dec 31 12:20 .guayadeque
dr-x------  2 ngn  ngn      0 Jan  5 13:58 .gvfs
drwxrwxr-x  4 ngn  ngn   4096 Jan  1 13:48 .icedtea
drwxr-xr-x  5 ngn  ngn   4096 Dec 31 12:20 .icons
drwxrwxr-x  4 ngn  ngn   4096 Jan  1 17:24 .java
drwxr-xr-x  3 ngn  ngn   4096 Dec 31 12:20 .local
drwxrwxr-x  2 ngn  ngn   4096 Jan  1 14:05 .mono
drwxr-xr-x  4 ngn  ngn   4096 Dec 31 12:20 .mozilla
drwxr-xr-x  4 ngn  ngn   4096 Nov 16 20:26 Music
drwxr-xr-x  3 ngn  ngn   4096 Jan  1 12:03 Pictures
drwxr-xr-x  2 ngn  ngn   4096 Dec 31 12:20 Public
drwx------  2 ngn  ngn   4096 Jan  5 13:58 .pulse
-rw-------  1 ngn  ngn    256 Dec 31 12:31 .pulse-cookie
-rw-rw-r--  1 ngn  ngn    413 Jan  5 14:40 .recently-used
drwxr-xr-x  3 root root  4096 Jan  1 13:17 .sketsa
drwx------  2 ngn  ngn   4096 Dec 31 15:04 .ssh
drwxr-xr-x  2 ngn  ngn   4096 Dec 31 12:20 Templates
drwxr-xr-x  3 ngn  ngn   4096 Dec 31 12:20 .themes
drwx------  4 ngn  ngn   4096 Dec 31 16:58 .thumbnails
drwxr-xr-x  2 ngn  ngn   4096 Dec 31 12:20 Videos
-rw-------  1 ngn  ngn   1556 Dec 31 16:57 .viminfo
-rw-------  1 ngn  ngn     56 Jan  5 13:58 .Xauthority
drwx------  3 ngn  ngn   4096 Jan  1 13:37 .xchat2
-rw-r--r--  1 ngn  ngn     14 Dec 31 12:31 .xscreensaver
-rw-------  1 ngn  ngn  25657 Jan  5 14:56 .xsession-errors
-rw-------  1 ngn  ngn   7463 Jan  4 18:50 .xsession-errors.old

```

There is no /etc/skel/.bashrc. Should I be afraid of having somehow created a non-human user? <vbg>

---

### Post by Bucky Ball on 2014-01-05
Have you tried downloading Lubuntu yourself, burning a disk and booting from that? Cover CDs can sometimes come in strange, exotic and custom remixes.

[QUOTE=engine]Following the easy, go with the flow installation proposed by the DVD, there is no separate root user configured; for sudo operations, I just need to authenticate with my own password.[/QUOTE]

This is new and it sounds like it is some kind of 'try before you buy' remix.

---

### Post by bab1 on 2014-01-05
> **engine said:**
> 
There is no /etc/skel/.bashrc. Should I be afraid of having somehow created a non-human user? <vbg>

Non human users are called system users.  I wouldn't be afraid of creating a system user.  I'm more interested in how you could install a Linux OS and not have a /etc/skell/.bashrc file.  This is a basic Debian/Ubuntu file.

The root user is configured.  The password is disabled.  When you use sudo you are temporarily running commands as the root user.  Sudo stands for Switch User and Do.  This is a normal part of the Ubuntu install.  

My thoughts at this time is to backup the data you have in your home directory and reinstall the OS.

---

### Post by Impavidus on 2014-01-05
What is that .sketsa directory? It may not be related at all, but it's root-owned, which shouldn't happen in your home directory.

Besides, Lubuntu 12.04 is not an LTS release.

---

### Post by bab1 on 2014-01-05
> **Impavidus said:**
> What is that .sketsa directory? It may not be related at all, but it's root-owned, which shouldn't happen in your home directory.

Besides, Lubuntu 12.04 is not an LTS release.

The /etc/skel directory is where the system stores the files that are used to create a new user.  They aren't in the users home directory at all.  When the user is created the system copies the .bashrc and .profile to the new users directory and changes the ownership to the new user.

---

### Post by jamesisin on 2014-01-05
It is common for a user NOT to have a .bashrc file, because for a default user it would be empty anyway.  None of my Ubuntu installations have an /etc/skell/.bashrc and that also seems normal (for the aforementioned reason).  If you do not have a ~/.bashrc file you can just create your own.  If it doesn't work, delete it (you may need to either ssh in or use a different user account to fix yours, so keep that in mind as you prepare things).

---

### Post by bab1 on 2014-01-05
> **jamesisin said:**
> It is common for a user NOT to have a .bashrc file, because for a default user it would be empty anyway.  None of my Ubuntu installations have an /etc/skell/.bashrc and that also seems normal (for the aforementioned reason).  If you do not have a ~/.bashrc file you can just create your own.  If it doesn't work, delete it (you may need to either ssh in or use a different user account to fix yours, so keep that in mind as you prepare things).

The directory is /etc/skel NOT as you have noted  /etc/skell.  Consider this from the man page of **adduser**```
       adduser will **copy files from SKEL into the home directory **and prompt  for  finger  (gecos)
       information  and a password.  The gecos may also be set with the --gecos option.  With the
       --disabled-login option, the account will be created but will be disabled until a password
       is  set. The --disabled-password option will not set a password, but login is still possi&#8208;
       ble (for example with SSH RSA keys).  To set up an encrypted home directory  for  the  new
       user,  add  the  --encrypt-home  option. 
```

The default .bashrc (which is installed when bash is the default shell) is ```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines or lines starting with space in the history.
# See bash(1) for more options
HISTCONTROL=ignoreboth

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# If set, the pattern "**" used in a pathname expansion context will
# match all files and zero or more directories and subdirectories.
#shopt -s globstar

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color) color_prompt=yes;;
esac

# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
#force_color_prompt=yes

if [ -n "$force_color_prompt" ]; then
    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
	# We have color support; assume it's compliant with Ecma-48
	# (ISO/IEC-6429). (Lack of such support is extremely rare, and such
	# a case would tend to support setf rather than setaf.)
	color_prompt=yes
    else
	color_prompt=
    fi
fi

if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac

# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi

# some more ls aliases
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'

# Add an "alert" alias for long running commands.  Use like so:
#   sleep 10; alert
alias alert='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '\''s/^\s*[0-9]\+\s*//;s/[;&|]\s*alert$//'\'')"'

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
    . /etc/bash_completion
fi

```...this is a little more than an empty file for the user to fill in.

In addition the .profile file comes from /etc/skel also.

---

### Post by jamesisin on 2014-01-07
I see.  Thanks for correcting my file path.  I may have overstated the matter.

A **.bashrc** file is not a required file.  If you *cat* your **.profile** file you will note the line "# include .bashrc if it exists".  Nonetheless, it would appear that Ubuntu *does* by default use one.  In which case I suppose the user could *cp /etc/skel/.bashrc ~/.bashrc* and then take ownership of that new file.

---

### Post by bab1 on 2014-01-07
> **jamesisin said:**
> I see.  Thanks for correcting my file path.  I may have overstated the matter.

A **.bashrc** file is not a required file.  If you *cat* your **.profile** file you will note the line "# include .bashrc if it exists".  Nonetheless, it would appear that Ubuntu *does* by default use one.  In which case I suppose the user could *cp /etc/skel/.bashrc ~/.bashrc* and then take ownership of that new file.

If you look at the OP's listing of his home directory you will see that there is NO **.profile **in that directory either.  Yes all that stuff is in a .profile and in the .bashrc.  The problem is the OP has **neither** file.

Go look at other distros.  You will see they have /etc/skel directories.  It is the scripts used to install the OS along with the adduser scripts that use this directory for the skeletal files to setup users.  If you wanted to add a file for a each new user you can use /etc/skel to do that also.

---

### Post by jamesisin on 2014-01-07
Can't he just do the same with his .profile file?

```
cp /etc/skel/.profile ~/.profile
```

... and then fix the ownership of the file.

---

### Post by bab1 on 2014-01-08
> **jamesisin said:**
> Can't he just do the same with his .profile file?

```
cp /etc/skel/.profile ~/.profile
```

... and then fix the ownership of the file.

I don't think the OP has *any* /etc/skel files.  That's why I recommended reinstalling a known good ISO.

---

### Post by jamesisin on 2014-01-09
If that is the case then you are probably right.  Odd though.

---

### Post by engine on 2014-01-10
OK, I believe I am now running lubuntu 13.10 as suggested ... but even though the ISO image verified when I burnt it, there was a message about "failed to install software" during the installation procedure and I am now left with a number of "no parking" signs on the desktop. I don't mind trying to install these missing packages through synaptic, but what are they?
[LIST]
[*]the launchpad to the left contains FileManagerPCManFM, three placeholders for missing software, Pidgin, four more placeholders, Task Manager and Lubuntu Software Centre
[*]the taskbar (bottom left) contains the Start button equivalent, a folder list, three placeholders, "left click to iconify", and the two desktop icons
[*]the statusbar (bottom right) shows Volume control, Wired network &#8210; luckily! &#8210; followed by two placeholders, time/date and one last placeholder
[/LIST]
Once I've got this sorted, I'll install my non-synaptic software again and get back to the question of updating $PATH. No-one ever said it was going to be easy <g>

---

### Post by bab1 on 2014-01-10
> **engine said:**
> 
Once I've got this sorted, I'll install my non-synaptic software again and get back to the question of updating $PATH. No-one ever said it was going to be easy <g>
The question right now is do you have these two files in your home directory```
.bashrc

.profile
```

To check all you need to do is this```
ls -al ~
```

If you want to check using the GUI you will need to do this before looking ```
Ctrl + h
```...this makes the hidden files visible.

---

### Post by engine on 2014-01-19
OK, back online after a busy week elsewhere … with some progress to report: I'm now running lubuntu 13.04

Still no home/ngn/.bashrc, though I do have a .bash-history. On the other hand, I do at least have a .bashrc and a .profile in /etc/skel.

What do I need to do next in order to resolve this should-be-so-simple question of updating my $PATH? Thanks in advance!

---

### Post by bab1 on 2014-01-19
> **engine said:**
> OK, back online after a busy week elsewhere &#8230; with some progress to report: I'm now running lubuntu 13.04

Still no home/ngn/.bashrc, though I do have a .bash-history. On the other hand, I do at least have a .bashrc and a .profile in /etc/skel.

What do I need to do next in order to resolve this should-be-so-simple question of updating my $PATH? Thanks in advance!

How did you create the user ngn?  

Post the output of ```
getent passwd |grep 100
```

---

### Post by engine on 2014-01-21
Now on Lubuntu 13.10; still no /home/ngn/.bashrc, but at least I now have a .bashrc in etc/skel

What should I do next, with a view to being able to edit $PATH?

---

### Post by bab1 on 2014-01-21
> **engine said:**
> Now on Lubuntu 13.10; still no /home/ngn/.bashrc, but at least I now have a .bashrc in etc/skel

What should I do next, with a view to being able to edit $PATH?

I would start by answering my previous post.  ;-)

---

### Post by engine on 2014-01-23
Oops &#8210; managed to overlook that. Here's the info:

```
prompt$ getent passwd |grep 100
libuuid:x:100:101::/var/lib/libuuid:/bin/sh
ngn:x:1000:1000:myName,,,:/home/ngn:/bin/bash
```

---

### Post by bab1 on 2014-01-23
> **engine said:**
> Oops &#8210; managed to overlook that. Here's the info:

```
prompt$ getent passwd |grep 100
libuuid:x:100:101::/var/lib/libuuid:/bin/sh
ngn:x:1000:1000:myName,,,:/home/ngn:/bin/bash
```

There was 2 questions.  The other question was: How did you create the user ngn?   

Was this user created when you installed the OS?

[COLOR="#0000FF"]**Edit:** In the end the files in /etc/skel (.profile and .bashrc) should be copied to your home directory and the ownership of them should be changed to the user (in your case -- chown ngn:ngn and permissions of 644).  Once we can modify the path setting. [/COLOR]

---

