---
title: "A resume.d-script that does not work"
date: 2007-10-21
forum: General Help
---

### Post by flagel on 2007-10-21
I have a small script for overclocking my nvidia-based graphics card at every start of X. This by simply adding the script in System >Preferences > Sessions > Startup Programs. Now this script has to be run after every instance of suspend/hibernation as well so I put it in /etc/acpi/resume.d/99-nvclock.sh. However, this does not seem to work

My best guess is that since nvclock uses coolbits as backend the nvidia-driver must be loaded and maybe (I'm just speculating) it can't load while the desktop is "locked".

Any ideas?

Thanks in advance! :)
 
Here's the script btw:
#!/bin/sh
/usr/bin/nvclock -n 280 -m 500 >/dev/null 2>&1

P.S: I found a similar thread but no solution: [http://ubuntuforums.org/showthread.php?t=472830](http://ubuntuforums.org/showthread.php?t=472830)

Edit: The script runs, confirmed with letting it echo "hello world" into my home-dir. However nvclock-part doesn't work.

Edit2: The nvclock-part doesn't pipe output to any file either, weird.

Edit3: Still nothing:
#!/bin/bash
if [ -x /usr/bin/nvclock ]; then
        echo "Exe" > /home/flagel/Exe;
        sleep 30
        /usr/bin/nvclock -n 280 -m 500 > /home/flagel/nvclockoutput
fi

---

### Post by flagel on 2007-10-21
I hate to bump, but really, is there no-one who has a clue to why this doesn't work?

---

### Post by hihihi on 2008-06-09
@flagel: did u get your script to work in the meantime?

I found a solution actually after studying "man acpid":

If your script works correctly executed from the terminal, and if the permissions are set up correctly for the script to be executable, than do the follwing:

save your script somewhere else (I saved mine in my home directory /home/<username>/<directory-for-own-scripts>/special-script.sh

to start this script on resume, make a new script in /etc/acpi/resume.d
$ sudo gedit /etc/acpi/resume.d/99-extraservices.sh
enter this:

#!/bin/bash

/home/<username>/<directory-for-own-scripts>/special-script.sh [COLOR="Red"]"%e"[/COLOR]


save it and make it executable:
$ sudo chmod +x /etc/acpi/resume.d/99-extraservices.sh

to test it right away without restarting the whole system:
$ sudo killall acpid

$ sudo acpid

and now hibernate and than resume again.
should work.

you see this little "%e"?
that does the trick, quote from man acpid:
[I]The  script ... gets called and will see the complete event string
       as parameter $1.[/I]

cheers!!

---

### Post by hihihi on 2008-07-10
a second thing i learned since last post:

to check for a running process throughout a bash-script triggered by acpid, wich runs on root-level, you might have to  define the user-level, where that process started!?

so i guess in your case it could look like this:

inside your file /etc/acpi/resume.d/99-nvclock.sh 
instead of the script above, you point to your nvclock script like this:

```
#!/bin/sh

sudo -u <my username> $HOME/someFolder/myNvClockScript.sh &
exit 0
```

whereby you substitute <my username> with your username
 and $HOME/someFolder/ with the path to your script, which i called here 
"myNvClockScript.sh".
"&" gives the process an own process-tree, so nothing will have to wait for it to finish.

another option can be to add a loop that waits till x is up, before it checks for  nvclock, so it will pass the values at the right moment, like this:

```
#!/bin/bash

while true; do

        ## is desktop on?
       display=`echo $DISPLAY`
        ## Check if it is detected
       if [ "$display" = :0.0 ]; then
            
                ## If it is, get out of the loop 
                break
       fi
done

if [ -x /usr/bin/nvclock ]; then
echo "Exe" > /home/flagel/Exe;
/usr/bin/nvclock -n 280 -m 500 > /home/flagel/nvclockoutput
fi

exit 0


```

##good luck

---

