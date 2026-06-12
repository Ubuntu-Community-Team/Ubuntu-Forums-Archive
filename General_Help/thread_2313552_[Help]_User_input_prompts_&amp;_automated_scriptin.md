---
title: "[Help] User input prompts &amp; automated scripting"
date: 2016-02-13
forum: General Help
---

### Post by benbrockn on 2016-02-13
Hello,

I'm trying to write a simple bash script that can automate creating users and logging them in, or for any general purpose use where a command is run and a prompt shows up asking for user input (such as "username: ", "password: ", "continue? [y/n]", "press enter to continue", etc...)

Here's a few things:


[LIST=1]
[*]I already know that entering a password using a command in the terminal or by using a script is bad practice because you can use the ps command to see it. For my purposes, this won't matter.
. 
[*]I do not want to enable "autologon" to Ubuntu to automatically log me in when I start it up. This is not the solution I need.
. 
[*]I tried looking up the "expect" command and creating an expect script, but was confused by it, and if possible, I'd like to only have one script that contians all of the information I need (the commands, the username, the password, etc..). I know that it is bad practice to do this. 
[/LIST]

Here are some things I Google'd but they failed:

```
[COLOR=#0000ff](in terminal window or script)[/COLOR]

echo "password" | login username

[COLOR=#0000ff](acts if nothing happened)[/COLOR]
```

```
[COLOR=#0000ff](in terminal window or script)[/COLOR]

login username && echo "password"

[COLOR=#0000ff](runs first command, waits until first command is finished, then runs second command)[/COLOR]
```

```
[COLOR=#0000ff](in terminal window or script)[/COLOR]

login username & echo "password"

[COLOR=#0000ff](runs both at same time, usually "echo" first, but does not enter "password" into the first command)[/COLOR]
```

```
[COLOR=#0000ff](in .sh file)[/COLOR]

#!/bin/bash

login username
expect "*?assword:*"
send -- "$password\r"

[COLOR=#0000ff](errored with: send: command not found)[/COLOR]

```

and different variations of these.

This is what I want to happen **(doesn't have to be used with root account)**:

```
root@ubuntu:~# **[COLOR=#ff0000]adduser USER[/COLOR]**
Adding user `USER' ...
Adding new group `USER' (1006) ...
Adding new user `USER' (1004) with group `USER' ...
Creating home directory `/home/USER' ...
Copying files from `/etc/skel' ...
Enter new UNIX password:  **[COLOR=#ff0000][autofill][/COLOR]**
Retype new UNIX password:  **[COLOR=#ff0000][autofill][/COLOR]**
passwd: password updated successfully
Changing the user information for to
Enter the new value, or press ENTER for the default
    Full Name []:  **[COLOR=#ff0000][Enter key pressed or autofill][/COLOR]**
    Room Number []: **[COLOR=#ff0000][Enter key pressed or autofill][/COLOR]**
    Work Phone []: **[COLOR=#ff0000][Enter key pressed or autofill][/COLOR]**
    Home Phone []: **[COLOR=#ff0000][Enter key pressed or autofill][/COLOR]**
    Other []: **[COLOR=#ff0000][Enter key pressed or autofill][/COLOR]**
Is the information correct? [Y/n] **[COLOR=#ff0000][Y or n pressed or Enter key pressed][/COLOR]**
```

If possible, I'd like it to be verbose like the code above. If that can't happen, it's not a big deal.

Thanks,

-- Ben

---

### Post by dragonfly41 on 2016-02-13
I would try using an automation script created in Actionaz GUI.   Actionaz package is in repo.

---

