---
title: "no bash color and autocompletion"
date: 2008-02-08
forum: General Help
---

### Post by el_itur on 2008-02-08
Suddenly my bash terminal doesn't show colors and doens't do tab autocompletion.

throwing ls --color=yes shows the colors but it is not persistent
I don't know how to work around the autocompletion stuf.

Note that i don't have a .bashrc on my home and my /etc/profile is :

```
# /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).

if [ "$PS1" ]; then
  if [ "$BASH" ]; then
    PS1='\u@\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
        . /etc/bash.bashrc
    fi
  else
    if [ "`id -u`" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi

umask 022

```


Thanks in advance

---

### Post by TheBoat on 2008-02-08
The following is located in my .bashrc file to enable color to ls:> # enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'
fi


---

### Post by el_itur on 2008-02-08
Sorry for the noobish question, do I have to restart the computer after this for change to happen?

---

### Post by TheBoat on 2008-02-08
no you just have to execute the file. For .bashrc, > . ~/.bashrcand for .profile,> . ~/.profile

---

### Post by el_itur on 2008-02-08
Well, thanks for the wuick replies, but it doesn't work, I think the problem should be somewhere else.

After aplying your suggested changes it behaves the same way than before, no colors, no autocompletion

---

### Post by TheBoat on 2008-02-08
Sorry I couldn't help. One note: the code I gave you was to execute the .profile in your home directory, but if you are adding it into the file in /etc/profile, then it should be:> . .profilein whatever folder the .profile you are editing is located.  I am not sure about auto completion but this is the only way I know of for turning on color for ls.

---

### Post by johnnyb1726 on 2008-02-08
Try making the changes to the .profile or .bashrc file in your home directory.

---

### Post by TheBoat on 2008-02-08
Yeah, he is right.  If you have a .bashrc file in your home directory (cd ~/), then you should edit that one instead of the file in /etc.

---

