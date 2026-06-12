---
title: "SUDO &amp; SU command not working"
date: 2016-10-05
forum: General Help
---

### Post by prasancumar on 2016-10-05
When I give sudo command in terminal sudo apt-get update i get the below message 

"**sudo: /usr/bin/sudo must be owned by uid 0 and have the setuid bit set**"

When I try su command and give password it gives below error message

"**su authentication failure**"

Could you please help me with this.

Regards
prasan cumar

---

### Post by yetimon_64 on 2016-10-05
> **prasancumar said:**
> When I give sudo command in terminal sudo apt-get update i get the below message 

"**sudo: /usr/bin/sudo must be owned by uid 0 and have the setuid bit set**"

When I try su command and give password it gives below error message

"**su authentication failure**"

Could you please help me with this.

Regards
prasan cumar
I have seen that sudo error posted here before. Just to get a better idea of the possible cause can you tell us what you have done recently that may have caused the change? 

Specifically, have you been running any commands as root (using sudo before the command) that could have possibly altered system file ownerships or permissions ?

An example of one such command is in [[COLOR=#0000ff]--this thread--[/COLOR]]("https://ubuntuforums.org/showthread.php?t=2321693") (the OP there ended up reinstalling because of the command used), another command that can cause such problems is "sudo chmod 777" especially if run on the root filesystem or the section of the system filesystem that holds the sudo command or the "sudo chown" command done wrongly.

If only sudo is affected it can be repaired from a recovery boot option, however if the damage to the filesystem extends further than just the sudo command it would help us greatly to know how this could have come about.

---

### Post by prasancumar on 2016-10-05
Hi [COLOR=#000000][FONT=Ubuntubeta]**yetimon_64**[/FONT][/COLOR]

I had given "**sudo chown -r 777 /" **instead of "[B]sudo chown -r 777 /usr/local"

[/B]Regards
Prasan Cumar

---

### Post by yetimon_64 on 2016-10-05
Usually the octal permissions of "777" would be used with the chmod command. The chmod command changes permissions, whereas the chown command (what you say you have used here) actually changes ownership NOT permissions (777 is octal permissions for "read write and execute" for "owner group and others". Even doing that is not a good idea to do to any system files including /usr/local; that is giving global access to system files which is not a good idea to do ever in Linux). 

If you have used that with the chown command you have changed file system ownership to a user by the name of 777 and done so recursively from the root of the system through every system file. That is not very good and may possibly need a reinstall to fix. 

Most system files and folders have the ownership of root:root but there are some special system files that are owned by other special system based user names so it may not be so simple to accurately reverse that command with a simple "sudo chown -r root /" command. Doing so could still leave important system files with the wrong ownership.

I would like to see the output of the following command posted back here (in code tags please, use the "Go Advanced" reply button and put the output between [noparse]```

```[/noparse] tags using the "#" symbol on the toolbar there) ...
```
ls -la /
```This command will list your root filesystem, including hidden files and folders, showing ownership and permissions and we can tell from that exactly what sort of damage will have occured, knowing that you have done so recursively down throughout the whole filesystem.

---

### Post by prasancumar on 2016-10-06
Please find attached the terminal screenshot after the command "[COLOR=#000000][FONT=&amp]ls -la /"[/FONT][/COLOR]

---

### Post by yetimon_64 on 2016-10-06
> **prasancumar said:**
> Please find attached the terminal screenshot after the command "[COLOR=#000000][FONT=&amp]ls -la /"[/FONT][/COLOR]

I don't understand what is exactly going on here. Going by what you said in post #3, that you issued the command "sudo chown -r 777 /" and earlier that sudo no longer works, that last command should have showed different output to what it is doing so now.

That looks normal with respect to permissions and ownership. Which sort of confuses me a bit :confused:. But moving on, try posting back the output of the command ... ```
ls -la /usr/bin/sudo
```

---

