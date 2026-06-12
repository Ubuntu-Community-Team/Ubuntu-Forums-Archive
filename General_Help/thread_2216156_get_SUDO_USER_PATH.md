---
title: "get SUDO_USER PATH"
date: 2014-04-10
forum: General Help
---

### Post by Little_Nooby on 2014-04-10
Hi,

I'm currently making the installation script for a custom software and I've got a problem to check the right PATH environement variable. The user must launch the script with root privileges. The following line modify correctly the PATH (Ok, it doesn't really modify it but you got it, right?)

```
echo "export PATH=\$PATH:$folder #MIL:infapt" >> $HOME/.bashrc
```
If the user was using sudo, it will use the $HOME directory of $SUDO_USER.

My problem is that I can't get the access the $SUDO_USER PATH variable. I can only access the root PATH variable. It results in my script failing to see if the $SUDO_USER PATH variable is correctly set up. It really disturbs me as "echo $PATH" and "sudo echo $PATH" give the same output.



So, is there a way to access the SUDO_USER PATH variable (without modifying any other file other than this one)?

Thanks whoever will try to help me,

Little Nooby

EDIT:SOLUTION
I think it isn't possible to get the unflushed PATH variable without modifying other file than this one (and I didn't want to) and I didn't want to modify the PATH elsewhere. So I decided to check the .bashrc file.
Here is what I came to :
```
inpath=$(echo $PATH|grep $folder|wc -l) #0 means folder wasn't in path, 1 or more means it was in.
checkbashrc=$(cat $HOME/.bashrc|grep "$folder"|grep "export PATH="|wc -l) #0 means there is no corresponding export line .bashrc, 1 or more means there surely is one (Let's assume there is).
let 'inpath = inpath + checkbashrc'
```

Here is the full code if you need it :
```
#!/bin/bash
#HELP:START

# #######################
# ##### INFORMATION #####
# #######################

# FILE        : /usr/local/bin/infapt
# USAGE       : ./infapt install or infapt <option>
# DESCRIPTION : This script and its subscripts has as purpose to keep records of when you installed something, uninstalled something and updated your system. This script doesn't really do anything itself, it uses aga, agi, agr and agu. You can't use this script without option.
# ------------------------------
# OPTIONS     : ituch
# VERSION     : 1.00
# CREATED     : 10-04-2014 13:02
# SEE ALSO    : aga, agi, agr and agu.
# ------------------------------
# AUTHOR      : Adrien Horgnies
# EMAIL       : adrien.horgnies@gmail.com
# ------------------------------
# NOTE        : It will install itself in /usr/local/bin/ and keep the records in ~/.infapt.

# ###################
# ##### OPTIONS #####
# ###################

# i     Install this software.
# t     Specify installation folder rather than using default folder (/usr/local/bin).
# u     Uninstall this software.
# c     Use this to keep records when uninstalling (~/.infapt/ will remain).
# h     Display this help and exit.

#HELP:END

# ###########################
# ##### OPTIONS PARSING #####
# ###########################

decision=2 #0 means installation, 1 means uninstallation, 2 means no decision taken.
folder="/usr/local/bin" #default installation folder
removerecords=0 #0 means it will remove records with uninstallation. 1 means it won't remove them.
while getopts "it:uch" opt; do
  case $opt in
    i)
       if [ $decision -ne 2 ]; then
          echo "You can't use both installation and uninstallation options. Aborting script."
          exit 1
       else
          decision=0
       fi;;
    t)
       folder=$OPTARG
       ;;
    u)
       if [ $decision -ne 2 ]; then
          echo "You can't use simultaneously installation and uninstallation options. Aborting script."
          exit 1
       else
          decision=1
       fi;;
    c)
       removerecords=1
       ;;
    h)
       sed '1,/HELP\:START/d; /HELP\:END/Q' $0|cut -c 2-
       exit;;
  esac
done
shift $((OPTIND-1))

# ##########################
# ##### IMPLEMENTATION #####
# ##########################

# check root permissions
if [[ $UID != 0 ]]; then
    echo "Please start the script as root or sudo!"
    exit 1
fi

if [ $decision -eq 0 ]; then
   echo "Checking installation folder : "

   if [ ! -d $folder ]; then
       echo "$folder doesn't exist or is not a directory. No change made to system, Aborting script."
       exit 1
   else
       echo "Destination folder : $folder"
   fi

   inpath=$(echo $PATH|grep $folder|wc -l) #0 means folder wasn't in path, 1 means it was in.
   if [ $inpath -eq 0 ]; then
      addit=$($(dirname $0)/checkuser "$folder wasn't found in your PATH environement variable. Do you wish to add $folder to it? [Y/n]")
      echo #newline
      if [ $addit -eq 0 ]; then
         echo "export PATH=\$PATH:$folder #MIL:infapt" >> $HOME/.bashrc
         echo "$HOME/.bashrc correctly modified."
      else
         echo "You chose not to add this folder to PATH. Please, retry to install with another directory (which is in PATH) or accept to add $folder in PATH. PATH=$PATH. No change made to system, exiting script."
         exit 0
      fi
   fi
   echo "Destination folder : OK"

elif [ $decision -eq 1 ]; then
   echo "Uninstalling infapt and subscripts."
fi
```

---

### Post by steeldriver on 2014-04-10
I think what you're missing here is that unquoted variables get expanded immediately by the shell - for example

```

$ echo $PATH
/home/steeldriver/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
$
$ sudo echo $PATH                # $PATH gets expanded by current shell
[sudo] password for steeldriver:
/home/steeldriver/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
$
$ sudo sh -c 'echo $PATH'        # $PATH passed unexpanded to root shell
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

```

Similarly,
```

$ sudo echo $SUDO_USER

$
$ sudo sh -c 'echo $SUDO_USER'
steeldriver

```

---

### Post by Little_Nooby on 2014-04-10
Ok, I understand this event better now. It's not that I get the wrong PATH, it's that I only modified the PATH for the shell and the shell drops the modifications when running a script.
I saw I can modify this behaviour with the sudouser file. But I'd like my script to run without modifying this file (because it is a security behaviour and the script should run correctly on unmodified O.S.).

Knowing this I'll do more research, thank you steeldriver.

---

