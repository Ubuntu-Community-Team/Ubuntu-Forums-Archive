---
title: "Shutdown -r not working in bash script run as cron job"
date: 2019-08-29
forum: General Help
---

### Post by userdenied2 on 2019-08-29
Hello,

I'm trying to write a script that will gracefully stop the Minecraft servers I am running, and then reboot the host. I've got a script that works if I run it manually from a terminal window, but when trying to run the script as a cron job it fails at the line that should reboot the host. 

This is my script called host_restart.sh
```

#!/bin/bash
exec 1> >(logger -s -t $(basename $0)) 2>&1
echo Starting host restart script...

#Announce Server reboots
echo Announcing restart to prod server...
screen -S minecraft -X stuff "say Server is restarting in 60 seconds\\r"
screen -S minecraftdev -X stuff "say Server is restarting in 60 seconds\\r"
sleep 60
echo Kicking players from  prod server...
screen -S minecraft -X stuff "kick @a Server is restarting. Downtime less than 5min\\r"
sleep 1
echo Stopping prod server...
screen -S minecraft -X stuff "stop\\r"

#Stop Minecraft Dev Server:
echo Kicking players from dev server...
screen -S minecraftdev -X stuff "kick @a Server is restarting. Downtime less than 5min\\r"
sleep 1
echo Stopping prod server...
screen -S minecraftdev -X stuff "stop\\r"

#Announce Servers are stopped
echo Prod and Dev Minecraft server stopped...

#Restart host
echo restarting host...
sudo shutdown  -r now

```

When looking at the syslog I found that the restart was failing due to the prompt for the sudo password as shown by "no tty present and no askpass program specified".
```
Aug 29 12:04:01 astora CRON[4696]: (solaire) CMD (/usr/bin/host_restart.sh)
Aug 29 12:04:01 astora host_restart.sh: Starting host restart script...
Aug 29 12:04:01 astora host_restart.sh: Announcing restart to prod server...
Aug 29 12:04:02 astora host_restart.sh: Kicking players from prod server...
Aug 29 12:04:03 astora host_restart.sh: Stopping prod server...
Aug 29 12:04:03 astora host_restart.sh: Kicking players from dev server...
Aug 29 12:04:04 astora host_restart.sh: Stopping prod server...
Aug 29 12:04:04 astora host_restart.sh: Prod and Dev Minecraft server stopped...
Aug 29 12:04:04 astora host_restart.sh: restarting host...
Aug 29 12:04:04 astora host_restart.sh: sudo: no tty present and no askpass program specified
Aug 29 12:04:04 astora CRON[4695]: (CRON) info (No MTA installed, discarding output)

```

After doing some research on this I found that this should be correctable by editing the sudoers file to bypass the requirement for a password for a given user and a given script. I've added this entry for both my user and root, but am still getting the same error. 

Here is a copy of my sudoers file
```
  GNU nano 2.9.3                                           /etc/sudoers.tmp

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
root  ALL=(ALL) NOPASSWD: /usr/bin/host_restart.sh
solaire ALL=(ALL) NOPASSWD: /usr/bin/host_restart.sh

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL

# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d

```

Is there something I've done wrong in the sudoers file, or is there another nuance that I am missing? Any help is greatly appreciated. If more information is needed please let me know. :)

---

### Post by Holger_Gehrke on 2019-08-29
Wouldn't it be cleaner and simpler to run the script from root's crontab ? No need for 'sudo' then.

Holger

---

### Post by userdenied2 on 2019-08-29
> **Holger_Gehrke said:**
> Wouldn't it be cleaner and simpler to run the script from root's crontab ? No need for 'sudo' then.

I forgot to add that I had tried this, but it causes two other issues that seemed harder to get around.


[LIST=1]
[*]The screen commands fail because the screen sessions are not found, even though they exist. 
[*]The shutdown command fails as 'shutdown: command not found' 
[/LIST]

 I also assumed it wasn't ideal to run an entire script with elevated privileges when I really just need one small portion run as sudo. I know for this small use case it won't matter so much, but I'm trying to build good habits now so I don't expose myself to issues later.

---

### Post by TheFu on 2019-08-29
Don't put the script in the sudoers. Put just the /sbin/shutdown command in there and only for your userid.
root doesn't need sudo.

---

### Post by userdenied2 on 2019-08-29
> **TheFu said:**
> Don't put the script in the sudoers. Put just the /sbin/shutdown command in there and only for your userid.
root doesn't need sudo.


Interesting, I hadn't thought about the fact that shutdown is just another script that I'm calling and THAT is what needs the exception. 

I've modified my sudoers file trying both my username and userid as below but still get the same error. Have I still misunderstood something?

Here with username
```
  GNU nano 2.9.3                               /etc/sudoers.tmp

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
solaire ALL=(ALL) NOPASSWD: /sbin/shutdown

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL

# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d
``` 

Here with userid as given by echo $UID
```
  GNU nano 2.9.3                                           /etc/sudoers.tmp

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
1000 ALL=(ALL) NOPASSWD: /sbin/shutdown

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL

# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d
```

---

### Post by TheFu on 2019-08-29
Did you use **visudo** to edit the file?
```

     When multiple entries match for a user, they are applied in order.  Where
     there are multiple matches, the last match is used (which is not necesâ
     sarily the most specific match).
```

So move the line you added with the userid to the bottom of the file. Bet it makes all the difference. ;)

thefu ALL=(ALL) NOPASSWD: /sbin/poweroff, /sbin/reboot, /sbin/shutdown
Don't touch the other %sudo line.

---

### Post by userdenied2 on 2019-08-30
@TheFu,

Using visudo yep, saw the cautions about editing directly. 

And moving that entry to the end of the file worked! Though I had to use my username and not my userid, but I'll take it!

Thanks  a ton for the help, really appreciate it. I'm pretty new to Linux, but  I'm really enjoying the process of learning how to do everything and  communities like this are a big part of that. :)

---

### Post by TheFu on 2019-08-30
username is clear. It is the name/letters.
uid is clear. It is the number.
userid can mean either 'thefu' or 1010.

Always check the program manpage for how any specific config or command uses each.  It has been fuzzier since a few Windows-centric tools allow mixing and matching of either the name or the numbers.

sudo has many, many, many, more uses than just allowing a user/group to run programs as root.  So many more.  

Also, if we put that line into a file inside the /etc/sudoers.d/ directory, it would have worked too. Why? Because the include for that directory is at the bottom of the sudoers file. There are rules about the filename patterns allowed and the required permissions and owner/group. The patterns are different from many other config file required patterns - like for apache.

---

