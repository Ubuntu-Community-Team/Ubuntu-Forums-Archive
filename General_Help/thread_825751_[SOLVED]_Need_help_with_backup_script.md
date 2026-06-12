---
title: "[SOLVED] Need help with backup script"
date: 2008-06-11
forum: General Help
---

### Post by jeroensd on 2008-06-11
Hello everyone,

I'm making a backup script so I can make a backup of the home directory. Right now I have this so far:

```

#!/bin/bash

echo "This script creates a backup of the /etc directory."
echo "Are you sure you want to create a backup? (yes/no):"

read answer

if [$answer == "yes]
then
    echo "The directory will now be copied."
    cd /
    mkdir etc_backup
    cp -rf /etc/ etc_backup.
    echo "The directory has been copied. See the etc_backup directory"

else
    echo "No backup will be made. This prorgam will now be closed"

fi

```

I'm stuck with the if part. I can not compare a string with another string. I tried almost everything. What am I doing wrong? And will this code work so far or not? Do I miss something?

Greetings,
Jeroen :)

---

### Post by HermanAB on 2008-06-11
Hmm, search for a 'bash user guide' with Google.  

However, a better way to make backups is with rsync.  See this:
[http://ubuntuforums.org/showthread.php?t=825680](http://ubuntuforums.org/showthread.php?t=825680)

---

### Post by jeroensd on 2008-06-11
Well it's part of a schoolproject so I must program it in the Bash shell. I already red a bash guide for beginners But i coulnd't find anything in there...

---

### Post by forger on 2008-06-11
use [[ and ]]
```
if [[ "mom" == "dad" ]]; then echo "Your parents are the same text string."; else echo "Your parents are not the same text string."; fi
```

---

### Post by jeroensd on 2008-06-11
I tried this

```

if [[$answer == "yes"]]
then

```

but that doesn't work either. I get the message "Command not found"

---

### Post by victor.zamanian on 2008-06-11
> **jeroensd said:**
> I tried this

```

if [[$answer == "yes"]]
then

```

but that doesn't work either. I get the message "Command not found"

The problem is that you have to have spaces between [ and the next thing, as well as at the end, so:

```
if [ $answer == "yes" ]
then
```

This is because [ is actually a program. Hope this helps.

Edit: And you definitely don't necessarily need double brackets ([[, ]]). Singles are fine, I do singles all the time.

Also, since [ is a program, you can even do it without if and then and else and fi, using && (and) and || (else), as such:
```
[ $answer = "yes" ] && ( command; command; command; command; ) || ( commands; if; not; equal; to; "yes" )
```
or for example switch it around and go
```
[ $answer != "yes" ] && ( commands; if; not; equal; to; "yes" ) || ( command; command; command; ... )
```
or 
```
[ $answer = "yes" ] || ( commands if not equal to yes) && ( commands if equal to yes )
```
You can also spread it out on several rows using:
```
[ $answer = "yes" ] && (
    command1;
    command2;
    ...
) || (
    echo "You answered \"no.\""
)
```
Doing it in any of these ways, without if and else and all of that is of course a little bit more complicated, visually, but logically, they are equivalent. Just make sure, before you use any of these ways, if you do decide to, that you are absolutely certain that you know what's going to happen in each outcome. It is very easy to get confused in logical expressions if the syntax and/or language isn't very clear (compare if-else-then to && and || -- English vs kind-of-random characters).

Hope you learned something and that any of it helped. :-) Cheers.

---

### Post by jeroensd on 2008-06-11
Thanks! That helped!

How can I create a directory with a bash command? I know I can use mkdir but It complains that I don't have the rights to create a directory. 
I have this script so far:

```

#!/bin/bash

echo "This script creates a backup of the /etc directory."
echo "Are you sure you want to create a backup? (yes/no):"

read answer

if [[ $answer == "yes" ]]
then
    echo "The directory will now be copied."
    mkdir etc$20BACKUP
    cp -rf /etc/ etc$20BACKUP/
    echo "The directory has been copied. See the etc_backup directory"

else
    echo "No backup will be made. This prorgam will now be closed"

fi

```

But that doesn't work. How else can i write a script that copies the /etc directory in another directory name ect%20BACKUP?

---

### Post by victor.zamanian on 2008-06-11
Oh, well, you could run the script as super user with the sudo command, perhaps, like:
```
$ sudo ./script.sh (or whatever it's called)
```
and then enter the administrator password; or add "sudo mkdir" inside of the script for example. Note that you'll have to enter the password either way.

The reason why you can't create a folder in /etc is because /etc has restricted access rules, so that only root can access it.

Edit: Also need to have root access to copy the etc folder, which means you have to put "sudo" infront of cp as well. Take care to note that this makes all the backup files property of root (i.e. the owner is the user, "root"). You may change the owner of an entire folder and it's (sub)contents using
```
chown -R <username>[:<groupname>] <folder>
```
Please note the colon (':') between usename and groupname if you choose to change the group as well.

Another thing: what do you mean to do by putting "etc$20BACKUP"?

---

### Post by jeroensd on 2008-06-12
Hi! Thanks for your reply. I'm still having some troubles but i'm getting there. I want to copy the etc folder into a new folder named "etc BACKUP". So the name in the script will be etc%20BACKUP  (Sorry I used the dollar sign).

The backup folder should be in the / location.

I'm gonna try to use the su and sudo commands. I'll let you know if I'm getting stuck...Thanks for the help everyone!

---

### Post by jeroensd on 2008-06-12
Hi! My script is almost finished. This is what I've got so far:

```

#!/bin/bash

echo "This script creates a backup of the /etc directory."
echo "Are you sure you want to create a backup? (yes/no):"

read answer

if [[ $answer == "yes" ]]
then
    elif [ -d /etc-BACKUP]
    then
        echo "This directory excist."
    else
        sudo mkdir /etc-BACKUP
        sudo cp -rf /etc/ /etc-BACKUP/
else
    echo "The directory will not be copied."
fi

```

But my elif code won't work. I want to check if that directory already excist. Why does it not work? 

Greetings,
Jeroen

---

### Post by jeroensd on 2008-06-12
I have it working already...I use if instead of elif.... :D

---

### Post by jeroensd on 2008-06-12
I have one more question. This is the main part of my script:

```
 
if [ $answer == "yes" ]
then
    if [ -d /etc-BACKUP]
    then
        sudo rm -r /etc-BACKUP
    fi

    sudo mkdir /etc-BACKUP
    sudo cp -rf /etc/ /etc-BACKUP/
else
    echo "No backup will be made."
fi

```


Alright, this code works almost perfectly. The script makes a backup of the etc directory but the script is placing it in de wrong map....

I want to copy all the files of the etc directory inside the etc-BACKUP directory but now the script creates a directory named etc-BACKUP and copies the whole directory etc in that directory.

So right now it looks like this:
/etc-BACKUP/etc/(files in etc)

But it should be this:

/etc-BACKUP/(files in etc)

I hope that anyone understand this. I don't know how to explain it correct. How can I do this in my code? I only want to copy all the files inside the etc folder and not the etc folder itself.

Greetings,
Jeroen

---

### Post by jeroensd on 2008-06-12
I figured this one out too. Just use this

```

sudo cp -rf /etc/* /etc-BACKUP/

```

Greetings,
Jeroen

---

### Post by victor.zamanian on 2008-06-12
Clever lad. ;-)

If you have any further questions, feel free to ask. If you feel like your script is completely finished/your problem is solved, however, please take the time to mark this thread as [SOLVED] by going into Thread Tools near the top of the page.

Kudos on figuring the stuff out!

---

