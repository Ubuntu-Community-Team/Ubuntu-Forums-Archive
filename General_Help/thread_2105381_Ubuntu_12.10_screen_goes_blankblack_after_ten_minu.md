---
title: "Ubuntu 12.10 screen goes blank/black after ten minutes"
date: 2013-01-15
forum: General Help
---

### Post by Hewjr100 on 2013-01-15
I tried this command:   sudo xset s off but still the screen goes blank/black.  Is there really any solution to this?  If so let me know, because this was the last one I tried.

Henry

---

### Post by c901906 on 2013-01-15
I put this in ~/.profile:

xset s 0 0

Worked for me.

---

### Post by Hewjr100 on 2013-01-15
Did not work.  Put it at bottom just above fi.

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

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"

xset s 0 0
fi

Was this right.

Henry

---

### Post by c901906 on 2013-01-15
I did it the very first line of ~/.profile before the comments.

Also, it won't take affect until you log out and back in again. 

You should be able to verify that the command runs with:

xset q | grep timeout

Should have a value of zero.


If it still doesn't work and you have not already seen this link then there might be something that will work for you:

[http://askubuntu.com/questions/207131/screensaver-blanking-problem](http://askubuntu.com/questions/207131/screensaver-blanking-problem)


Good luck.

---

### Post by Hewjr100 on 2013-01-15
Ok got it working, moved it to the top like you said.  Thanks for your help.

Henry

---

