---
title: "Restart of a program wihin a screen session"
date: 2015-05-20
forum: General Help
---

### Post by ELMIT on 2015-05-20
I have a program, that I start with a bash script in one screen session ("A") - it is a Java
I have another program, that I start with a bash script in onother screen session ("B") - It is a Node

B connects via sockets to A.
It works fine a couple of months, then on one day I get several times the situation that B cannot connect to A.
During that time the Java uses a load of up to 500, while during normal operation, it is just at 20.

To fix that, I just have to close A and B and restart it.

For security reason only a couple of IP addresses can login to that server. That situation appears most of the time, when I am not at such IP address.

I want to find a solution to (either or together):

1. shutdown A 
2. shutdown B

I have no idea how I can find a trigger for that. So I thought, maybe I can create a hidden php page, that touches a file. And a cron task could check for that file, and kill that task and re-start it.

How can I implement this so, that it is still running in this screen session?

---

### Post by nerdtron on 2015-05-20
It would be better if you create a php page that would create a file, then check if that file exists, then reboot both machines:
 Example:

```

if [ -f /var/checkfile.txt ];  # check if a file is create
then
    echo "checkfile exist."
    rm -f /var/checkfile.txt      # delete the check file so that it won't exist on next check
    reboot                        # reboot the computer
fi


```

Then for example you can add this script to crontab and check the file every hour.

EDIT: by shutdown, you mean shutdown the application and not the PC it self?

You terminate the screen (thereby terminate the application inside) and then just spawn another screen session. You can do it via a single command too. This command will create a screen session and then run the command inside it. You can then put this on your scripts.
```
 screen -S "screen-name-here" "./myscript or application command here"
```

---

### Post by ELMIT on 2015-05-20
Thanks, that is a great start!

I still have some doubts how to do it in details:

1. a cron check with a bash file as you suggested to check for a trigger file

2. I want to kill the screen program, not reboot the computer
How does the script know which task(s) to kill? I know the screen name I gave (and will give the next time again)

3. I tried a test to start a new screen with:
screen -S "A" "top"

I see top now running.
I need to start two screens, for "A" and "B"

When I CTRL-A + d and:
screen -ls
There is a screen on:
	513.A	(05/20/2015 08:10:24 PM)	(Detached)
1 Socket in /var/run/screen/S-ronald.

I can now kill -9 513
screen -ls
There is a screen on:
	513.A	(05/12/2015 01:00:07 AM)	(Dead ???)
Remove dead screens with 'screen -wipe'.
1 Socket in /var/run/screen/S-ronald.

I have to use screen -wipe to get rid of the dead screens.

---

### Post by Lars Noodén on 2015-05-20
> **ELMIT said:**
> 2. I want to kill the screen program, not reboot the computer
How does the script know which task(s) to kill? I know the screen name I gave (and will give the next time again)

3. I tried a test to start a new screen with:
screen -S "A" "top"

What about having that session quit?

```

screen -S A -X quit

```

As far as I know, that should take out any processes under it.

---

### Post by nerdtron on 2015-05-20
You 2 and 3 requirements were addressed by Lars above. 

As for the script to check the existence of a file:
(assuming you use php to create the file, I doesn't matter how you do it, and I'm not familiar with PHP).

First create a script, say you saved it as /home/user/checker.sh with the following contents:
```

#!/bin/bash
if [ -f /var/checkfile.txt ];  # check if a file is create
then
    echo "checkfile exist."
    rm -f /var/checkfile.txt      # delete the check file so that it won't exist on next check
    screen -S "screen-name" -X quit   # quit the "screen-name" screen
    screen -S "screen-name" "full-path-command-to-run-inside-screen-here"    # this will create a new screen session
fi

```
Modify it to your needs, say if you need to quit two screen sessions, then create two new screens, just add them there. Save the file.

As for the cron job to check every hour, you'll need to edit the crontab.
If you run your screen scripts as root or sudo, you need to edit the crontab as sudo too:
```
 sudo crontab -e 
```

Now on the last line, add the following entry to run the script you created every hour.
```
 @hourly /bin/bash  /home/user/checker.sh 
```

Save and exit. To verify that you have the crontab entry:
```
 sudo crontab -l 
```

---

### Post by ELMIT on 2015-05-21
Almost, as I need it ;-)


The program I start in the screen session needs to be started in a certain directory and it produces a log file ( > A.log  and > B.log ).

I tried:

Code:
> #!/bin/bash
if [ -f /var/checkfile.txt ];  # check if a file is create
then
    echo "checkfile exist."
    rm -f /var/checkfile.txt      # delete the check file so that it won't exist on next check
    screen -S "screen-name-A" -X quit   # quit the "screen-name" screen
cd /path/to/start/A
    screen -S "screen-name-A" "ls -l > 1.txt"    # this will create a new screen session
    screen -S "screen-name-B" -X quit   # quit the "screen-name" screen
cd /path/to/start/B
    screen -S "screen-name-B" "ls -l > 2.txt"    # this will create a new screen session
fi


I only get:
Cannot execute ls -l > 1.txt : No such file or directory

and the screens are terminated

---

### Post by Lars Noodén on 2015-05-21
> **ELMIT said:**
> I only get:
Cannot execute ls -l > 1.txt : No such file or directory

and the screens are terminated

That causes screen to look for "ls -l > 1.txt"

I think you'd have to wrap your line in its own shell

```

screen -S "screen-name-B" sh -c "ls -l > 2.txt" 

```

Or else use screen's own logging to catch everything else in that screen window, too.

```

screen -L -S "screen-name-B" ls -l 

```

But either way, screen will then terminate when 'ls' finishes.

---

### Post by ELMIT on 2015-05-21
No, these two methods do not work at all.

---

### Post by Lars Noodén on 2015-05-21
When run with just *ls* it will drop through to "[screen is terminating]" but it will have run.  Check the outout from the file or screen log.  You'll have to run it against something ongoing like ping or top to see screen in action because when a command is specified as an argument screen will terminate when the command finishes.  I'm not sure of a way to do it in screen, but tmux has an option for keeping the session active even after the command terminates, using the setting "remain-on-exit"  I mostly use tmux these days because it is a little more organized to figure out.

---

### Post by ELMIT on 2015-05-23
Yes, it works:

screen -L -S "screen-A" sh -c "./A.js"

Thanks!

Actually I could add a little thing to create this checkfile.txt

The log file of the current session contains some triggerlines. If these triggerlines come to often at the past lines, than this checkfile.txt could be created

tail screenlog.0
line -10    No triggerword
line -9     TRIGGERWORD
line -8     TRIGGERWORD
line -7     TRIGGERWORD
line -6     No triggerword
line -5     TRIGGERWORD
line -4     TRIGGERWORD
line -3     No triggerword
line -2     TRIGGERWORD
line -1     TRIGGERWORD

What bash one-liner could I use to touch checkfile.txt if the TRIGGERWORD occurs 5 out of 10 times at the end of the screenlog.0 file?

---

### Post by Lars Noodén on 2015-05-23
If you just want to check the last ten every once in a while, then you could do something like this with awk:

```

tail -n 10 checkfile.txt | awk 'BEGIN{ count=0 } /TRIGGERWORD/ {count++;} END { if ( count>=5 ) { system( "echo run in circles, scream and shout" );  } }' 

```

system() launches what you have in the quotes, there above it is just an 'echo' but it could be another script or something.

If you want it to track live, then you probably need to do something with a named pipe and I'm not sure if awk waits around for more input so it may be necessary to escalate to perl.

---

### Post by Lars Noodén on 2015-06-01
If you want to track a running total, then something like this might work:

```

#!/usr/bin/perl                                                                                                  

use strict;
use warnings;

open(LOG, "+<", "checkfile.txt") # rw mode needed to keep file open as it fills                                  
    or die("$!\n");

my @queue = (); # buffer                                                                                         

while ( my $line = <LOG> ) {

    push( @queue, $line );      # add item to queue                                                              

    if ( $#queue >= 10 ) {      # count starts at zero                                                           
        shift( @queue );        # trim queue down to max length                                                  
    }

    if ( grep( /TRIGGERWORD/, @queue ) >= 5 ) {
        system( "echo", "run in circles, scream and shout" );
        @queue = ();    # reset counter                                                                          
    }

}

close( LOG );

```

---

### Post by ELMIT on 2015-07-12
I thought it was solved, but it still has a problem.

I have to start job-a in one screen and job-b in another screen

> kill -9 `ps ax | grep Job-A`
kill -9 `ps ax | grep Job-B`


cd ~/Job-A
screen -S "Job-A" -X quit   # quit the "Job-A" screen
screen -L -S "Job-A" sh -c "./run-a.sh"   # -L results in ~/Job-A/screenlog.0

cd ~/Job-B
screen -S "Job-B" -X quit   # quit the "Job-B" screen
screen -L -S "Job-B" sh -c "./run-b.js"   # -L results in ~/Job-B/screenlog.0


Problem is, that Job-A will be started, but it does not detach, therefore Job-B does not start at all.

How can I solve that?

BTW, is it possible to name the screenlog.0    like  Job-A.log  ???

---

### Post by nerdtron on 2015-07-12
> **ELMIT said:**
> I thought it was solved, but it still has a problem.

I have to start job-a in one screen and job-b in another screen



Problem is, that Job-A will be started, but it does not detach, therefore Job-B does not start at all.

How can I solve that?

I noticed you used, "screen -S" have you tried "screen -dmS" instead which forces the screen to detach immediately.

> BTW, is it possible to name the screenlog.0    like  Job-A.log  ???
I believe so. Just rename it and see if the log file is created.

---

### Post by ELMIT on 2015-07-12
I replaced:
screen -L -S "Job-A" sh -c "./run-a.sh" 

1.
screen -L -dmS "Job-A" sh -c "./run-a.sh" 

results in    No screen session found.

2.
screen -L -d -S "Job-A" sh -c "./run-a.sh" 

results in    There is no screen to be detached matching Job-A.

3.
screen -L -d -m -S "Job-A" sh -c "./run-a.sh" 

results in    No screen session found.

4.
screen -L -S "Job-A" sh -c "./run-a.sh" 
screen -d "Job-A"

results   waiting till  I key in   CTRL-A d

---

### Post by Lars Noodén on 2015-07-13
> **ELMIT said:**
> BTW, is it possible to name the screenlog.0    like  Job-A.log  ???

You might try experimenting with .screenrc  The section "CUSTOMIZATION" in the manual page for screen has a lot of information, specifically the *logfile* option.  What is missing, as far as I can tell, is a list over what the built-in variables like %w, %n, and %t etc mean.

---

### Post by ELMIT on 2015-10-06
Sorry, I am still fighting with this part;

I have two programs which should be started frequently. These two programs are in two screen sessions.

With cron I check for an existing text file (flag) to restart (one at a time):


```
#!/bin/bash
if [ -f /var/www/html/restartpgm1.txt ];  # check if a file is create
then
    echo "remove checkfile restartpgm1.txt."
    rm -f /var/www/html/restartpgm1.txt      # delete the check file so that it won't exist on next check
    screen -d "Pgm1"
fi

if [ -f /var/www/html/restartpgm.txt ];  # check if a file is create
then
    echo "checkfile restartpgm.txt exists."
    mv /var/www/html/restartpgm.txt /var/www/html/restartpgm1.txt      # move for next time second part above
    /home/ronald/bin/restartpgm.sh
fi
```


What I want:
If I touch /var/www/html/restartpgm.txt the cron program above should find the flag, starts the program and moves the flag file to the next part flag (restartpgm1.txt). 
At the second round, it should remove the restart flag (restartpgm1.txt) AND detach the screen session.

It works ONLY if I start the cron program from the command line and then the cron version will detach my screen session.

If cron alone starts, then the program ends, no screen session to detach in the second round.


I have tmux installed as well, but there I have even less knowledge how to solve it.

---

### Post by Lars Noodén on 2015-10-06
If you are running that script from within screen, it will detach because of this :  screen -d "Pgm1"

If you are running that script outside of screen, then it will do nothing unless there is a screen session somewhere named "Pgm1".  If there is a screen session with that name, it gets detached.  Otherwise, screen has nothing to work on.  

What do you want running in screen (or tmux)?

---

### Post by ELMIT on 2015-10-06
I cannot read your solution!

---

### Post by ELMIT on 2015-10-06
I think I missed to show you restartpgm.sh:

```
cd /home/ronald/
    screen -S "Pgm1" -X quit   # quit the "Pgm" screen
    screen -L -S "Pgm1" sh -c "./run.sh"   # -L results in screenlog.0

```

-----
touch restartpgm.txt

If I start the cron program in the command line, then above program will be started and the screen session is displayed, and so the second run of that program from cron will do all correct and detach the session.

If only cron starts the program, then it stops the running session (if one), and restarts the program quoted above and EXIT !!! So the next run of the cron program finds no session to detach.

It seems if I run it from cron, then   screen -L -S "Pgm1" sh -c "./run.sh"  is either not started or already finished before I can detach it.

---

### Post by ELMIT on 2015-10-07
It works now. Instead of 

screen -L -S "Pgm1" sh -c "./run.sh"   # -L results in screenlog.0

I use now:

screen -L -dmS "Pgm1" sh -c "./run.sh"   # -L results in screenlog.0

I am very sure I tried that before.

---

