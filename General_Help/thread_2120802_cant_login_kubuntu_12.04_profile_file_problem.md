---
title: "cant login kubuntu 12.04 profile file problem"
date: 2013-02-27
forum: General Help
---

### Post by imight on 2013-02-27
hi
i am having a problem with loggin in.
its in a cycle login with password correct - > login -> login with password correct -> login.

i ve seen a few threads about this matter but none helped.

i do ctrl+atl+f2, when i log in it shows me two erros

```
-bash: /home/imight/.profile: line 19 unexpected EOF while looking for matching `"
--bash: /home/imight/.profile: line 22: syxtax error: unexpected end of file
```

always learning, next time dont mess with files b4 you are sure what your are going to do :P

thank you

---

### Post by dabl on 2013-02-27
Here's the ~/.profile file from my fully-updated Kubuntu 12.10 system, for what it is worth:

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
```

Also, use "ls -la" and confirm that there are no files owned by root in your user's home folder.

---

