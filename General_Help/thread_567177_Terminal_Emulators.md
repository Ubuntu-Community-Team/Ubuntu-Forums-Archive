---
title: "Terminal Emulators"
date: 2007-10-04
forum: General Help
---

### Post by blackrat47 on 2007-10-04
I migrated from Gentoo on my laptop (IBM Thinkpad X21) because sound and X both decided not to work.

Xubuntu is great- it runs light, and has everything I need.

One thing I am missing about the command-line gentoo install that I had, is colours in the terminal. Most of my navigation is carried out fropm the terminal (I am currently using the emulator which ships with Xubuntu), but no matter what i do it all just stays in black and white. This vastly reduces the effectiveness of Vim as an editor- one of its great strengths is syntax highlighting.

Is there an emulator which is pretty much like the bog standard gentoo install command line?

---

### Post by darknuala on 2007-10-04
Have you tried playing with the settings on Gnome-Terminal, or perhaps KONSOLE?  I'm not sure of the options available, but I know you can customize text colors, although to what extent I am not sure.

---

### Post by kellemes on 2007-10-04
You should edit your bashrc

This is mine..

```
alias ls='ls --color=auto'
#set -o vi

#PS1='[\u@\h \W]\$ '

##################################################
# Fancy PWD display function                               NIET GEBRUIKT!!!!!!!!!!!!!
##################################################
# The home directory (HOME) is replaced with a ~
# The last pwdmaxlen characters of the PWD are displayed
# Leading partial directory names are striped off
# /home/me/stuff          -> ~/stuff               if USER=me
# /usr/share/big_dir_name -> ../share/big_dir_name if pwdmaxlen=20
##################################################
bash_prompt_command() {
    # How many characters of the $PWD should be kept
    local pwdmaxlen=25
    # Indicate that there has been dir truncation
    local trunc_symbol=".."
    local dir=${PWD##*/}
    pwdmaxlen=$(( ( pwdmaxlen < ${#dir} ) ? ${#dir} : pwdmaxlen ))
    NEW_PWD=${PWD/#$HOME/\~}
    local pwdoffset=$(( ${#NEW_PWD} - pwdmaxlen ))
    if [ ${pwdoffset} -gt "0" ]
    then
        NEW_PWD=${NEW_PWD:$pwdoffset:$pwdmaxlen}
        NEW_PWD=${trunc_symbol}/${NEW_PWD#*/}
    fi
}


bash_prompt() {
    case $TERM in
     xterm*|rxvt*|gnome-terminal*)
         local TITLEBAR='\[\033]0;\u: ${PWD}\007\]'
          ;;
     *)
         local TITLEBAR=""
          ;;
    esac
    local NONE="\[\033[0m\]"    # unsets color to term's fg color
    
    # regular colors
    local K="\[\033[0;30m\]"    # black
    local R="\[\033[0;31m\]"    # red
    local G="\[\033[0;32m\]"    # green
    local Y="\[\033[0;33m\]"    # yellow
    local B="\[\033[0;34m\]"    # blue
    local M="\[\033[0;35m\]"    # magenta
    local C="\[\033[0;36m\]"    # cyan
    local W="\[\033[0;37m\]"    # white
    
    # empahsized (bolded) colors
    local EMK="\[\033[1;30m\]"
    local EMR="\[\033[1;31m\]"
    local EMG="\[\033[1;32m\]"
    local EMY="\[\033[1;33m\]"
    local EMB="\[\033[1;34m\]"
    local EMM="\[\033[1;35m\]"
    local EMC="\[\033[1;36m\]"
    local EMW="\[\033[1;37m\]"
    
    # background colors
    local BGK="\[\033[40m\]"
    local BGR="\[\033[41m\]"
    local BGG="\[\033[42m\]"
    local BGY="\[\033[43m\]"
    local BGB="\[\033[44m\]"
    local BGM="\[\033[45m\]"
    local BGC="\[\033[46m\]"
    local BGW="\[\033[47m\]"
    
    local UC=$Y                 # user's color
    [ $UID -eq "0" ] && UC=$R   # root's color

#if [ ${UID} -eq 0 ]; then
#	UC=$R
#fi
 
    PS1="${EMB}[${UC}\u@\H ${EMK}\${PWD}${EMK}]${UC}\\$ ${NONE}"
#    PS1="${EMK}[${UC}\u ${EMB}\${PWD}${EMK}]${UC}\\$ ${NONE}"
#    PS1="$TITLEBAR ${EMK}[${UC}\u${EMK}@${UC}\h ${EMB}\${PWD}${EMK}]${UC}\\$ ${NONE}"
    # without colors: PS1="[\u@\h \${PWD}]\\$ "
}

#PROMPT_COMMAND=bash_prompt_command
bash_prompt
unset bash_prompt

```

---

### Post by RedSquirrel on 2007-10-04
> **blackrat47 said:**
> One thing I am missing about the command-line gentoo install that I had, is colours in the terminal. Most of my navigation is carried out fropm the terminal (I am currently using the emulator which ships with Xubuntu), but no matter what i do it all just stays in black and white. This vastly reduces the effectiveness of Vim as an editor- one of its great strengths is syntax highlighting.

Is there an emulator which is pretty much like the bog standard gentoo install command line?

I use uxterm.

You mean the terminal itself has no colors, even for things like directories, symbolic links and so on? I would think for that you would just need this as an alias:

```
alias ls='ls --color=auto'
```That should already be in your ~/.bashrc.

You can also have a color prompt. You just have to comment some lines in .bashrc and uncomment some others. The lines for that are all in the default .bashrc.

Which vim package are you using? The one that is installed by default is most likely vim-tiny which doesn't support syntax highlighting. Have a look at the different vim-* packages in the repositories. There is one called "vim" that has a standard set of features. I install vim-gtk because sometimes I like to use GVIM and its fancy tabs. :)

And you might have to turn the highlighting on with:

```
syntax on
```in your ~/.vimrc

---

