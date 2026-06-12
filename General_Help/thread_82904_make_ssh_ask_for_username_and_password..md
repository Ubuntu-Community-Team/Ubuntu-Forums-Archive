---
title: "make ssh ask for username and password."
date: 2005-10-27
forum: General Help
---

### Post by bb002 on 2005-10-27
On my mandriva box if i ssh into it i get a prompt for both username and password. However on Ubuntu i only get a password prompt. the username gets defaulted to the account i made during install. Sure I could do "ssh username@ip" to login as who i wanted but i want a username and pass prompt if i only do "ssh ip". SUSE 9.0 Enterprise Edition has this habit as well. I tried make my mandriva and ubuntu configs the same but that seems to have no effect. though I haven't tried copying the mandriva ssh config over top ubuntu's....but I rather do it right and not the noob way.

---

### Post by Alexander Kirillov on 2005-10-27
[QUOTE=bb002]On my mandriva box if i ssh into it i get a prompt for both username and password. However on Ubuntu i only get a password prompt. the username gets defaulted to the account i made during install. Sure I could do "ssh username@ip" to login as who i wanted but i want a username and pass prompt if i only do "ssh ip". SUSE 9.0 Enterprise Edition has this habit as well. I tried make my mandriva and ubuntu configs the same but that seems to have no effect. though I haven't tried copying the mandriva ssh config over top ubuntu's....but I rather do it right and not the noob way.[/QUOTE]
I do not know how to do this, but an alternative method is to specify username in ssh config file. See man:ssh_config (look for option User).

Even better is using public keys: then you do not need to enter neither username nor password.

---

### Post by Felipe_U on 2005-11-15
[QUOTE=bb002]On my mandriva box if i ssh into it i get a prompt for both username and password. However on Ubuntu i only get a password prompt. the username gets defaulted to the account i made during install. Sure I could do "ssh username@ip" to login as who i wanted but i want a username and pass prompt if i only do "ssh ip". SUSE 9.0 Enterprise Edition has this habit as well. I tried make my mandriva and ubuntu configs the same but that seems to have no effect. though I haven't tried copying the mandriva ssh config over top ubuntu's....but I rather do it right and not the noob way.[/QUOTE]
 I think you need to type this to log on with the user you want:
ssh -l <user> <www.your-host-or-ip-here.com>     without the<>

---

### Post by bb002 on 2005-11-26
I figured out what was going on. If you try to ssh to a remote machine without specifing a username ssh takes the name of the user it is running as and tries to login to the remote machine with that username. So using this method ssh appears to loginwith only a password. If your current username doesn't exist on the remote machine logging in fails.

---

### Post by HeWhoE on 2008-05-23
I'd like to know how to configure ssh for this too!  I'm trying to set up a launcher on a public machine that opens gnome-terminal and executes ssh to open a connection to a particular server.  I want the user to be prompted for their own username, not the username from the public guest account!

---

### Post by HeWhoE on 2008-07-19
I've written a bash script to take care of this problem.  Here are the steps to make it work.

Edit the .bashrc file with your choice of editor.  In the following examples, I use vi.
```
$ vi ~/.bashrc
```
Add the following line to the file.
```
export PATH=$HOME/bin:$PATH
```

Update your settings:
```
$ source ~/.bashrc
```

Create a bin directory in your home directory.
```
$ mkdir ~/bin
```

Create a file named ssh in your bin directory.
```
$ vi ~/bin/ssh
```

Put the following in the new file.
```

#!/bin/bash

if [ $# -lt 0 ]
then
  exec ssh --help
else
  echo -en "\nEnter your username: "
  read user
  exec /usr/bin/ssh $user@$1
fi

```

---

