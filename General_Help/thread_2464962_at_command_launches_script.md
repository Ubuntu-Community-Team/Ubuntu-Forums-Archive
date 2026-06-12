---
title: "at command launches script"
date: 2021-07-17
forum: General Help
---

### Post by Langstracht on 2021-07-17
I want to use "at" to launch an .sh file.

For example ```
at now + 2 hours a.sh
```.

I have used the script in question forever so there is no doubt that it works.

I have tried a variety of commands and searched on the 'net for "at" help ... and have gotten nowhere.

Can anyone help?

TIA

---

### Post by TheFu on 2021-07-17
[https://blog.jdpfu.com/2011/03/04/schedule-jobs-with-at](https://blog.jdpfu.com/2011/03/04/schedule-jobs-with-at) shows how.  

You cannot trust the PATH to find a.sh.  Specify the location exactly. That can be either with an absolute path to the file or with a relative path. Your choice.

```
at -f ./a.sh  now + 2 hours 
at -f ~/bin/a.sh  now + 2 hours 
at -f /usr/local/bin/a.sh  now + 2 hours
```

If you must trust the PATH, then you'll need to use the stdin command method outlined in the link.

---

### Post by Langstracht on 2021-07-17
Thanks for your reply - much appreciate it.

Based on what you've said I think perhaps my problem is with the path.

Can you tell me where "at"  thinks it's at, so to speak. I've tried a whole bunch (although I guess obviously not all!) of paths and none of them has worked.

---

### Post by TheFu on 2021-07-17
well, I can't  guess where a.sh is.  It is your system, your file, not mine. 

If you type **ls /path/to/file/a.sh** and that is correct, that is the answer you seek.

15 yrs using linux? Or Windows? Shouldn't matter. The *path to a file* works the same on both.

---

### Post by The Cog on 2021-07-17
If you type ```
 which a.sh
```it will tell you the full path to it.

---

### Post by Langstracht on 2021-07-17
Thanks again for dealing with this.

I realize that you don't know where the file is.  But I didn't think that was the issue.

The situation is:

I have been "commanding" "at" from the folder that the file is in.  And it doesn't work!

So, I thought, if I knew where "at" is looking for the file - home, bin, usr, wherever - then I could give supply a path to the file.  OR move the file to where "at" is looking for it.

The other thing that I am totally baffled by is that, if I type "sh" in the folder holding the file (sh being required by at apparently), the path to that folder disappears and is replaced by "$".  Is this perhaps contributing to the problem and I should being invoking "at" from the $ prompt?  Presumably together with the appropriate path.

---

### Post by Langstracht on 2021-07-17
Thanks for pitching in The Cog - alas you're going to have to hold my hand a bit more.

From where am I to enter which a.sh?

Obviously not from the folder containing a.sh.  But where?

---

### Post by The Cog on 2021-07-17
So can you name the folder where a.sh is located? I guess you can since you say you have been "commanding" "at" from the folder that the file is in.
When you say "commanding", does this mean you are openg a terminal (with a command prompt) and typing "a.sh"? That won't work. If the folder that a.ah is located is not in the list of folders where the command prompt will look for commands you type, then it won't find it. You need to type "./a.sh", where the leading "./" means "here in my current working directory". The command prompt will (by default) open and save files in your current working directory, but won't run executable files there, hence needing to specify ./a.sh if you want to execute it.

Assuming a.sh is located in /home/langstracht/myProject, then the full path to it is /home/langstracht/myProject/a.sh, and this is what you should put in your scripts.

If this still doesn't help, then please post the full names instead of leaving us guessing and using long descriptions just because we don't know the facts.

---

### Post by Holger_Gehrke on 2021-07-17
'which' searches for executables along $PATH. PATH is a variable that holds a colon-separated list of directories. The shell **only** searches for executables in those directories, so 'which' will tell you which file is actually executed if you enter a command. Note that '.' aka the current working directory is **not** in PATH for security reasons (imagine unpacking a tar that holds a script named 'ls' and having '.' in the PATH ...). If the directory your script is in is not in $PATH, 'which' will not find it. 'locate' will find it, assuming that the file has existed long enough that the regularly scheduled update of locate's database has been run during the lifetime of the file. You can of course execute any executable file if you give the shell a full path and name for the file, so './executableFile' will execute executableFile in the current working directory and '$HOME/scripts/argelbargel' will work if there's an executable of that unlikely name in a directory named scripts in your HOME.

So you can call 'which a.sh' in the shell from any directory, but you will only get an answer if 'a.sh' is in a directory in PATH. 'locate a.sh' will find the file even if it isn't in PATH.

Holger

---

### Post by Langstracht on 2021-07-17
Sorry to all.  This has become far more complicated and obtuse than I intended.  And I must suppose I have not been clear.  For which I apologize.

But, I thought, to repeat:

a.sh is in folder Desktop/Scripts

If I go to that folder and enter bash a.sh (or sh a.sh for that matter!) the script performs just fine.

Still in that folder, if I then enter an "at" command in ANY of it's forms, it does not work.  Presumably because "at" can't find the file.

So I can move the file to where it can find it.  OR somehow find the path that it needs ...

---

### Post by TheFu on 2021-07-17
~/Desktop/Scripts/a.sh is the answer you seek.
or 
/home/$USER/Desktop/Scripts/a.sh.

Without any path data as part of the filename, it is going to look in the $PATH.  ~/Desktop/ isn't (and shouldn't!!!!) be in your PATH.


So, 

```
at    -f     ~/Desktop/Scripts/a.sh  now + 2 hours
```

---

### Post by Doug S on 2021-07-17
I see TheFu answered, but I'll post anyhow, since I was working on an answer:

I made an example script called "example":

```
doug@s19:~/tmp$ cat example
#!/bin/dash

# example Smythies 2021.07.17
#       see https://ubuntuforums.org/showthread.php?t=2464962
#

echo "example ran:" >>example.txt
date >> example.txt
```

and for finding the full path I did:

```
doug@s19:~/tmp$ find $PWD -name example
/home/doug/tmp/example
```

and so I ran this:

```
doug@s19:~/tmp$ at now + 1 minute -f /home/doug/tmp/example
warning: commands will be executed using /bin/sh
job 3 at Sat Jul 17 12:52:00 2021
```

and got this:

```
doug@s19:~/tmp$ cat example.txt
example ran:
Sat 17 Jul 2021 12:03:00 PM PDT
example ran:
Sat 17 Jul 2021 12:05:00 PM PDT
example ran:
Sat 17 Jul 2021 12:52:00 PM PDT
```Where you see I started this before lunch and finish now after.

---

### Post by Langstracht on 2021-07-17
So I copied and entered the code 

```
at    -f     ~/Desktop/Scripts/a.sh  now + 2 hours
```

(changing the hours to minutes)

provided by TheFu into Desktop/Scripts.

And ... it did not work!

---

### Post by TheFu on 2021-07-17
#!/bin/bash -x

output?


What does :  **ls -l  ~/Desktop/Scripts/a.sh** show?

---

### Post by Langstracht on 2021-07-17
```
-rwxrwxr-x 1 allan allan 595 Jul 15 08:55 /home/allan/Desktop/Scripts/a.sh
```

---

### Post by Doug S on 2021-07-17
> **TheFu said:**
> #!/bin/bash -x

output?


What does :  **ls -l  ~/Desktop/Scripts/a.sh** show?+1. we need better information than just "And ... it did not work!"

EDIT: here is mine, showing it is executable by user me:```
doug@s19:~/tmp$ ls -l example
-rwxrw-r-- 1 doug doug 156 Jul 17 11:57 example
```

EDIT: I see you posted while I was typing this.

---

### Post by Langstracht on 2021-07-17
Doug S, I am so sorry but I have no idea what better information I can give you.

I ran "at".

It appeared in the atq queue.

It ran at the appropriate time - disappearing from the atq queue.

There was no output.  For what it's worth the web pages that it was supposed to open, did not.

If you would like to explain how I can get you the better information that you are looking for that would be very helpful ...

---

### Post by Doug S on 2021-07-17
> **Langstracht said:**
> Doug S, I am so sorry but I have no idea what better information I can give you.You provided a wealth of information via this very reply.

> **Langstracht said:**
> I ran "at".

It appeared in the atq queue.

It ran at the appropriate time - disappearing from the atq queue.

There was no output.  For what it's worth the web pages that it was supposed to open, did not.

If you would like to explain how I can get you the better information that you are looking for that would be very helpful ...It is a detached process, so no its output would not appear on your terminal.
I'll modify my example:

```
doug@s19:~/tmp$ cat example
#!/bin/dash

# example Smythies 2021.07.17
#       see https://ubuntuforums.org/showthread.php?t=2464962
#

echo "example ran:" >>example.txt
date >> example.txt
echo "example ran: this goes to console, but does it?"
```and run it manually:

```
doug@s19:~/tmp$ ./example
example ran: this goes to console, but does it?
```
but that echo to terminal line will not appear via the "at" method:

```
doug@s19:~/tmp$ at now + 1 minute -f ~/tmp/example
warning: commands will be executed using /bin/sh
job 7 at Sat Jul 17 14:04:00 2021
doug@s19:~/tmp$ atq
7       Sat Jul 17 14:04:00 2021 a doug
doug@s19:~/tmp$ atq

doug@s19:~/tmp$ cat example.txt
example ran:
Sat 17 Jul 2021 12:03:00 PM PDT
example ran:
Sat 17 Jul 2021 12:05:00 PM PDT
example ran:
Sat 17 Jul 2021 12:52:00 PM PDT
example ran:
Sat 17 Jul 2021 01:27:00 PM PDT
example ran:
Sat 17 Jul 2021 01:28:00 PM PDT
example ran:
Sat 17 Jul 2021 01:59:00 PM PDT
example ran:
Sat 17 Jul 2021 02:02:31 PM PDT
example ran:
Sat 17 Jul 2021 02:04:00 PM PDT
```

---

### Post by Langstracht on 2021-07-17
So Doug S, are you saying that "at" is simply not capable of doing what I want - running an ".sh" script which opens web pages?

If that is not what you are saying then, sorry, but I have no idea what to do with your response.

---

### Post by TheFu on 2021-07-17
**at** sends all output to the locally installed/setup MTA.  Then you would use a mail program to see what happened.

But ... if you are trying to control a GUI program via **cron** or **at**, don't.  They don't tie into an X/Session or Wayland.  If it does work, count yourself lucky. cron and at are meant to work for non-interactive purposes, when no users are logged into the system. If you are trying to run something to popup anything in a GUI, then I think you want a different tool.  Look at **alarm-clock-applet** instead.

I use **at** all the time - to launch programs to download stuff from specific locations, at specific times, for specific durations.  There are 4 jobs scheduled for today, right now, with 1 of them running currently according to atq.

I asked for you to add a '-x' option to your bash script, run it, and post the output.  Did you miss that?

---

### Post by Langstracht on 2021-07-18
Yes TheFu, I did miss that.  Sorry.

So ... I changed 

```
#!/bin/sh
```

to

```
#!/bin/bash -x
```

in a.sh.

Alas with the same result.

I think I am prepared to give up.  I've wasted too much of my time on this as well as the time of a number of others.

I find it just a bit incredible that getting a script to be triggered by at can be such a problem ...

---

### Post by TheFu on 2021-07-18
>  I asked for you to add a '-x' option to your bash script, _run it_, and _post the output_. Did you miss that? 

Dude, if you don't post the script and the output, we can't help.  -x is a troubleshooting technique, not a "fix it" option.

If you are trying to have the script do anything with a GUI, forgetaboutit.  cron (and at) aren't designed for that purpose.  If you are 1000 miles away from the computer, not logged in, but the computer is on, will your script do something useful?  

For example, I use 'at' to record TV shows from a network-based TV tuner.  If the tuner is powered on and the computer is powered on, then the recordings happen. I don't need to be logged in.  The files are recorded to /TV/Recordings/ with the show name, channel, and a timestamp.ts. Multiple shows can be recorded concurrently.  There is no interaction with the GUI.  The output from 'at' gets emailed to my email server.

Last night it recorded...
```
INFO: Output file will be: "/TV/Recordings/Consuelo_Mack_WealthTrack-2021-07-08-232800-8.1.ts"
--2021-07-08 23:28:00--  http://hdhr5:5004/auto/v8.1
Resolving hdhr5 (hdhr5)... 172.22.22.25
Connecting to hdhr5 (hdhr5)|172.22.22.25|:5004... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [video/mpeg]
Saving to: ‘/TV/Recordings/Consuelo_Mack_WealthTrack-2021-07-08-232800-8.1.ts’

     0K .......... .......... .......... .......... ..........  168K
    50K .......... .......... .......... .......... ..........  194K
   100K .......... .......... .......... .......... ..........  210K
   150K .......... .......... .......... .......... ..........  194K
   200K .......... .......... .......... .......... ..........  210K
....
2263200K .......... .......... .......... .......... ..........  852K
2263250K .......... .......... .......... .......... ..........  842K
2263300K .......... .......... .......... .......... ..........  842K
2263350K .......... .......... .......... .......... ..........  837K
2263400K .......... .......... .......... .......... ..........  844K
2263450K .......... .......... .......... .......... ..........  837K
2263500K .......... .......... .......... .......... ..........  831K
ERROR: 0
```
That email message and the recorded video file are the only results.  If I was logged into the system, the GUI wouldn't show anything, which is good, because it cannot.  'at' doesn't interact with any GUI.

---

### Post by Langstracht on 2021-07-18
Unless I missed it (again) I don't think anyone expressed any desire to see the apparently offending script.

That said, here it is:

```
#!/bin/bash -x
#----------------------------------------------

/usr/bin/firefox  https://www.bbc.co.uk/schedules/p00fzl7l https://www.bbc.co.uk/schedules/p00fzl7j https://www.thingiverse.com/search?q=tools&type=things&sort=newest&page=1 
```

As I indicated on multiple occasions it performs just fine with bash and with sh.

Sorry but I have no idea where this GUI thing came from.  It's a text file and launched with the command line.

---

### Post by ActionParsnip on 2021-07-18
You must use the absolute path, starting from "/". If it is on your desktop (I don't suggest you store scripts there. It's messy) then you will need to specify the folders all the way to your desktop. Eg

/home/yourusername/Desktop/a.sh

This is an absolute path. The opposite is a relative path and is relative to your location that the shell is in. You can see this by running

```

pwd

``` 

The at scheduler doesn't have this path, nor your BASH variables.

---

### Post by TheFu on 2021-07-18
Firefox is a GUI program.  It won't work unless a user is logged in with an GUI session active, and the program is being run from inside that GUI session.  
**[COLOR="#FF0000"]cron and at aren't designed to work with GUI programs.[/COLOR]**  They don't know what the current GUI session is.  They don't know how to connect to the current GUI session.  If you can use a mouse/trackpad, that is a GUI session.

When you open a terminal inside a GUI session (Wayland or X/Windows), then that terminal inherits all the required settings for the current session.  cron and at do not.  I'm sorry. I don't know how to be any clearer.

Take a look at **alarm-clock-applet**.  This is a GUI tool where timers can be setup either for a specific time (9pm) or for a specific delay (2 hrs). A custom command can be put into it.  The schedule is recalled after a reboot for any active timers and the times continue working.

Also, you may want to use the xdg-open command instead of firefox.  I have a script like this:
```
xdg-open http://pihole.lan/admin/index.php
xdg-open https://darksky.net/forecast/
xdg-open https://wb.lan/login
sleep 4
xdg-open https://nc.lan/nextcloud/login
xdg-open http://istar.lan:32400/web/index.html#

```
which will open tabs in an already running browser.  Nothing wrong with using firefox either. Just providing an option.

And the last URL has an '&' inside it. That is a special character in all shells and needs to be quoted or escaped so it gets passed through as an argument to the program.  Need to [COLOR="#FF0000"]'[/COLOR]https://www.thingiverse.com/search?q=tools&type=things&sort=newest&page=1[COLOR="#FF0000"]'[/COLOR] - single-quote it.
```
/usr/bin/firefox \ 
   https://www.bbc.co.uk/schedules/p00fzl7l \
   https://www.bbc.co.uk/schedules/p00fzl7j \
   'https://www.thingiverse.com/search?q=tools&type=things&sort=newest&page=1'
```
alarm-clock-applet will work.

If you are interested in recording audio from websites, there are non-GUI methods to do that. If the URL for the feed can be determined, **wget** can often be used with "**timeout**" to record to a file, but for a limited time.  No GUI needed.

---

### Post by Langstracht on 2021-07-18
My confusion continues.

ActionParsnip seems to be suggesting that, if I EVER get the path right, this should work - i.e. "at" runs a script and the script "executes.

You TheFu seems to be saying this will NEVER work.

I still fail to understand why a typed in "sh" or "bash" on the command line works just fine.  And the same commands typed in to an "at"command do/will not.

Call me stoopid!

---

### Post by TheFu on 2021-07-18
If you tried the exact at command I provided in post #11 and that didn't work, then it is some other issue.  Finally in post #23, we see that you are trying to run a GUI program.  at and cron aren't designed to work with GUI programs.  The environment is NOT the same.

Have you ever used ssh to remote into another computer?  There's no GUI.  There's no GUI-session. You can't run any GUI programs on that remote system without doing something extra to make it work.

If you use X/Windows, there are some terrible work-arounds, but I'm not gonna get into those because they are hacks of hacks and don't always work.  I doubt Wayland will allow it at all. Wayland has more security.  

Use alarm-clock-applet. It will work for this purpose.  Have you tried it?

---

### Post by Langstracht on 2021-07-18
i believe I have tried every suggestion offered in this thread.  To no avail.

And just to perhaps clarify, firefox is NOT running when I bash, or sh, the script.  It opens firefox, successfully, all by itself.  As you might find should you deign to do so.

---

### Post by Langstracht on 2021-07-18
I guess I left a couple of loose ends ...

I have never used ssh to remote into another computer?

I do not use X/Windows.

I have not tried the alarm-clock-applet?

As I said earlier I have pretty much given up on this and somewhat regret starting the thread in the first place.

---

### Post by The Cog on 2021-07-18
You could try telling firefox which display you want it to use when it launches, like this:```
#!/bin/bash -x
#----------------------------------------------
export DISPLAY=:0.0
/usr/bin/firefox  https://www.bbc.co.uk/schedules/p00fzl7l https://www.bbc.co.uk/schedules/p00fzl7j https://www.thingiverse.com/search?q=tools&type=things&sort=newest&page=1
```
but it will only work if you are logged in and running a graphical interface at the time it runs. 
If nobody is logged in, or if some other user is logged in then the at command will not be able to open a graphical application on that display.

Like The FU tells you, at is not intended for launcing graphical apps. It is intended for running unattended programs that run in the background.

---

### Post by Langstracht on 2021-07-18
I really need to stop doing this.  But:

This 
```

at> export DISPLAY=:0 && firefox https://www.ted.com/
```

which DOES open your GUI, works just fine.

And yet, the command which "should" _open a script_ WHICH SHOULD open firefox does not.

Sorry but my pea brain is unable to process that.

---

### Post by TheFu on 2021-07-18
I highly doubt that you aren't/haven't used X/Windows.  That has been the default display server for almost every release of Ubuntu since the beginning. If you have any window displayed at all or even a login GUI and mouse, you've been using X/Windows all this time.

One more time .... **alarm-clock-applet** will do what you seek.  Good luck.

---

