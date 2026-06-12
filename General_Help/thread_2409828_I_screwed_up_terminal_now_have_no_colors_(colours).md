---
title: "I screwed up terminal now have no colors (colours) but !  16.04 32 bit"
date: 2019-01-07
forum: General Help
---

### Post by adrian-h on 2019-01-07
OK I was removing files from home directory some .*.gz to get rid of all the gzip files I had placed in there, finger trouble meant I removed .*

Next time I rebooted and logged into remote terminal no colours, no blues and greens in listings etc just plain black background and white letters.

So I screwed up.

On another backup machine quick check of  hidden files with ls -la and I was missing .bashrc   .profile and  .bash_logout

So I copied them from the working machine, made sure with chmod they had the same permissions and rebooted, no change.

I have searched for this issue and found several responses including editing the files, but basically no change.

I am sat with the non color machine plugged into it directly so screen and keyboard no colors, a remote ssh terminal logged in gets the same no colors.

If I echo "$TERM" directly in console, I get   linux
If I echo "$TERM" from a ssh remote login, I get xterm-256color

These are the same in the working machine as well

I would like to get the colours back as it is very good to determine directories, scripts, gz files etc.

If I use ```
ls --color=auto
``` I will see blue directories and green scripts.

Do I have to offer some command so that it will use .bashrc .profile etc on startup?

For information here are the .bashrc and .profile contents

```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
case $- in
    *i*) ;;
      *) return;;
esac

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
if [ -z "${debian_chroot:-}" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color|*-256color) color_prompt=yes;;
esac

# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
#force_color_prompt=yes
```

```
# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile; for setting the umask
# for ssh logins, install and configure the libpam-umask package.
#umask 022

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
        . "$HOME/.bashrc"
    fi
fi

# set PATH so it includes user's private bin directories
PATH="$HOME/bin:$HOME/.local/bin:$PATH"
```

they are exactly the same on the PC with colors and no colors

I have also used ```
dircolors --print-database | less
```

To check they are both the same and they are.

Here is a listing of my local user directory

```
drwxr-xr-x 7 adrian adrian 4096 Jan  7 10:56 .                                                                                                                                                            
drwxr-xr-x 3 root   root   4096 Dec  8 00:18 ..                                                                                                                                                           
drwxrwxr-x 2 adrian adrian 4096 Jan  7 01:10 backups                                                                                                                                                      
-rw------- 1 adrian adrian 3814 Jan  7 10:58 .bash_history                                                                                                                                                
-rw-r--r-- 1 adrian adrian  221 Jan  7 08:35 .bash_logout                                                                                                                                                 
-rw-r--r-- 1 adrian adrian 1514 Jan  7 10:11 .bashrc                                                                                                                                                      
drwx------ 2 adrian adrian 4096 Jan  6 20:27 .cache                                                                                                                                                       
drwxrwxr-x 2 adrian adrian 4096 Dec  8 00:31 .nano                                                                                                                                                        
-rw-r--r-- 1 adrian adrian  662 Jan  7 09:06 .profile
drwxrwxr-x 2 adrian adrian 4096 Jan  7 10:37 scripts
-rw-rw-r-- 1 adrian adrian   66 Jan  7 01:21 .selected_editor
drwx------ 2 adrian adrian 4096 Jan  7 10:30 .ssh
-rw-r--r-- 1 adrian adrian    0 Jan  6 20:32 .sudo_as_admin_successful
```


Done hours searching on this and I do not understand where I have gone wrong and how to put it right?  Guessing is is more than just files in my localuser directory as everything seems to be the same.

Adrian

---

### Post by adrian-h on 2019-01-07
OK I just solved it, phew!

I found another post about something very similar this below, making sure I try to give credit

--------------------------------------------------------------------------
 You may want to copy the files from /etc/skel.
  cp -rT /etc/skel/ "$HOME"
  Those are the files which every newly created user starts with in the HOME folder, and are sufficient to be able to log in.
     
                    [share]("https://askubuntu.com/a/652395")[improve this answer]("https://askubuntu.com/posts/652395/edit")
                    
                    [edited Jul 24 '15 at 22:49]("https://askubuntu.com/posts/652395/revisions")     
                   
                                             
     
 
    
                                   answered Jul 24 '15 at 22:44     
              [URL="https://askubuntu.com/users/159370/gunnar-hjalmarsson"][IMG]https://i.stack.imgur.com/aZsF6.jpg?s=32&g=1[/IMG]
[/URL]     
              [Gunnar Hjalmarsson]("https://askubuntu.com/users/159370/gunnar-hjalmarsson")
--------------------------------------------------------------------------

So I did this, initially no change, so I logged out and then logged back in and now when I ls I have colours on both console and in remote terminal.

I am a happy bunny again and leave this post in case it helps others when they make the same mistake as me.

Adrian

---

### Post by howefield on 2019-01-07
> **adrian-h said:**
> ...initially no change, so I logged out and then logged back in and now when I ls I have colours on both console and in remote terminal.

The other option to make file changes to ~/.bashrc take effect is to use the command..

```
source ~/.bashrc
```

saves closing and reopening the terminal.

---

