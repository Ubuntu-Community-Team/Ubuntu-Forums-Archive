---
title: "Give a script root access when without sudo"
date: 2018-04-30
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2018-04-30
So lets say i have this script
```

!/bin/sh
smart="$(nvme smart-log /dev/nvme0)"
echo "$smart" | grep temperature

```
[FONT=courier new]nvme smart-log /dev/nvme0[/FONT] requires sudo
I would like to allow this script/command to run as root
without giving unrestricted access to the nvme command to the user
[FONT=courier new]smartctl -A /dev/nvme0[/FONT]  would also work

I know there is a way to do this with hddtemp:
[FONT=courier new]sudo chmod u+s /usr/sbin/hddtemp[/FONT]

---

### Post by HermanAB on 2018-04-30
Yes, you can set *nvme* to SUID root with *chmod*.

It is best to limit the number of utilities that are SUID root, since it is sometimes possible to abuse them, but if it is your own machine and you are the only user, then the risk is minimal.

In general, a utility that is able to launch another command, such as *find* with the *exec* option, should never be set to SUID root, since that will allow anyone to run any program as root.

---

### Post by erind on 2018-04-30
One way is to give elevated privileges to the whole script by adding its full path into the sudoers file:** /etc/sudoers **
This way only the script can be run as root, but not the individual command, **nvme** in this case. Say the script is **/home/user_name/bin/nvme_script.sh**:
```
#!/bin/bash
smart="$(nvme smart-log /dev/nvme0)"
echo "$smart" | grep temperature
```
 
Then it'd be added somewhere to the end of the **/etc/sudoers** file, like so:

```
[...]

# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d
...
user_name ALL=NOPASSWD: /home/user_name/bin/script_1.sh
user_name ALL=NOPASSWD: /home/user_name/bin/script_2.sh
...
[B]user_name ALL=NOPASSWD: /home/user_name/bin/nvme_script.sh
[/B]
[...]

```
Then the script can be run as root, but without being prompted for a password:

```
sudo nvme_script.sh
```

If you want to omit the **sudo** in front of the script, then you can run it as root in a slightly different way. Again add the script first in the **sudoers** file, then add 
**[ $(whoami) = root ] || exec sudo $0** at the top of the script, like so:
```
#!/bin/bash

**[ $(whoami) = root ] || exec sudo $0** 

smart="$(nvme smart-log /dev/nvme0)"
echo "$smart" | grep temperature
```
Then run it simply as:

```
**$ nvme_script.sh**
```

---

### Post by pqwoerituytrueiwoq on 2018-04-30
```
root@Z97Killer:~# ls /etc/sudoers.d -l
total 8
-r--r----- 1 root root  49 Apr 30 13:52 nvme_temp
-r--r----- 1 root root 958 Jan 17 19:08 README
root@Z97Killer:~# cat /etc/sudoers.d/nvme_temp 
user_name ALL=NOPASSWD: /usr/local/bin/nvme_temp
root@Z97Killer:~# 
```
EDIT:
how do i apply the change to have it take effect
I see how i need to do it now, the file should contain
[FONT=courier new]%sudo ALL=NOPASSWD: /usr/local/bin/nvme_temp[/FONT]

---

### Post by erind on 2018-04-30
> **pqwoerituytrueiwoq said:**
> [...]

EDIT:
how do i apply the change to have it take effect
I see how i need to do it now, the file should contain
[FONT=courier new]%sudo ALL=NOPASSWD: /usr/local/bin/nvme_temp[/FONT]

The right way to do it is running visudo command, type:

```
$ sudo visudo
```

Then:

> Got to the last line of the file.
Type "o" to insert a new line below it.
Now type what you want to insert, eg "your_actual_user_name ALL=NOPASSWD: /usr/local/bin/nvme_temp.sh".
Hit esc to exit insert-mode.
Type ":x" to save and exit.

See more here:

[https://www.garron.me/en/linux/visudo-command-sudoers-file-sudo-default-editor.html](https://www.garron.me/en/linux/visudo-command-sudoers-file-sudo-default-editor.html)

Nothing goes to **/etc/sudoers.d** directory, better stay away from it.

---

### Post by erind on 2018-04-30
For example **/etc/sudoers** file with your script added to the end, will look something like this:

```
#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults        env_reset
Defaults        mail_badpass
Defaults        secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin"

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL

# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d
your_actual_user_name ALL=NOPASSWD: /full/path/to/script_1.sh
your_actual_user_name ALL=NOPASSWD: /full/path/to/script_2.sh
...
[COLOR=#ff0000]your_actual_user_name ALL=NOPASSWD: /usr/local/bin/nvme_temp.sh 
[/COLOR]
```[COLOR=#ff0000]
[/COLOR]
Obviously replace your_actual_user_name with your account name, say if it's          **pqwoerituytrueiwoq**, then that line will look like:
         ```
...

pqwoerituytrueiwoq  ALL=NOPASSWD: /usr/local/bin/nvme_temp.sh
```

---

