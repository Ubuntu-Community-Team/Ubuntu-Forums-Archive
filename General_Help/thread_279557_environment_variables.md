---
title: "environment variables"
date: 2006-10-18
forum: General Help
---

### Post by petervdv on 2006-10-18
How do I change permanent the PATH variabele ?  (I want to add /opt)
With "export" it only lasts till the next login.
This is my .bashrc, what do I change?
```

cat /etc/bash.bashrc
# System-wide .bashrc file for interactive bash(1) shells.

# To enable the settings / commands in this file for login shells as well,
# this file has to be sourced in /etc/profile.

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, overwrite the one in /etc/profile)
PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '

# Commented out, don't overwrite xterm -T "title" -n "icontitle" by default.
# If this is an xterm set the title to user@host:dir
#case "$TERM" in
#xterm*|rxvt*)
#    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD}\007"'
#    ;;
#*)
#    ;;
#esac

# enable bash completion in interactive shells
#if [ -f /etc/bash_completion ]; then
#    . /etc/bash_completion
#fi

# sudo hint
if [ ! -e $HOME/.sudo_as_admin_successful ]; then
    case " $(groups) " in *\ admin\ *)
    if [ -x /usr/bin/sudo ]; then
        cat <<-EOF
        To run a command as administrator (user "root"), use "sudo <command>".
        See "man sudo_root" for details.

        EOF
    fi
    esac
fi

```

---

### Post by nikhilk on 2006-10-18
Add the following line at the end
```
PATH=/opt:$PATH
```

---

### Post by petervdv on 2006-10-18
No, that does not work.
When I log out and back in, /opt still isn't in my path.

Can anyone help please?

---

### Post by quixote on 2006-10-18
In the bash_profile in your home directory you add the following line:

> PATH=$PATH:/opt:/some_other_dir

And so on.  The $PATH, I think, means that the paths defined here are _added_ to the global PATH list rather than replacing it.  There are no spaces, the colons are important, and no colon at the end.

I'm a newbie, so it'd be good if one of the "carafe of dark roast" folks confirmed or corrected this!

I have a major frustration of my own to ask about:

HOW CAN I ADD TO THE $PATH SO THAT IT INCLUDES ALL SUBDIRS?

The problem is I've installed wine, but it can't find anything unless I enumerate every single one of the relevant subdirectores by hand.  Horrible.  Is there an easy way to alter the PATH statement above, or do anything, so that PATH understands that all subdirs in a given branch are included?

Postscript: I think because $PATH precedes /opt, it should retain your global PATH settings, i.e. the ones in your /etc/bash.bashrc  Perhaps the reason the previous suggestion didn't work for you is because I think if /opt comes first, then that becomes the only path on the system, and the $PATH variable has nothing in it except /opt.  (Am I making sense? :-? )

---

### Post by beejayzed on 2006-10-18
Put the export in ~/.gnomerc in the following format:
#!/bin/sh
CONTENT

And make it executable.

---

### Post by quixote on 2006-10-19
> **beejayzed said:**
> Put the export in ~/.gnomerc in the following format:
#!/bin/sh
CONTENT

And make it executable.

Erm.  Sorry to be dense, beejayzed, but:

1) what "export" are you talking about?  What is it that I'd be exporting?  Where am I exporting it from?

2) I use kde, so I assume there's an equivalent .kderc.  ?

3) The shell script "CONTENT" that you mention: could you give an example?  One that would leave all my existing paths intact and just add a whole branch of subdirectories without having to enumerate each one.

How does the shell script relate to whatever it is I should be putting in the .gnomerc?  What, exactly, would I be entering in the .gnomerc?

Thanks for your help!  You obviously know the answer.  Now if I could just understand it....

---

### Post by joshmachine on 2006-11-16
I'm sure you've already answered this, but what beejayzed was saying is that the content you want executed should replace the word CONTENT.  i.e. 

#!/bin/sh
export PATH=$PATH:/opt

"export" is basically the command that a script uses to makes an environment variable "stick" after it has exited. 

This is why your first script wasn't working.  

Summary.  In a bash script there are two ways to set variables.  

FOO="some value"
and
export BAR="another value"

while you are still in the script both of these variables are available.  After the script has exited, only BAR wil remain set.

---

### Post by goliathbeats on 2006-11-21
Hi i'm totally new to all this so bear with me please.  I have commands I'd like to run, but I don't know where to complete "export" commands.  Do I do this in root?  Terminal?  How or where do I actually get to perform bash commands such as export or path variables.  Thank you.

---

