---
title: "Help - Purging old kernels with cron job - Questions"
date: 2013-11-07
forum: General Help
---

### Post by jcllings on 2013-11-07
Step 1: Write a script

Step 2: Write a cron job that calls the script weekly.

So I see that: 

```
dude@desktop:~$ dpkg --get-selections | egrep linux-image-[0-9] | sort
linux-image-3.2.0-39-generic            deinstall
linux-image-3.2.0-40-generic            deinstall
linux-image-3.2.0-41-generic            deinstall
linux-image-3.2.0-43-generic            deinstall
linux-image-3.2.0-44-generic            deinstall
linux-image-3.2.0-45-generic            deinstall
linux-image-3.2.0-48-generic            install
linux-image-3.2.0-49-generic            install
linux-image-3.2.0-51-generic            install
linux-image-3.2.0-52-generic            install
linux-image-3.2.0-53-generic            install
linux-image-3.2.0-54-generic            install
linux-image-3.2.0-55-generic            install

```

All of these are installed but some are marked for removal already.  This is true because I see them all in /boot and uname shows "3.2.0-55-generic".

Questions: 
1. How did some of them get marked for deinstall? 
2. Can't I just grep these for "deinstall" and then call the command that executes the selected operation?  This would assume that somehow these are getting selected for deinstall automagically as they age or as new kernels are added.

---

### Post by ian-weisser on 2013-11-07
A weekly cron script seems like overkill.
I clean out mine every six months after a release upgrade. Manually. Just takes a minute.

If I were to script it, I would base the script on what I actually have in /boot.

---

### Post by XBNCPRk on 2013-11-07
Theres several dozen scripts on here and google that do just that, and can remove all but the current, or all but the current plus 1 back, 2 back, etc. I typically keep the current, and one back just to keep my boot drive pared to a reasonable minimum. Id agree also that weekly is more often than you might need, but theres no harm in it running that often. 
For instance [http://askubuntu.com/questions/244732/is-this-command-to-remove-old-kernels-safe-to-use](http://askubuntu.com/questions/244732/is-this-command-to-remove-old-kernels-safe-to-use)  The one selected as best answer has worked nicely for me.

Also pretty sure apt-get autoclean will leave you with your current kernel + one previous now, as of 12.04. Anyone know firsthand if thats the case?

---

### Post by jcllings on 2013-11-23
This was my solution which was called from a cron job but you can actually handle this with the Ubuntu Tweak GUI which you can just grab and install. 

```

#!/bin/bash
# We need to make sure the kernel we are using isn't removed, so lets get the version.
CURRENT_VERSION=`uname -r`

#Build the initial list, excluding the current kernel version.
#Note that the package name "linux-image" as opposed to linux-image-* is documentation, not a kernel.  
LIST=`dpkg --get-selections | egrep linux-image-[0-9] | grep -v ${CURRENT_VERSION} | sort | awk '{ print $1 }'`
ARRAY=(${LIST})

#We want to keep at least 2 besides the one currently in use, so lets get the integer size of the list for some math. 
declare -i SIZE
SIZE=`echo $LIST | tr ' ' '\n' | grep -c linux`

#Size becomes size - 2
SIZE=${SIZE}-2

if [ ${SIZE} -gt 0 ];then
    #Iterate over the array for all items 0 to size. 
    for I in ${ARRAY[@]:0:${SIZE}};
    do
        apt-get -y purge $I
    done
    
else
    echo "No kernels available to be removed."
fi


```

---

### Post by ian-weisser on 2013-11-23
Do keep in mind that the /etc/kernel/postinst.d/apt-auto-removal script, included with the *apt* package, is intended to keep a maximum of three older kernels on the system. The script has had a few issues (as seen here with users with full /boot partitions and lots of kernels), but the 14.04 version is startling to look a lot more effective.

Make sure your script doesn't conflict with or duplicate it's work.

---

