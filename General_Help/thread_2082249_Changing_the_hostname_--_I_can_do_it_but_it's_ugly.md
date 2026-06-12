---
title: "Changing the hostname -- I can do it but it's ugly"
date: 2012-11-08
forum: General Help
---

### Post by pwabrahams on 2012-11-08
I want to change the hostname of my computer.  I can do it by editing (as root) the files **/etc/hostname** and **/etc/hosts** (unless I missed some other important place).  But that's ugly.  Is there a straightforward way to do it?  (The **hostname** command only modifies your home directory.)

This would be a useful addition to System Settings.

---

### Post by pqwoerituytrueiwoq on 2012-11-08
let me make you something for that
this script is called [FONT=Courier New]new-host-name[/FONT]
```
#!/bin/sh
if [ -z "$1" ];then
   echo"usage $(basename $0) newHostName"
   exit
fi
if [ ! "$(whoami)" = "root" ];then
   echo "$(whoami) is not root"
   exit
fi
old="$(cat /etc/hostname)"
new="$1"
sed -i "s/$old/$new/" /etc/hosts
echo "$new" > /etc/hostname
exit
```* this script is untested

---

