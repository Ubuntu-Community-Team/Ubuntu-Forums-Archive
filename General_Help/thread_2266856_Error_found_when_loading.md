---
title: "Error found when loading"
date: 2015-02-25
forum: General Help
---

### Post by mickee384 on 2015-02-25
Hello! I have an error:

"Error Found when loading /home./mickee/.profile
As a result your session will not be configured correctly.
You should fix the problem as soon as feasible."

This is my .profile

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

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi

logitech=$(xinput --list --short | grep -m1 "Logitech USB Receiver" | cut -f2 | cut -d= -f2)

xinput --set-prop "$logitech" "Device Accel Constant Deceleration" 4
```

I tried to put a # in front of the logitech line as I don't have a logitech mouse, but the error persisted so i took that out.
The only thing that happened was a 'partial upgrade' I allowed the partial. It appeared after that. I believe that this is after grub, but not sure. Please let me know if you would like further information. I am happy to oblige.

---

### Post by oldos2er on 2015-02-25
Now you know--never allow partial upgrades.

Here's my default ~/.profile file. If you can boot from your installation medium you can copy it to your home folder: ```
        [FONT=monospace][COLOR=#000000]# ~/.profile: executed by the command interpreter for login shells. [/COLOR]
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
fi
```
[/FONT]

---

### Post by mickee384 on 2015-02-25
Thanks for that Ann. It works great now. I have a question, (as far as partial upgrade, There were 2 choices, upgrade and continue, should I just have clicked continue? )I will look thru the forums for info on partial upgrades. Once again thanks for your help!:p

---

### Post by oldos2er on 2015-02-26
If you're using the GUI Update Manager, I think you can just close its window (or is "cancel" an option?), and ignore it. Try updating again in a day or two. I use "apt-get update && apt-get upgrade" in terminal, so I've kind of forgotten how Update Manager works.

---

