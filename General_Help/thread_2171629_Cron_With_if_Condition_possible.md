---
title: "Cron With if Condition possible?"
date: 2013-08-31
forum: General Help
---

### Post by mutiny2 on 2013-08-31
I'm very much a beginner and am using Ubuntu to act as my media server.

I have managed to figure out how to write a cron job that executes "sudo pm-hibernate" every night at 11:30.

Is it possible to put in a condition that states that if I'm currently streaming something over the network that the "pm-hibernate" command is delayed for 30min. or so?

---

### Post by CharlesA on 2013-08-31
You would have to write a script if you want to use an if statement. You would also need to check if anything is being accessed from over the network, too.

I'm not sure what program you use to access your media, but getting a script together shouldn't be too difficult with lsof, sleep and the like.

---

### Post by alexandari on 2013-08-31
You can make a script (containing the if statement and so on ) and make cron execute it

---

### Post by tgalati4 on 2013-08-31
Write a script to open your media player and put a "lock" file in /tmp.  Then  in your cron script check for the existence of the lock file and if it exists delay the hibernate.

---

### Post by mutiny2 on 2013-08-31
I figured as much that I might have to write a script and have crontab execute it. Thanks for the quick replys.

Now for my next question. How do I write an if condition script and would it be best to have it check the network activity.

 e.g. If the network activity is greater than "whatever" than delay task.

---

### Post by CharlesA on 2013-08-31
> **tgalati4 said:**
> Write a script to open your media player and put a "lock" file in /tmp.  Then  in your cron script check for the existence of the lock file and if it exists delay the hibernate.

This would probably be a better way to accomplish what you want, instead of trying to tell based on network activity.

---

### Post by mutiny2 on 2013-08-31
Okay that works. Sounds difficult. Is this something a novice could do? If so how?

---

### Post by mutiny2 on 2013-09-02
I found a python script that uses "ifstat" that I can edit to my needs. I know it's not what was recomended however, it's a good start while I'm learning.

The problem is I can't get it to work. When I run the script manually the terminal window just sits there with a blinking prompt. It doesn't matter if the network speed is above or below the 15KB target. Can someone please help fine tune it to my needs?

Objective:
Have a corn job call to the script every night at 11:30pm
The script checks for network activity using ifstat
If network activity is below the target then the computer hibernates
If the network activity is above the target then the script will not hibernate the computer
Then rechecks every 30min. for 5 cycles for the network condition

Thanks for the help

```

## Hibernate

# Set the interface you wish to monitor, eg: eth0, wlan0, usb0
INTERFACE = "eth4"


# Set the minimum download speed in KB/s that must be achieved.
MINIMUM_SPEED = 15


# Set the number of retries to test for the average minimum speed. If the average speed is less
# than the minimum speed for x number of retries, then shutdown.
RETRIES = 5


# Set the interval (in seconds), between retries to test for the minimum speed.
INTERVAL = 1800




import os, time
from commands import getoutput


def worker ():
    RETRIES_COUNT = RETRIES
    while True:
        SPEED = int(float(getoutput("ifstat -i %s 1 1 | awk '{print $1}' | sed -n '3p'" % INTERFACE)))
        if (SPEED < MINIMUM_SPEED and RETRIES_COUNT <= 0):
            os.system("pm-hibernate")
        elif SPEED < MINIMUM_SPEED:
            RETRIES_COUNT -= 1
            time.sleep(INTERVAL)
        else:
            RETRIES_COUNT = RETRIES
            time.sleep(INTERVAL)


worker()

```

---

### Post by Lars Noodén on 2013-09-02
> **mutiny2 said:**
> Okay that works. Sounds difficult. Is this something a novice could do? If so how?

Locks can be managed for you by the [flock](http://manpages.ubuntu.com/manpages/raring/en/man1/flock.1.html) utility.  See the manual page for flock, it has some short examples of how to put it into your script.  There's not a lot written about it because it is rather simple to use.

---

### Post by mutiny2 on 2013-09-02
I think I made some progress. I commented outs the INTERFACE, moved the eth4 along side ifstat and removed all referenced to INTERFACE and %.

First test showed that while the script was running with a movie streaming there was not action. I then stopped the movie and after a little bit of time the computer went into hibernation.

NOTE: I changed the interval to 20 for testing

```
## Hibernate


# Set the interface you wish to monitor, eg: eth0, wlan0, usb0
#INTERFACE = "eth4"




# Set the minimum download speed in KB/s that must be achieved.
MINIMUM_SPEED = 15




# Set the number of retries to test for the average minimum speed. If the average speed is less
# than the minimum speed for x number of retries, then shutdown.
RETRIES = 5




# Set the interval (in seconds), between retries to test for the minimum speed.
INTERVAL = 1800








import os, time
from commands import getoutput




def worker ():
    RETRIES_COUNT = RETRIES
    while True:
        SPEED = int(float(getoutput("ifstat -i eth4 1 1 | awk '{print $1}' | sed -n '3p'" )))
        if (SPEED < MINIMUM_SPEED and RETRIES_COUNT <= 0):
            os.system("pm-hibernate")
        elif SPEED < MINIMUM_SPEED:
            RETRIES_COUNT -= 1
            time.sleep(INTERVAL)
        else:
            RETRIES_COUNT = RETRIES
            time.sleep(INTERVAL)




worker()

```

---

### Post by mutiny2 on 2013-09-02
Nope, scratch that. Didn't work.

> **mutiny2 said:**
> I think I made some progress. I commented outs the INTERFACE, moved the eth4 along side ifstat and removed all referenced to INTERFACE and %.

First test showed that while the script was running with a movie streaming there was not action. I then stopped the movie and after a little bit of time the computer went into hibernation.

NOTE: I changed the interval to 20 for testing

```
## Hibernate


# Set the interface you wish to monitor, eg: eth0, wlan0, usb0
#INTERFACE = "eth4"




# Set the minimum download speed in KB/s that must be achieved.
MINIMUM_SPEED = 15




# Set the number of retries to test for the average minimum speed. If the average speed is less
# than the minimum speed for x number of retries, then shutdown.
RETRIES = 5




# Set the interval (in seconds), between retries to test for the minimum speed.
INTERVAL = 1800








import os, time
from commands import getoutput




def worker ():
    RETRIES_COUNT = RETRIES
    while True:
        SPEED = int(float(getoutput("ifstat -i eth4 1 1 | awk '{print $1}' | sed -n '3p'" )))
        if (SPEED < MINIMUM_SPEED and RETRIES_COUNT <= 0):
            os.system("pm-hibernate")
        elif SPEED < MINIMUM_SPEED:
            RETRIES_COUNT -= 1
            time.sleep(INTERVAL)
        else:
            RETRIES_COUNT = RETRIES
            time.sleep(INTERVAL)




worker()

```

---

### Post by Crusty Old Fart on 2013-09-03
I made a little toy that you can play with:
```

#!/bin/bash

# Enable extended globbing.
  shopt -s extglob

# Abort this script on first error.
  set -e

# Set the interval (in minutes) between retries to count the number of accumulated inbound Tcp segments.
  Checktime='15m'

# Set the time duration (in seconds, the default) to accumulate inbound Tcp segments.
  Tcptime=5

# Set the minimum number of accumulated inbound Tcp segments required to prevent hibernation.
  Tcpmin=10

  while true ; do
    # Clear the network statistics
      nstat -n

    # Allow time to accumulate inbound Tcp segments.
      sleep $Tcptime

    # Count the accumulated inbound Tcp segments.
      Tcpsum=$(nstat | grep TcpInSegs) || true
      Tcpsum=${Tcpsum##@(TcpInSegs)+( )} || true
      Tcpsum=${Tcpsum%@( )+(*)} || true
      (( Tcpsum > 0 )) && echo "Accumulated Inbound Tcp Segments = $Tcpsum"

    # Check if the number of accumulated inbound Tcp segments is less than the allowed minimum.
      (( Tcpsum < Tcpmin )) && break 

    # Pause looping until the next retry interval begins.
      sleep $Checktime
  done

# Replace the echo command below with your hibernate command followed by a whitespace and an ampersand character: &
  echo -e "Hibernating\n"

exit 0

```
You'll need to make it executable, of course.
Happy to answer any questions.
Have fun,

Crusty

---

### Post by mutiny2 on 2013-09-03
Fabulous! Thank you! I'll try it tonight when I get home.

> **Crusty Old Fart said:**
> I made a little toy that you can play with:
```

#!/bin/bash

# Enable extended globbing.
  shopt -s extglob

# Abort this script on first error.
  set -e

# Set the interval (in minutes) between retries to count the number of accumulated inbound Tcp segments.
  Checktime='15m'

# Set the time duration (in seconds, the default) to accumulate inbound Tcp segments.
  Tcptime=5

# Set the minimum number of accumulated inbound Tcp segments required to prevent hibernation.
  Tcpmin=10

  while true ; do
    # Clear the network statistics
      nstat -n

    # Allow time to accumulate inbound Tcp segments.
      sleep $Tcptime

    # Count the accumulated inbound Tcp segments.
      Tcpsum=$(nstat | grep TcpInSegs) || true
      Tcpsum=${Tcpsum##@(TcpInSegs)+( )} || true
      Tcpsum=${Tcpsum%@( )+(*)} || true
      (( Tcpsum > 0 )) && echo "Accumulated Inbound Tcp Segments = $Tcpsum"

    # Check if the number of accumulated inbound Tcp segments is less than the allowed minimum.
      (( Tcpsum < Tcpmin )) && break 

    # Pause looping until the next retry interval begins.
      sleep $Checktime
  done

# Replace the echo command below with your hibernate command followed by a whitespace and an ampersand character: &
  echo -e "Hibernating\n"

exit 0

```
You'll need to make it executable, of course.
Happy to answer any questions.
Have fun,

Crusty

---

### Post by mutiny2 on 2013-09-04
Your a rockstar! The script works perfectly when I manually run it. I can't seem to get the script to run from a cron. I did make the script exacuatble. Below is my crontab.

I'm guessing that that I know that the script works, the problem has to be with the crontab.

```

#SHELL=/bin/bash
#PATH='/usr/local/sbin:/usr/sbin:/sbin:/usr/local/bin:/usr/bin:/bin'
#HOME=/

29 22 * * * /home/dave/hibernate.sh

```

 I've tried all sorts of combinations:
[LIST]
[*]full path to file
[*]add shell, path, home to crontab
[*]short path to file
[*]chmod 755 for script
[/LIST]

---

### Post by Crusty Old Fart on 2013-09-04
Make sure that there is a blank line at the end of your crontab. <-- This is required.

Also, please post the output of the following command so I can see how you've built your final script:
```

cat /home/dave/hibernate.sh

```
Thanks,

Crusty

---

### Post by Crusty Old Fart on 2013-09-04
Colored text in the quote box below are my comments.
> **mutiny2 said:**
> ...
 I've tried all sorts of combinations:
[LIST]
[*]full path to file **[COLOR=green]<-- Good. It needs to be that way.[/COLOR]** 
[*]add shell, path, home to crontab  **[COLOR=red]<-- Not needed. Besides, you commented them out. You may remove those lines.[/COLOR]** 
[*]short path to file **[COLOR=red]<-- Nope. You need the full path.[/COLOR]** 
[*]chmod 755 for script **[COLOR=green]<-- That's fine.[/COLOR]** 
[/LIST]

Your crontab should work just fine if it looked like this:
```

29 22 * * * /home/dave/hibernate.sh
**[COLOR=blue]   ~~~ Replace this blue line with a blank line ~~~   [/COLOR]**

```
If it doesn't, you could try the following: **(Note: There's a whitespace between /bin/bash and /home/dave/hibernate.sh)**
```

29 22 * * * /bin/bash /home/dave/hibernate.sh
**[COLOR=blue]   ~~~ Replace this blue line with a blank line ~~~   [/COLOR]**

```
If it still doesn't work, then we need to take a close look at how you are installing the crontab.

---

### Post by mutiny2 on 2013-09-04
Great, thank you I will give these options a try tonight and I will definitely double check for that blank line at the end of the crontab.

I will also get you the output of:
```
cat /home/dave/hibernate.sh
```

I install crontab with:
```
sudo crontab -e
```
edit the file then save
once I exit it says installing new crontab

---

### Post by Crusty Old Fart on 2013-09-04
> **mutiny2 said:**
> ...I install crontab with:
```
sudo crontab -e
```
edit the file then save
once I exit it says installing new crontab
That's one way to do it. But there's another way that I like much better. I'll show it to you after we finish examining the content of your script.

---

### Post by mutiny2 on 2013-09-04
Okay I changed ownership to root, added a blank line at the end of my crontab and tryed adding /bin/bash to the crontab with a white space between it and the command. I'm about to run a second test but it doesn't look like it's working.

```
cat /home/dave/hibernate.sh
```
```

#!/bin/bash

# Enable extended globbing.
  shopt -s extglob

# Abort this script on first error.
  set -e

# Set the interval (in minutes) between retries to count the number of accumulated inbound Tcp segments.
  Checktime='1m'

# Set the time duration (in seconds, the default) to accumulate inbound Tcp segments.
  Tcptime=5

# Set the minimum number of accumulated inbound Tcp segments required to prevent hibernation.
  Tcpmin=10

  while true ; do
    # Clear the network statistics
      nstat -n

    # Allow time to accumulate inbound Tcp segments.
      sleep $Tcptime

    # Count the accumulated inbound Tcp segments.
      Tcpsum=$(nstat | grep TcpInSegs) || true
      Tcpsum=${Tcpsum##@(TcpInSegs)+( )} || true
      Tcpsum=${Tcpsum%@( )+(*)} || true
      (( Tcpsum > 0 )) && echo "Accumulated Inbound Tcp Segments = $Tcpsum"

    # Check if the number of accumulated inbound Tcp segments is less than the allowed minimum.
      (( Tcpsum < Tcpmin )) && break 

    # Pause looping until the next retry interval begins.
      sleep $Checktime
  done

# Replace the echo command below with your hibernate command followed by a whitespace and an ampersand character: &
 # echo -e "pm-hibernate" &
      "pm-hibernate" &

exit 0


```

---

### Post by Crusty Old Fart on 2013-09-04
Remove the quotes from this line:
```

"pm-hibernate" &

```
It should look like this:
```

pm-hibernate &

```

---

### Post by mutiny2 on 2013-09-04
Still nothing

It works everytime with:
```
sudo bash /home/dave/hibernate.sh
```


```

#!/bin/bash

# Enable extended globbing.
  shopt -s extglob

# Abort this script on first error.
  set -e

# Set the interval (in minutes) between retries to count the number of accumulated inbound Tcp segments.
  Checktime='1m'

# Set the time duration (in seconds, the default) to accumulate inbound Tcp segments.
  Tcptime=5

# Set the minimum number of accumulated inbound Tcp segments required to prevent hibernation.
  Tcpmin=10

  while true ; do
    # Clear the network statistics
      nstat -n

    # Allow time to accumulate inbound Tcp segments.
      sleep $Tcptime

    # Count the accumulated inbound Tcp segments.
      Tcpsum=$(nstat | grep TcpInSegs) || true
      Tcpsum=${Tcpsum##@(TcpInSegs)+( )} || true
      Tcpsum=${Tcpsum%@( )+(*)} || true
      (( Tcpsum > 0 )) && echo "Accumulated Inbound Tcp Segments = $Tcpsum"

    # Check if the number of accumulated inbound Tcp segments is less than the allowed minimum.
      (( Tcpsum < Tcpmin )) && break 

    # Pause looping until the next retry interval begins.
      sleep $Checktime
  done

# Replace the echo command below with your hibernate command followed by a whitespace and an ampersand character: &
 # echo -e "pm-hibernate" &
      pm-hibernate &

exit 0

```

---

### Post by Crusty Old Fart on 2013-09-04
Please post the output of the following command:
```

crontab -l

```

---

### Post by mutiny2 on 2013-09-04
current crontab
```
38 17 * * * /home/dave/hibernate.sh


```

installed with:
```
sudo crontab -e
```

```
$ crontab -l
no crontab for dave
```

---

### Post by Crusty Old Fart on 2013-09-04
Okay, now post the output of this command:
```

pm-is-supported --hibernate && echo yes || echo no

```

---

### Post by mutiny2 on 2013-09-04
```
$ pm-is-supported --hibernate && echo yes || echo no
yes


```

---

### Post by Crusty Old Fart on 2013-09-04
Please create a file: /home/dave/hibernate_cron.tab
Then copy and paste the following text into it:
```

# System crontab can be located using the following
# command at the b prompt: which crontab
#
# Uncomment the following line to suppress mailings from cron.
    MAILTO=""
#
# Set chmod 700 or 755 for cron scripts
#
# mh = minute of the hour
# hd = hour of the day 
# dm = day of the month
# my = month of the year
# dw = day of the week
# command = full path to the scheduled script
#
# mh hd dm my dw command
#
  38 17 * * * /home/dave/hibernate.sh
#
# There must be a blank line at the end of this file.


```
Make sure there is a blank line below the last comment. The code box above may have removed it.
When you're done, please post the output of the following command:
```

cat /home/dave/hibernate_cron.tab

```

---

### Post by mutiny2 on 2013-09-04
```
$ cat /home/dave/hibernate_cron.tab
#
# System crontab can be located using the following
# command at the b prompt: which crontab
#
# Uncomment the following line to suppress mailings from cron.
    MAILTO=""
#
# Set chmod 700 or 755 for cron scripts
#
# mh = minute of the hour
# hd = hour of the day 
# dm = day of the month
# my = month of the year
# dw = day of the week
# command = full path to the scheduled script
#
# mh hd dm my dw command
#
  38 17 * * * /home/dave/hibernate.sh
#
# There must be a blank line at the end of this file.


```
I did add a blank line, the comment box removes it

---

### Post by Crusty Old Fart on 2013-09-04
[color=red]**Edit: I was wrong about a lot of this. See strike-throughs and comments in bold, red text.**[/color]

As you can see, the code box removes the blank line at the bottom.

You have been installing your crontab as root, because you have been using sudo.
[color=red][s][color=black]And since you are signed into your computer as dave, then root's crontab doesn't run because you're running a user session.[/color][/s] **<-- This isn't true. Consequently, it makes the rest of this post irrelevant.**[/color]
[color=red][s][color=black]Now we'll fix that.
Remove the existing crontab with the following command:
```

sudo crontab -r

```
Now we'll create a crontab for dave, by installing the file you just created as the source code for dave's crontab
Don't use sudo for anything unless I tell you to.
```

crontab /home/dave/hibernate_cron.tab

```
Finally, without using sudo, post the output from this command:
```

crontab -l

```[/color][/s][/color]

---

### Post by mutiny2 on 2013-09-04
```

$ crontab -l
#
# System crontab can be located using the following
# command at the b prompt: which crontab
#
# Uncomment the following line to suppress mailings from cron.
    MAILTO=""
#
# Set chmod 700 or 755 for cron scripts
#
# mh = minute of the hour
# hd = hour of the day 
# dm = day of the month
# my = month of the year
# dw = day of the week
# command = full path to the scheduled script
#
# mh hd dm my dw command
#
  38 17 * * * /home/dave/hibernate.sh
#
# There must be a blank line at the end of this file.


```

---

### Post by Crusty Old Fart on 2013-09-04
Good.
Now edit your crontab to see if the script works by changing the minute and hour using the command:
```

crontab -e

```
Again, don't use sudo.
Let's see if that fixes things.

---

### Post by mutiny2 on 2013-09-04
Doesn't seem to be doing anything.

```

$ crontab -l
#
# System crontab can be located using the following
# command at the b prompt: which crontab
#
# Uncomment the following line to suppress mailings from cron.
    MAILTO=""
#
# Set chmod 700 or 755 for cron scripts
#
# mh = minute of the hour
# hd = hour of the day 
# dm = day of the month
# my = month of the year
# dw = day of the week
# command = full path to the scheduled script
#
# mh hd dm my dw command
#
  59 18 * * * /home/dave/hibernate.sh
#
# There must be a blank line at the end of this file.



```

---

### Post by Crusty Old Fart on 2013-09-04
Okay...There's something else going on that may need some changes to the script. I'll give you a new one with the changes in it As soon as I can. It should only take a few minutes.

---

### Post by mutiny2 on 2013-09-04
Awesome! Thank you. I really appreciate all the time your putting into this.

---

### Post by Crusty Old Fart on 2013-09-04
[color=red]**Edit: With the exception of the unnecessary code in the box below, this would have probably worked if it had been called using sudo from root's crontab.**[/color]

I made changes to the top and the bottom of the file. So, please replace the entire contents of /home/dave/hibernate.sh with the code in the following box:
```

#!/bin/bash

# Enable extended globbing.
  shopt -s extglob

[color=red][s][color=black]# Export display so cron can run this script.
  export DISPLAY=:0.0[/color][/s]** <-- This line and the one directly above were unnecessary.**[/color]

# Abort this script on first error.
  set -e

# Set the interval (in minutes) between retries to count the number of accumulated inbound Tcp segments.
  Checktime='15m'

# Set the time duration (in seconds, the default) to accumulate inbound Tcp segments.
  Tcptime=5

# Set the minimum number of accumulated inbound Tcp segments required to prevent hibernation.
  Tcpmin=1000

  while true ; do
    # Clear the network statistics
      nstat -n

    # Allow time to accumulate inbound Tcp segments.
      sleep $Tcptime

    # Count the accumulated inbound Tcp segments.
      Tcpsum=$(nstat | grep TcpInSegs) || true
      Tcpsum=${Tcpsum##@(TcpInSegs)+( )} || true
      Tcpsum=${Tcpsum%@( )+(*)} || true
      (( Tcpsum > 0 )) && echo "Accumulated Inbound Tcp Segments = $Tcpsum"

    # Check if the number of accumulated inbound Tcp segments is less than the allowed minimum.
      (( Tcpsum < Tcpmin )) && break 

    # Pause looping until the next retry interval begins.
      sleep $Checktime
  done

# Hibernate
pm-hibernate &

exit 0

```
Then you can test again by adjusting your minute and hour again using:
```

crontab -e

```

[color=red][s][color=black]By the way, all of the things we've fixed so far needed to be fixed. So nothing we've done should be put back to the way it was before we started tonight.[/color][/s]** <-- Oh boy! Was I ever wrong about that. The small changes we made in the script weren't too bad, but most of what we've been doing with crontabs will be completely redone.**[/color]
For this run I've also changed Tcpmin to 1000 to force hybernation even if the network traffic is high.
Let's see how it goes this time.

---

### Post by Crusty Old Fart on 2013-09-04
Damn! I still have a bug somewhere.
I need to spend some time testing everything we've been doing tonight on my machine to make sure cron can run what we're doing.
This could take a while, so I won't keep you any longer tonight.
When I get everything running as it should. I'll post again.
I might be ready in an hour or so, or maybe not until morning.
Fortunately, we haven't wasted too much time tonight because we fixed several things that needed to be fixed.
Keep both of the files we made in your home directory for now. We may need them again soon.
Unless you post some questions for me, I'll be busy pulling rabbits out of my hat.

---

### Post by mutiny2 on 2013-09-04
Sounds good, thank you

---

### Post by Crusty Old Fart on 2013-09-04
You're mighty welcome, Dave.
My pleasure,

Crusty

---

### Post by Crusty Old Fart on 2013-09-05
**[COLOR=red]Edit: Re-written to remove the security risk associated with user ownership and write permission to files that should be restricted to root only.[/COLOR]**

Okey dokey, Dave.
I have everything nailed on my system now, let's hope it works on yours as well.

There's a fair amount of work to do, so I'll take you through it all step by step.

Before getting into the details, here's a brief description of what we'll be doing, just so you can get somewhat of an understanding of the whole process before we jump into the commands.

[LIST]
[*]The first thing we'll do is clean up the mess we made yesterday. We'll be getting rid of the files we made in your home directory, as well as the crontabs for both dave and root. 
[*]Then, we'll download a new script and a new file containing the source code for root's crontab. The crontab source file will be downloaded with a .txt extension. After it has made its way to you, we'll change its extension to .tab. Then we'll tightening the security settings on these files to prevent a hacker from being able to gain full root access to your computer. 
[*]Lastly, we'll install root's crontab, and have you take the whole enchilada for a test drive. 
[/LIST]

Now, look at me, this is VERY IMPORTANT: Don't use "sudo" unless I've included it in a command or told you it was okay if you needed it. Thanks.

Also, you may know this already but just in case you don't, you can copy commands out of code boxes, paste them into your shell next to your user prompt, and then hit [Enter]. This saves a lot of time and cuts way down on typing errors. Just make sure that when you're dragging your mouse that you copy the entire command and nothing more. Take a good look at what you pasted to make sure its right before you hit [Enter].

So, here we go:

Execute the following two commands one at a time. They will remove the two files we don't need anymore. If you need to use "sudo" with them, it's okay.
```

rm /home/dave/hibernate.sh
rm /home/dave/hibernate_cron.tab

```
The next two commands will remove the crontabs from yesterday. The first command removes the crontab for: dave. The second command removes the crontab for: root. In order for this to work, "sudo" must NOT be used with the first command, and MUST be used on the second command as shown in the code box below:
```

crontab -r
sudo crontab -r

```
Now we'll download the files we need, they must be saved in your home directory: /home/dave
Download the script by clicking on this --> **[attach]246026[/attach]**
Download the crontab source file by clicking on this --> **[attach]246027[/attach]**

When you have the two files downloaded and saved in your home directory, do the following:

Change the name of the crontab source file:
```

mv /home/dave/hibernate_cron.txt /home/dave/hibernate_cron.tab

```

**[COLOR=red]Now we need to change ownership and allow access to these files by root only. This is very important. Please run the following commands, one at a time.[/COLOR]**
```

sudo chown root:root /home/dave/hibernate_cron.tab
sudo chown root:root /home/dave/hibernate.sh
sudo chmod 700 /home/dave/hibernate_cron.tab
sudo chmod 700 /home/dave/hibernate.sh

```

Install root's crontab using sudo:
```

sudo crontab /home/dave/hibernate_cron.tab

```

Now you can take a test drive. Edit the hour and minute parameters in root's crontab using sudo:
```

sudo crontab -e

```

That's it. If I haven't hosed my instructions, it should work.
You may have to wait several seconds before the 'puter hibernates and turns itself off.
This code works perfectly on my machine now. If it doesn't on yours, I may have made a typo or some other simple mistake that should be quick and easy to fix.

I'm about to pass out now, so I think I'll crawl into bed before I tip over and crash on the floor.

Good night, Dave.

And Good Luck,

I'll be checking here to see how things went when I wake up.

---

### Post by mutiny2 on 2013-09-05
Very cool! Thank you for all that you've done. I want to play with it now but can't... stupid work. Haha

---

### Post by Crusty Old Fart on 2013-09-05
In order to make absolutely sure that what we've done is not exposing your computer to root access by a hacker. Please post the output from the following command:
```

ls -al ~ | grep hibernate

```
Thanks,

Crusty

---

### Post by mutiny2 on 2013-09-05
BINGO! It's working perfectly and I can't thank you enough.

At first nothing, it wasn't working with;
```

44 17 * * * sudo /home/dave/hibernate.sh > /dev/pts/0

```

I then just tryed:
```
sudo bash /home/dave/hibernate.sh
```
An like before it worked in bash but not crontab.

So what the heck I changed:
```

44 17 * * * sudo /home/dave/hibernate.sh > /dev/pts/0

```
to
```

44 17 * * * sudo bash /home/dave/hibernate.sh

```

BAM! works like a charm. Below is the info you requested.


```

$ ls -al ~ | grep hibernate
-rwx------   1 root root     528 Sep  5 17:21 hibernate_cron.tab
-rw-rw-r--   1 dave dave       0 Sep  4 18:03 hibernate_cron.tab~
-rwxrwxr-x   1 dave dave     929 Sep  2 07:07 hibernateonnetwork.py~
-rw-rw-r--   1 dave dave       0 Aug 31 17:04 hibernate.py~
-rwxrwxr-x   1 dave dave     963 Aug 31 17:52 hibernateserver.py~
-rwx------   1 root root    1803 Sep  5 18:20 hibernate.sh
-rwxrwxr-x   1 dave dave    1259 Sep  3 21:30 hibernate.sh~
-rwxrwxr-x   1 dave dave     929 Sep  2 07:06 hibernatetest.py~



```

---

### Post by Crusty Old Fart on 2013-09-05
Good job, Dave...nice debug there. My guess it that I didn't need to use bash in the crontab because of what's in my root PATH environment variable. No biggy though. Glad you got it working.
The output I asked for looks good as well.

 I should tell you that if you ever call a script from root's crontab in the future, you should make root the owner of it AND change its permission level to 700. Otherwise, you could be leaving you computer at risk of being completely "owned" by a malicious hacker. Part of the reason for this is that root can run sudo without providing a password, which is why we had to call the script from root's crontab.

I am in the process of writing up some notes for you on "tuning" the network activity parameters in the script. They aren't ready yet.

Oh, did you see any output coming to your terminal window when the cronjob ran?

---

### Post by mutiny2 on 2013-09-05
Again I can't thank you enough. I really appreciate you taking the time, not only to put together the script but taking the time to teach and explain how and why it works.

When the crontab runs I didn't see any output however, when I ran the script in the terminal got:
```

Accumulated Inbound Tcp Segments = 5                 

Hibernating...
This may take several seconds
and your screen may blink before shutting down.
Please wait...


Shutting down...
This may take several more seconds.
Please wait...



```

---

### Post by Crusty Old Fart on 2013-09-05
Yeah...I just noticed that before your post came in. The reason is that you removed the code I had written to redirect the output from cron to your terminal, which is what the **[COLOR=blue]blue code[/COLOR]** in the box below does. I did this to make tuning the network parameters easier. You might want to fix this line in root's crontab, as well as in the hibernate_cron.tab file:
```

44 17 * * * sudo bash /home/dave/hibernate.sh **[COLOR=blue]> /dev/pts/0[/COLOR]**

```
This sends the output to the terminal window running from file: /dev/pts/0

The following command will cause a terminal window to tell you what file its running from:
```

tty

```
If it tells you something that isn't: /dev/pts/0 , you can close all your terminal windows, and open another one up. The new window should be running from file /dev/pts/0 then. And cron will send its output to it.

You're quite the little hacker, Buddy :cool:

---

### Post by Crusty Old Fart on 2013-09-05
> **mutiny2 said:**
> Again I can't thank you enough. I really appreciate you taking the time, not only to put together the script but taking the time to teach and explain how and why it works.
...
Wow, Dave. What a nice thing to write. Thank you very much. It feels good to be appreciated. I really appreciate you expressing your appreciation.

I should apologize for my ineptitude and any confusion I may have caused you, or anyone else reading this thread, once we got into working on cron. It has been years since I've been immersed so deeply into the intricacies of that area of Unix. Unfortunately, I fell flat on my face with it. In order to prevent leading anyone astray who may read this thread later, I've gone back and edited my postings to point out where I was wrong and was under the impression that certain things were true, when in fact, they were not. Very sorry about all that.

---

### Post by Crusty Old Fart on 2013-09-06
The script detects incoming Tcp segments whether they are coming from a machine on your home network (LAN) or the Internet (WAN) or both.

In order to have the number of incoming Tcp segments detected drop to zero, there must not be any incoming data from the LAN or the WAN. Even if you aren't intentionally streaming anything in from the Internet, you may still receive incoming Tcp segments if: your email client is running and is automatically checking for new mail periodically and/or your browser is open to a web page that has been coded to automatically update periodically -- several news related websites do this.

Since the script won't hibernate until the number of incoming Tcp segments drops below the minimum setting of the parameter: Tcpmin, WAN traffic may prevent hibernation if you set Tcpmin too low and/or allow too many Tcp segments to accumulate by setting the parameter: Tcptime too high.

Conversely, if Tcpmin is set too high and/or Tcptime is set too low, the script could force premature hibernation.

The frequency at which the script checks the Tcp traffic is controlled by specifying the interval of time to elapse between checks. This is done by changing the value assigned to the parameter: Checktime.

Tuning these parameters is done by editing hibernate.sh and changing their values. The block of code where these parameters are set is now more conspicuously marked with a banner heading in the file as follows:
```

# +-------------------------------------------------------------------+
# | Parameter settings may be changed in the following block of code. |
# +-------------------------------------------------------------------+

# Set the interval (in minutes) between retries to count the number of accumulated inbound Tcp segments.
  Checktime='15m'

# Set the time duration (in seconds, the default) to accumulate inbound Tcp segments.
  Tcptime=5

# Set the minimum number of accumulated inbound Tcp segments required to prevent hibernation.
  Tcpmin=1000


```

Below this block of code is another banner that warns against editing the code below it. This code is somewhat cryptic and can be easily broken by someone unfamiliar with some of the more advanced techniques in bash, like using extended globbing to enhance the string trimming capabilities of parameter expansion. The warning, unapologetically, looks like this:  
```

# +------------------------------------------------------------------------------+
# | Do not edit any of the code below unless you know EXACTLY what you're doing. |
# +------------------------------------------------------------------------------+

```

I think that about wraps it up for me, Dave.
It's been a pleasure working with you on this little project.
I've really enjoyed it.

I'll stay subscribed to this thread for another week or so, and will be happy to answer any further questions you may have.

In the meantime, I'll leave you with my buddy, Darthroy.
May the force be with you. :cool:

Crusty
```


                         _---_
                        /_/|\_\
                       (/-O^O-\)
                __    /_\\/*\//_\    __
         ------vVVv----- o###o -----vVVv------
                          """

                   Darthroy was here.


```

---

### Post by ralf_b2 on 2014-05-09
i think this is what im looking for, but.... ....is it possible to add a ping query? so that my server dont shutdown if a computer in my network is "online"?

---

### Post by Herbon on 2014-05-10
X

---

