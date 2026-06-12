---
title: "Install script error"
date: 2014-01-10
forum: General Help
---

### Post by Tristan_Williams on 2014-01-10
I have decided to make my own Ubuntu distro, which will be completely source based, like Gentoo. 
[http://ubuntuforums.org/showthread.php?t=2198648](http://ubuntuforums.org/showthread.php?t=2198648)

I have a script, which will install a package, all of its dependencies, and recommended packages.

However the script is not working as it should

Here is the script: (I turned on verbose output for troubleshooting purposes)
```

#!/bin/bash
set -v
clear

read -p "Package: " pkg
echo "Calculating extra packages... "
sudo apt-cache depends $pkg | awk '{if ($1 == "Depends:") print $2}'> /etc/apt/build-deps
sudo apt-cache depends $pkg | awk '{if ($1 == "Suggests:") print $2}'> /etc/apt/build-sug
sudo apt-cache depends $pkg | awk '{if ($1 == "Recommends:") print $2}'> /etc/apt/build-rec

echo "Building package lists... "
# cat /etc/apt/build-deps >> export builddeps
# cat /etc/apt/build-sug >> export buildsug
# cat /etc/apt/build-rec >> export buildrec
builddeps='cat /etc/apt/build-deps'
buildsug='cat /etc/apt/build-sug'
buildrec='cat /etc/apt/build-rec'

echo Packages to install: "
echo $builddeps $buildsug $buildrec
read -p "Confirm install? [y/n] " conf
        if [ "$conf" == "y" ]; then
                sudo apt-build install $builddeps $buildsug $buildrec
        elif [ "$conf" == "n" ]; then
                echo "Abort! "
        fi

echo "Removing temporary build files... "
rm -f /etc/apt/build-deps
rm -f /etc/apt/build-sug
rm -f /etc/apt/build-rec

echo "Removing unneeded variables... "
unset pkg
unset builddeps
unset buildsug
unset buildrec
unset conf

```

And here is the output:
```

read -p "Package: " pkg
Package: xfce4
echo "Calculating extra packages... "
Calculating extra packages... 
sudo apt-cache depends $pkg | awk '{if ($1 == "Depends:") print $2}'> /etc/apt/build-deps
sudo apt-cache depends $pkg | awk '{if ($1 == "Suggests:") print $2}'> /etc/apt/build-sug
sudo apt-cache depends $pkg | awk '{if ($1 == "Recommends:") print $2}'> /etc/apt/build-rec

echo "Building package lists... "
Building package lists... 
builddeps='cat /etc/apt/build-deps'
buildsug='cat /etc/apt/build-sug'
buildrec='cat /etc/apt/build-rec'

echo Packages to install: "
echo "$builddeps" "$buildsug" "$buildrec"
read -p "Confirm install? [y/n] " conf
    if [ "$conf" == "y" ]; then
        sudo apt-build install $builddeps $buildsug $buildrec
    elif [ "$conf" == "n" ]; then
        echo "Abort! "
    fi

echo "Removing temporary build files... "
rm -f /etc/apt/build-deps
rm -f /etc/apt/build-sug
rm -f /etc/apt/build-rec

echo "Removing unneeded variables... "
unset pkg
unset builddeps
unset buildsug
unset buildrec
unset conf
/etc/install.sh: line 30: unexpected EOF while looking for matching `"'
/etc/install.sh: line 36: syntax error: unexpected end of file

```

For some reason, it just runs all the way through, but doesn't actually execute the commands... It just prints the command to the screen and bypasses it

---

### Post by Tristan_Williams on 2014-01-10
Turns out I had a missing " 
...I am disappointed in myself :(

---

