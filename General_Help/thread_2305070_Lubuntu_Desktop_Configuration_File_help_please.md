---
title: "Lubuntu Desktop Configuration File help please"
date: 2015-12-02
forum: General Help
---

### Post by steve238 on 2015-12-02
Hi, I resurrected an old Dell D630 by upping the memory to 4Gb & loading Lubuntu  (Ubuntu 15.10) today & started playing with it, as a newbie to Linux.

I downloaded Minecraft.jar into new folder /home/dad/minecraft/ & created the following script as /home/dad/minecraft/minecraft.sh

#!/bin/bash
{
java -jar Minecraft.jar
} > log1 2>errfile 
exit

I allowed execution of this script, added /home/dad/minecraft to the PATH statement in /etc/environment & reloaded the system.

If you double click on this script it runs Minecraft Launcher with no errors.

I then created a desktop config file as follows:

[Desktop Entry]
Encoding=UTF-8
Name=Minecraft
Comment=Minecraft
Icon=/home/dad/icons/minecraft.jpeg
Exec=sh minecraft.sh
Terminal=false
Type=Application

When you double click this, nothing happens. I know it's at least a partially valid Desktop Entry, because it picks up Icon & Comment changes & reflects them on the desktop.

I've tried setting it to use a terminal & altering the script to set -x & -v in an attempt to debug it, but I get no output anywhere to indicate what the issue is.

It looks to me like the script is not being executed at all as it does not create the log1 & errfile files. I tried specifying the full path to the script just in case, but this made no difference.

Any help welcome,

Thanks,
Steve

---

### Post by furtom on 2015-12-02
> **steve238 said:**
> 
I then created a desktop config file as follows:

[Desktop Entry]
Encoding=UTF-8
Name=Minecraft
Comment=Minecraft
Icon=/home/dad/icons/minecraft.jpeg
Exec=sh minecraft.sh
Terminal=false
Type=Application




I think if you replace

```
Exec=sh minecraft.shwith
```
with
```
Exec=/home/dad/minecraft/minecraft.sh
```
it should work.

---

### Post by steve238 on 2015-12-02
Thanks for the suggestion... I tried & get an "Invalid desktop entry file" pop up when I double click it. 
I seem to get that whenever I use the "Exec=name" format pointing to a ".sh" script. 
If I change it back to "Exec=sh name" it doesn't error but doesn't work.

Cheers,
Steve

---

### Post by steve238 on 2015-12-02
Hmmm... some progress made by executing the "sh" command in a terminal rather than within Desktop Config..... The script file name was "minecraft.sh" in PCmanFM but for some reason in a "dir" command it showed as "/ minecraft.sh" ... I removed the "/ " from the name which improved things slightly.

If you start LXTerminal, navigate to /home/dad/minecraft/ then execute the script, it works, but if you execute it from anywhere else, using absolute or relative paths, it fails to run the script, giving no errors, but it appears to actually find the script.

---

### Post by furtom on 2015-12-03
if you run:

```
sh /home/dad/minecraft/minecraft.sh
```
it does not work? but if you

```
cd /home/dad/minecraft
./minecraft.sh
```

it does?

I'm just guessing now, but check the ownership and permissions of /hom/dad and also /home/dad/minecraft

EDIT: I should say especially /home/dad/minecraft :)

---

