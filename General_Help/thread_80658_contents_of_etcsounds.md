---
title: "contents of /etc/sounds"
date: 2005-10-22
forum: General Help
---

### Post by DoeRayMe on 2005-10-22
Could someone please put the contents of /etc/sounds into a zip and either attach or email to [email]williamshand14@msn.com[/email]

thanks in advance

---

### Post by tomchuk on 2005-10-22
Here's a little script that will list then reinstall all packages with files in any directory you specify as a command line argument.

```

#!/bin/sh

if [ "$#" -ne "1" ]
then
    echo "Useage: $0 FILE|DIRECTORY"
    exit 1
fi

PKGS=""

for pkg in `dpkg --get-selections | grep install | awk '{print $1}'`
do
    dpkg -L $pkg | grep $1 > /dev/null 2>&1
    if [ "$?" -eq "0" ]
    then
        echo -ne " $pkg"
        PKGS="$PKGS $pkg"
    fi
done
echo -ne "\n\nReinstalling the above packages, hit any key to continue or Ctrl-C to quit... "
read

sudo apt-get --reinstall install $PKGS

```

put that in a file and run it with the argument of /etc/sounds to reinstall all packages that had installed files in /etc/sounds.

---

