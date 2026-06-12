---
title: "rsync script works, but not as cronjob"
date: 2007-08-06
forum: General Help
---

### Post by jackn on 2007-08-06
I use an rsync script to mutually backup two boxes. When placed in a cronjob, however, the script does nothing.
I have studied previous posts on the forums and, unfortunately, was not able to find a solution.

Here are some observations:

The script run from terminal:
```
 :~$ files/bin/rsync_cronjob.sh
```
yields (lines snipped)
```
sent 11943 bytes  received 395930 bytes  30212.81 bytes/sec
total size is 2652756210  speedup is 6503.88

```

In addition, similar lines figure in a log file which the script is set up to report to:
```
2007/08/06 11:23:58 [17612] sent 11943 bytes  received 395930 bytes  30212.81 bytes/sec
2007/08/06 11:23:58 [17612] total size is 2652756210  speedup is 6503.88

```

In light of a comment made in a previous thread, I tested the script in an sh shell, and it ran properly, as in the bash shell above.

So, the script is fine.

In the crontab:
```
:~$ crontab -e
```
I have
```
0 11,18 * * * /home/jackn/files/bin/rsync_cronjob.sh
```

So, as the script runs fine from the command line, I expect to see some output into the log file at 11 and at 6pm. 
There is none, however.

In addition, when I run some other dummy job through cron (set to * * * * *), it runs fine.

Help? Thanks...

jackn

---

### Post by jackn on 2007-08-08
bump

---

### Post by ebash on 2007-08-08
There could be many reasons why a script works fine from the command line and not as a cron.
Most of the times the problems are due to the environment variables. Cron jobs run with a very limited environment.

To troubleshoot your script from the command line do the following. Create a dumb cron that prints the environment:

```
* * * * * env | sort > /tmp/cron-env.txt
```

Wait for the cron to run and disable it. Now the file /tmp/cron-env.txt should have the environment variables that are used by a cronjob. Start a new shell and delete all your environment variables, keep in mind that this will be very nasty for that shell, if something doesn't work close that shell and start a new one.

```
for var in `env | perl -lne '($v) = split /=/; print $v'` ; do unset $var ; done
```

Check that all environment variables are deleted by calling:

```
/usr/bin/env
```

You should have one line of input

```
_=/usr/bin/env
```

Now load the environment used by the cron system:

```

perl -lne '($n,$v) = split /=/, $_, 2; print qq{export $n="$v"}' /tmp/cron-env.txt > /tmp/cron-env.sh
source /tmp/cron-env.sh

```

That's it you should now have in your shell the same environment as in the crons. Try to execute your script and check if it works. If it doesn't make the right changes until it accomplish its task properly and try it as a real cronjob.

To repeat this commands for a future usage you can create a script named set-cron-env.sh that will include the following lines:

```

# Delete the current environment
for var in `env | perl -lne '($v) = split /=/; print $v'` ; do 
  unset $var ; 
done

# Load the environment of the crons
echo "REPLACE THIS LINE by the contents of /tmp/cron-env.sh"


```

Load that script through the command 'source':
```
source set-cron-env.sh
```

---

### Post by jackn on 2007-08-08
First, the rsync crontab is working just fine.
It turns out I simply had the wrong path in the crontab, so of course it didn't run...

What a stupid mistake.

I'm sorry about this.

I was very glad to see your post, ebash.
I knew I would learn a lot in the process of putting the advice into practice.
Which I did.

So, I created a cron-like environment by following the instructions, namely copying cron's environment into a shell stripped of the usual user environment.

A little note: I had to run 
```
/usr/bin/perl 
```
and not just 
```
perl
```
as the shell had no PATH.

When done, just to make sure, I printed the file holding the cron env:
```

less /tmp/cron-env.sh 
WARNING: terminal is not fully functional
export HOME="/home/jackn"RETURN)
export LANG="en_US.UTF-8"
export LOGNAME="jackn"
export PATH="/usr/bin:/bin"
export PWD="/home/jackn"
export SHELL="/bin/sh"
/tmp/cron-env.sh (END)
``` 

It was,  of course, the same as what I got when running /usr/bin/env:

SHELL=/bin/sh
PATH=/usr/bin:/bin
PWD=/home/jackn
LANG=en_US.UTF-8
HOME=/home/jackn
LOGNAME=jackn
_=/usr/bin/env

Although I was now  in a cron-like environment, when running the rsync script from the command line, I still had no trouble:
```
sent 7011 bytes  received 412277 bytes  55905.07 bytes/sec
total size is 2671132709  speedup is 6370.64
```

In other words, what was stopping the script from running was not the lack of the usual user variables.

I also wanted to test the idea that user env variables are missing in cron by adding them to the script. So, I created a shell stripped of all env variables (verified by running /usr/bin/env). 
I was about to add a normal shell's /usr/bin/env output to the script in order to give this stripped shell the usual user environment when running the script. 
But first I ran the script in this stripped, variable-less shell, to have a control for the run with variables added.
And, what do you know, the script ran with no env variables at all (all paths in it are absolute).


So, this was very useful as one possibility was ruled out, and I had learnt plenty, not to mention future uses of this procedure. But I still didn't know why the script wouldn't run.

I guess having ruled out the most likely substantive possibility, I was finally able to note that in the crontab  the path to the script skipped one of the directories.
I uisually try to avoid such mistakes by copying paths from TAB-completed command lines. What happened is that I had added an intermediate directory after setting up the cronjob without taking care of the path in crontab. 

I really appreciate the time  you put into this, ebash, and the detailed and precise instructions you've provided. 
I'm very glad I went through this, as I'm here to learn more than for any other reason. And I hope you won't mind too much.

Again, apologies. And thank you.

jackn

---

### Post by ebash on 2007-08-09
I'm glad to see that you fixed the problem. I know how annoying debugging cronjobs can be, specially if we are waiting for the cron to start in order to see the problem.

In regards to your comments, you are right that running the commands from the cronified environments will not work since the PATH variable is not set properly. I failed to precise that I was running most of the commands from a working shell and limited the cronified shell to clear the environment and to source the main file.

The same logic can be used to debug CGI scripts that fail to run from a web server but work fine at the command line. The idea is to create a CGI that will print the environment, to become the web server's user and to clear the environment variable.

I hope that this post can help other people facing a similar problem.

Cheers.

---

