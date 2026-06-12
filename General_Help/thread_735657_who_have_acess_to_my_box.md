---
title: "who have acess to my box?"
date: 2008-03-25
forum: General Help
---

### Post by bone2006 on 2008-03-25
I have ubuntu server installed and had a bunch of users, not all had a home directory.  I removed a lot of users, but can't seem to find a command to see who has access to the box or is cable of logging in?
I removed the users with sudo deluser username if it matters

---

### Post by ibuclaw on 2008-03-25
I'll have a look round for you, but for the moment, the only thing I know is checking the list of users who have logged into your server in the last week (I think, though it may be month, or since the computer first booted)

```
 users /var/log/wtmp 
```

Though if you feel that you have a lot of users, you may want to have the less command with it, so you can scroll up and down with the arrow keys.

```
 users /var/log/wtmp | less 
```

Be warned, though as it will show recurrences of the same user

here's my output of that command, it's rather short because I've recently done a clean install of Hardy.
> 
user1 user1 user1 user1 user1 user1 user1 user1 user1 user1 user1 user1 user1 user1 user1 user2 user2 user3 user3 user3 user3 user3 user3 user3 user3 user3 user3 user3 user3 user3 user3 user3


It's not good, I know, but I'm working on it and I'll get back to you as soon as I find a proper command.

[EDIT]
Changed my quote as it is misleading, the output printed are the users in alphabetical  order and the recurrences are the number of times they have logged in.
So it is possible to create a small BASH script to take these details in and print out the information in a neat, presentational way.

---

### Post by sumguy231 on 2008-03-25
Hmm, thanks tinivole, I didn't know about /var/log/wtmp. bone2006, you also might find /var/log/auth.log useful for more detailed information.

---

### Post by ibuclaw on 2008-03-25
Well, here's a script I've just written that prints out the /var/log/wtmp list in a clean manner.

```

#!/bin/bash

### Function ###
printusers() {
thisuser=""
nextuser=""
numlogins="0"
    while [ $# -gt 0 ]
    do
        export thisuser="$1"
        let "numlogins++"
        shift
        export nextuser="$1"

        while [ "$numlogins" != "0" ]
        do
            if [ "$thisuser" == "$nextuser" ]
            then
                shift
                export nextuser="$1"
             else
                echo " $thisuser"
                export numlogins="0"
            fi
        done
    done
}

### Main ###
echo
getusers=$(users /var/log/wtmp)
printusers $getusers
echo

```

Save it to a text file and mark it executable (chmod +x scriptname).
And upon executing (./scriptname)
It will print something like this
> 
 user1
 user2
 user3

Note that this will only print the users who have logged into your server (So I presume that that would be everyone, but you never know)
Hope this helps

Regards
Iain

---

### Post by bone2006 on 2008-03-26
thanks so much for the reply, the command:
users /var/log/wtmp | less

worked well, but I was not looking so much to who has logged on, but who has access to the box.  

I just created a new account sudo adduser test
users /var/log/wtmp | less
will only display somebody who has logged on.  I thought it would be easier to determine who has accounts on my system.

---

### Post by Oldsoldier2003 on 2008-03-26
> **bone2006 said:**
> thanks so much for the reply, the command:
users /var/log/wtmp | less

worked well, but I was not looking so much to who has logged on, but who has access to the box.  

I just created a new account sudo adduser test
users /var/log/wtmp | less
will only display somebody who has logged on.  I thought it would be easier to determine who has accounts on my system.

cat /etc/passwd will show all users on the system (including system accounts)

---

### Post by ibuclaw on 2008-03-29
I almost forgot about this:

looked at the /etc/passwd file.
Then made this up.

```

#!/bin/bash
    activeusers=$(awk -F: '{if ($3>=1000 && $3 < 65534) print $1}' /etc/passwd)
    echo "$activeusers"

```

Prints all users with IDs from 1000 to 65534.

or lets go for a one-liner.
```
 awk -F: '{if ($3>=1000 && $3 < 65534) print $1}' /etc/passwd 
```

If anyone reads this.
Hope this proves very useful in the future.

Regards

---

### Post by bone2006 on 2008-03-31
thanks that was what I was looking for

---

