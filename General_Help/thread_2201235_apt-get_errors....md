---
title: "apt-get errors..."
date: 2014-01-23
forum: General Help
---

### Post by murgero on 2014-01-23
Hello fellow ubuntu users, 

So I am very new to using linux and I was installing an application using make install. I have recieved errors during install and I went to delete the files made by make install.

The following errors happen when I use apt-get install <package name>

```
dpkg: warning: 'ldconfig' not found in PATH or not executable.
dpkg: warning: 'start-stop-daemon' not found in PATH or not executable.
dpkg: error: 2 expected programs not found in PATH or not executable.
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

Here is how I ended up doing this:

I had wanted to uninstall aircrack-ng from my system after realizing I couldn't use it with my Wireless card, so I deleted the "sbin" folder under /usr/local/sbin.
After I recreated the folder is where the error comes in when using apt-get.

I have checked my sudoers file as well as "echo PATH=<long string for sbin folder>" 

Is there any other solution other than reinstalling ubuntu?


Many thanks!

---

### Post by steeldriver on 2014-01-23
You need to find / fix root's PATH variable (not your own) - try

```
$ sudo sh -c 'echo $PATH'
```

and paste the output back here

---

### Post by murgero on 2014-01-23
> **steeldriver said:**
> You need to find / fix root's PATH variable (not your own) - try

```
$ sudo sh -c 'echo $PATH'
```

and paste the output back here

```
mitchell@UR-LINUX1:~$ sudo sh -c 'echo $PATH'
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
mitchell@UR-LINUX1:~$ 


```

It seems to be in there.


But has my deleting of the sbin folder and recreating it caused an issue (Either the folder itself or a symlink I am unaware of?)

---

### Post by murgero on 2014-01-23
The problem is I also have the old fix from the Debian 7 probelm too like my sudoers file already has > #
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults        env_reset
Defaults secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/$sbin:/bin"
# Host alias specification



I just do not want to have to reinstall ubuntu because it took me forever to figure wireless drivers.

---

### Post by philinux on 2014-01-23
Folder /usr/local/sbin should be:-

```
Group Owner Permissions
root  root  drwxr-xr-x
```

---

### Post by murgero on 2014-01-23
I have those set, but still no luck :/

---

### Post by philinux on 2014-01-23
Here's what my sudoers file contains. Never been messed about with.
```

#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults	env_reset
Defaults	mail_badpass
Defaults	secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo	ALL=(ALL:ALL) ALL

# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d
```

---

### Post by murgero on 2014-01-23
> **philinux said:**
> Here's what my sudoers file contains. Never been messed about with.
```

#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults    env_reset
Defaults    mail_badpass
Defaults    secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo    ALL=(ALL:ALL) ALL

# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d
```

Mine has all of thios except the Defaults mail_badpass.

---

### Post by philinux on 2014-01-23
Just spotted this in yours.

```
 Defaults secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/**[COLOR="#FF0000"]$[/COLOR]**sbin:/bin"
```

Not an expert on this so no idea of significance of $ sign.

---

### Post by murgero on 2014-01-23
This is my exact sudoers file, reads like this in gedit AND visudo as well.

> #
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults    env_reset
Defaults    mail_badpass
Defaults    secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo    ALL=(ALL:ALL) ALL

# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d

---

### Post by jeanjd63 on 2014-01-23
Hello 
I think you need two programs :
/sbin/ldconfig
/sbin/start-stop-daemon

For the first 
you can copy this in the file /sbin/ldconfig :

**sudo  gedit  /sbin/ldconfig**

> #!/bin/sh

if  test $# = 0                            \
    && test x"$LDCONFIG_NOTRIGGER" = x                \
 && test x"$DPKG_MAINTSCRIPT_PACKAGE" != x            \
 && dpkg-trigger --check-supported 2>/dev/null
then
    if dpkg-trigger --no-await ldconfig; then
        if test x"$LDCONFIG_TRIGGER_DEBUG" != x; then
            echo "ldconfig: wrapper deferring update (trigger activated)"
        fi
        exit 0
    fi    
fi


exec /sbin/ldconfig.real "$@"



and make it eXec 
[B]sudo  chmod a+x  /sbin/ldconfig
[/B]The second is binary but you can try this :
[SIZE=3][B][SIZE=2]sudo  -i[/SIZE]
[COLOR=#000000]touch  [/COLOR][/B][/SIZE]**/sbin/start-stop-daemon**[SIZE=3][B][COLOR=#000000]
echo exit 0 > [/COLOR][/B][/SIZE]**/sbin/start-stop-daemon**[SIZE=3][B][COLOR=#000000]
chmod +x  [/COLOR][/B][/SIZE]/**sbin/start-stop-daemon**
Good luck

---

