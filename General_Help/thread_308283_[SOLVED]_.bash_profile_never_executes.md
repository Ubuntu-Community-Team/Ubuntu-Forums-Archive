---
title: "[SOLVED] .bash_profile never executes"
date: 2006-11-27
forum: General Help
---

### Post by Falcorian on 2006-11-27
I've run into something that's confusing me. I did some google searches and searched the forum, but nothing came up that answered my question.

My .bash_profile never seems to load. I first noticed this when my ~/bin was not added to my path. I've restarted, I've source .bash_profile, I've bash .bash_profile.

Using source .bash_profile allows me access to all the scripts I have in ~/bin in that one terminal, but all others use my old path.

My .bash_profile:

```

# ~/.bash_profile: executed by bash(1) for login shells.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/login.defs
#umask 022

# include .bashrc if it exists
if [ -f ~/.bashrc ]; then
    . ~/.bashrc
fi

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH="${PATH}":~/bin
    export PATH
fi

```

I suppose I could just add to my path in my .bashrc, which runs fine with every terminal, but that seems like a work around.


Any ideas what's up?

---

### Post by mssever on 2006-11-27
Unless I'm mistaken, .bash_profile is only sourced by login shells. By default, gnome_terminal (and presumably others) doesn't start a login shell, although you can configure it to do so.

To test this, I put echo hi in my .bash_profile on my server. When I sshed to it, I see the echo. So I put the echo in my laptop's .bash_profile (the computer I'm sitting at). Opening up a new gnome-terminal didn't produce the echo, but sshing from my server to the laptop did.

I put all my config in .bashrc. Stuff that should only run in interactive shells goes after this: ```
# If not running interactively, don't do anything
[ -z "$PS1" ] && return
``` The idea is that PS1 only gets set by interactive shells.

---

### Post by Falcorian on 2006-11-27
I figured it must be something like that from another thread I found, but I wasn't sure...


Odd that the if ~/bin exists, add it to path comes in .bash_profile by default and not .bashrc, but what the heck. ;)

Guess I'll link .bash_profile to .bashrc and use your return trick.


EDIT: Oh yes, and thanks for the quick reply! Cheers! :)

---

### Post by mssever on 2006-11-27
> **Falcorian said:**
> Odd that the if ~/bin exists, add it to path comes in .bash_profile by default and not .bashrc, but what the heck. ;)

That was one of the first things I "fixed" after installing... :)

---

