---
title: "Add NOPASSWD in /etc/sudoers to only some specific commands"
date: 2017-06-07
forum: General Help
---

### Post by Xpdin on 2017-06-07
Are there any risks for letting the beyond commands to be used with no password?


It is a home computer, with no other users using it, I only use the single default created user when Ubuntu was installed.


I would like to don't have to write at all the sudo password for these commands:


    ```
echo 100 > /sys/class/backlight/intel_backlight/brightness
    
    ethtool -s eth0 autoneg off speed 100 duplex full


    dhclient eth0


    apt-get update && upgrade && dist-upgrade -y


    apt-get autoremove && remove && clean && autoclean -y
```


Thank you.

---

### Post by Habitual on 2017-06-07
Sudo: you're doing it wrong - [PDF]("https://www.bsdcan.org/2014/schedule/attachments/283_2014-04-29%20sudo%20tutorial%20-%20bsdcan%202014.pdf") @ 171 pages.
Sudo: you're doing it wrong - [YouTubeVid]("https://www.youtube.com/watch?v=o0purspHg-o") @ 1h:11m

Get some!

---

### Post by Xpdin on 2017-06-08
I appreciate Habitual,

Can you also help me with the questions please?

Thank you.

---

### Post by Habitual on 2017-06-08
You're welcome.

---

### Post by cariboo on 2017-06-08
My Raspberry Pi running Hassbian (Debian based) is set up to use sudo without a password, but it is all or nothing.

---

### Post by Xpdin on 2017-06-08
Can you say please how did you do it cariboo ? Thank you.

---

### Post by cariboo on 2017-06-09
That's the way it installed by default but here is the contents of the sudoers file:

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

# Allow members of group sudo to execute any command
%sudo	ALL=(ALL:ALL) ALL

# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d[/code'

it also checks the contents of /etc/sudoers.d the contents of that dir are:

[code]ls -l
total 12
-r--r----- 1 root root  27 Oct 18  2016 010_pi-nopasswd
-rw-rw-r-- 1 root root 139 May  1 04:48 020_homeassistant_hassbian-scripts
-r--r----- 1 root root 958 Jan 11  2016 README
```

the important file in this case is 010_pi-nopasswd the contents are:

```
pi ALL=(ALL) NOPASSWD: ALL
```

in this case the user's name is pi.

---

### Post by Xpdin on 2017-06-10
Thank you very much for your kindness cariboo,

It seems that these steps resolved this case:


   ```
sudo su
```


Create ```
/usr/local/bin/scriptname
``` and write the beyond lines in it:
 


    ```

#!/bin/bash
    
command in here without sudo
    
# the end of the scriptname
```




    Create ```
/etc/sudoers.d/scriptname
```and write the following lines in it:
    
    ```

User_Alias scriptname=username
Cmnd_Alias scriptabreviaton=/home/globalisation/r
scriptname ALL=NOPASSWD: scriptabreviaton
```




Add at the end of ```
/etc/sudoers
``` the next two lines:


    
  ```
  
username ALL=(ALL:ALL) ALL
username ALL=(ALL:ALL) NOPASSWD: /usr/local/bin/scriptname
```


    
    ```

chown root:root /etc/sudoers.d/scriptname
chown root:root /usr/local/bin/scriptname
chmod 0700 /usr/local/bin/scriptname
chmod 0440 /etc/sudoers.d/scriptname
```
  
From the regular user name:


```
sudo /usr/local/bin/scriptname
```


It shouldn't ask for sudo password any more.


Everywhere when it is written "scriptname", "usernme", "scriptabreviaton" every each of them should be the same.

---

