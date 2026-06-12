---
title: "[Xubuntu] keyboard shortcuts aware of bash env variables"
date: 2017-12-30
forum: General Help
---

### Post by porparek on 2017-12-30
Hi,

I have the following variable set in .bashrc:
export IBROWSER_PRIV="firefox -private-window"

I have the following script in ~/bin/google subdirectory:
$IBROWSER_PRIV [www.google.com](www.google.com)

The ~/bin/ is included in $PATH and running google script works in bash.
Unfortunately it doesn't work when I set a keyboard shortcut in Keyboard -> Application Shortcuts. I use the full path for application to be launched: /home/porparek/bin/google

The idea behind the $IBROWSER_PRIV variable is that when I want to use e.g. chromium browser I just set it as follows:
export IBROWSER_PRIV="chromium --incognito"

Note that I set a browser name along with parameters.

How can I force the ~/bin/google script to work under a specific key combination.

thanks for help

---

### Post by Holger_Gehrke on 2017-12-30
Set your shortcut to execute ```

bash -l -c ~/bin/google
```
A shell executing a script is non-interactive. Non-interactive shells don't read ~/.bashrc. By calling the shell explicitly and telling it to act as if it was a login shell (option -l), you force it to read /etc/profile and ~/.profile (which sources ~/.bashrc on a normal Ubuntu system).

Holger

---

### Post by porparek on 2017-12-31
Great thanks for an answer. Unfortunately it doesn't work. After pressing the key combination nothing happens. I also tried the absolute paths but still with no luck.

---

### Post by Holger_Gehrke on 2018-01-01
Close to the beginning of the .bashrc there's a check whether it's an interactive shell or not, which exits if it isn't. You've got to put your variable definition before that.

Holger

---

### Post by porparek on 2018-01-01
Now it works as you wrote. I only put it directly to ~/.profile. Great thanks for help.

---

### Post by porparek on 2018-01-01
When added the 
export IBROWSER_PRIV="chromium --incognito"
into ~/.profile
the shortcut's "command" may look as simple as:
/home/porparek/bin/google

---

