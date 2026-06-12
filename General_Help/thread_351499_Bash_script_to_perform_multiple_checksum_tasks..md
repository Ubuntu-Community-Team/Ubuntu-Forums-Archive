---
title: "Bash script to perform multiple checksum tasks."
date: 2007-02-02
forum: General Help
---

### Post by ardchoille42 on 2007-02-02
I have created a bash script to automate multiple checksum tasks and thought I would share it with the community. The bash script itself is attached to this post and the code is below:

```

#!/bin/bash
# Filename: csum.sh
# Version: 1.0
# Requires: md5sum, sha1sum, sed, bash
# Date: Thu Feb  1 21:21:28 PST 2007
# Author: Ian MacGregor (aka ardchoille42)
# License: GPL
#
# This script creates and verifies checksums
# with the option to save created checksum to file

mypath="/home/$USER"
redtext="\033[31m"
greentext="\033[32m"
boldtext="\033[1m"
normaltext="\033[0m"

getfilepath()
{
    myfile="/path/file"
    while [ ! -f $myfile ]
    do
        echo "Please enter the path and filename:"
        read myfile
        if [ ! -f $myfile ]
        then
            echo -e $boldtext$redtext"The path you entered does not exist." $normaltext
            echo
        else
            return
        fi
    done
}

getsum()
{
    mysum=""
    while [ ! $mysum ]
    do
        echo "Please enter the expected checksum:"
        read mysum
        if [ ! $mysum ]
        then
            echo -e $boldtext$redtext"You must provide a checksum to verify." $normaltext
            echo
        else
            return
        fi
    done
}

createmd5sum()
{
    getfilepath
    cmd5sum=`md5sum "$myfile"`
    echo
    echo "MD5SUM report:"
    echo $cmd5sum
    echo
    echo "Save this MD5SUM report to $mypath/mymd5report?"
    echo -e $boldtext"1"$normaltext "Yes"
    echo -e $boldtext"2"$normaltext "No"
    echo "====================="
    echo "Please select 1 or 2"
    read mysavereport
    case $mysavereport in
    "1") echo $cmd5sum >> $mypath/mymd5report ; cmd5sum="" ; myfile="" ; mysavereport="" ; return ;;
    "2") cmd5sum="" ; myfile="" ; mysavereport="" ; return ;;
    *) echo "Please select 1 or 2" ;;
    esac
}

createsha1sum()
{
    getfilepath
    csha1sum=`sha1sum "$myfile"`
    echo
    echo "SHA1SUM report:"
    echo $csha1sum
    echo
    echo "Save this SHA1SUM report to $mypath/mysha1report?"
    echo -e $boldtext"1"$normaltext "Yes"
    echo -e $boldtext"2"$normaltext "No"
    echo "====================="
    echo "Please select 1 or 2"
    read mysavereport
    case $mysavereport in
    "1") echo $csha1sum >> $mypath/mysha1report ; csha1sum="" ; myfile="" ; mysavereport="" ; return ;;
    "2") csha1sum="" ; myfile="" ; mysavereport="" ; return ;;
    *) echo "Please select 1 or 2" ;;
    esac
}

verifymd5sum()
{
    getfilepath
    echo
    getsum
    checkfile=`md5sum "$myfile" | sed 's/ .*//'`
    echo
    if [ "$checkfile" = "$mysum" ]
    then
        echo -e $boldtext$greentext"The expected md5sum matches the file's md5sum." $normaltext
    else
        echo -e $boldtext$redtext"The checksums do not match." $normaltext
    fi
    echo
    echo "Press the Enter key for Main Menu..."
    read
    checkfile=""
    myfile=""
    mysum=""
    return
}

verifysha1sum()
{
    getfilepath
    echo
    getsum
    checkfile=`sha1sum "$myfile" | sed 's/ .*//'`
    echo
    if [ "$checkfile" = "$mysum" ]
    then
        echo -e $boldtext$greentext"The expected sha1sum matches the file's sha1sum." $normaltext
    else
        echo -e $boldtext$redtext"The checksums do not match." $normaltext
    fi
    echo
    echo "Press the Enter key for Main Menu..."
    read
    checkfile=""
    myfile=""
    mysum=""
    return
}

while :
do
    clear
    echo "===================================="
    echo -e  $boldtext"Main Menu" $normaltext
    echo "===================================="
    echo -e $boldtext"1"$normaltext "Create an MD5 checksum for a file"
    echo -e $boldtext"2"$normaltext "Create an SHA1 checksum for a file"
    echo -e $boldtext"3"$normaltext "Verify a file by its MD5 checksum"
    echo -e $boldtext"4"$normaltext "Verify a file by its SHA1 checksum"
    echo -e $boldtext"5"$normaltext "Quit"
    echo "===================================="
    echo "Please select 1,2,3,4, or 5"
    read mych
    case $mych in
    "1") clear ; createmd5sum ;;
    "2") clear ; createsha1sum ;;
    "3") clear ; verifymd5sum ;;
    "4") clear ; verifysha1sum ;;
    "5") clear ; exit 0 ;;
    *) echo "Please select 1,2,3,4, or 5" ;;
    esac
done


```

This bash script runs fine on Ubuntu 6.06.1 LTS (Dapper Drake) and should run on almost any Linux distro as the dependencies are pretty basic. Download the attached file and run in a terminal.

---

### Post by joeashcraft on 2007-04-04
Many thanks to you, kind sir.

---

