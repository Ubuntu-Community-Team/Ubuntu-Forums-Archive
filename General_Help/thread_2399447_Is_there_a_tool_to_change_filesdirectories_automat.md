---
title: "Is there a tool to change files/directories automatically?"
date: 2018-08-25
forum: General Help
---

### Post by cyplex on 2018-08-25
I would like a tool that can run in the background (like a service) on boot and when there is a file that would appear in a directory (or a set of directories) and their sub-directories, then the tool would perform certain actions depending on the filename. For example:


[LIST]
[*]If a file called "ticket-00011" appears in /var/tmp/tickets/ directory then I would want the tool to perform an action such as run a specific script, passing the filename of the "ticket" to the script.
[/LIST]

[LIST]
[*]If it sees /home/myuser/myfiles-BACKUP.tgz it reads the time/date of when the file was created and if the file is so many days (or hours) old, remove it.
[/LIST]

Is there a tool that can do these things?

I wanted to see if anyone knows if something like this already exists before I have to spend some time to create such a program/service.

---

### Post by Holger_Gehrke on 2018-08-25
There's an API in the kernel for just this purpose: inotify.  There are several programs that use inotify to monitor the file system. One is called incron. It tries to be like cron but with events in the file system as triggers for actions instead of time. It works as advertised, although the author considered it 'alpha' and hasn't updated it in several years. And there is the package inotify-tools that has inotifywait, meant for use in a shell script to wait for an event in the filesystem. Both are in the repositories. Even if neither is exactly what you need, they should at least give you an idea on how to solve the problem.

Holger

---

### Post by #&amp;thj^% on 2018-08-25
+1 for inotify, 
```

inotifywait -m /path -e create -e moved_to |
    while read path action file; do
        echo "The file '$file' appeared in directory '$path' via '$action'"
        # do something with the file
    done

```
In Ubuntu inotifywait is provided by the inotify-tools package.

---

### Post by cyplex on 2018-08-25
Thank you for your reply.

I can't keep a shell script running just to see a change in the file system. That's the whole point of needing a daemon/service so I don't have to use a script to monitor the files. I will take a closer look at inotify but I don't know if it'll suit my purpose. The service has to be configurable as to what directories to watch and certain files require different actions.

I'll look into inotify but this thread is still open because I really would like to know if there's any other ideas out there. If not, then looks like I'll have to create a service.

UPDATE: I think inotifywatch from inotify-tools will work. If I have to use a script as suggested, I could probably run it via init.d.

---

### Post by SeijiSensei on 2018-08-25
Another option is run a script from cron that checks the directory once each minute and acts accordingly.  Add a line to /etc/crontab like
```
1 * * * * root /path/to/your/script
```

Not as immediate as inotify, but for some cases checking once a minute is sufficient.

---

### Post by cyplex on 2018-08-25
SeijiSensei Nice option for a low-use system. But this is a high-use server with a lot of files/directories to monitor. And a lot of cron job scripts already running. Would that add to or be a strain on the server? I'm talking hundreds of directories need monitoring.

---

### Post by SagaciousKJB on 2018-08-25
Unless you're expecting to see hundreds (perhaps even thousands) of modifications to those directories per minute, then the script to check for modifications itself shouldn't use much resources at all, and as a cron job it would probably be less since cron runs as its own daemon and would only run your script once every minute.  How much load that is presented on your system is going to be dependent on how many system calls the checking script generates, which would be dependent on how many events you expect to be monitored.  Excluding whatever operation you plan to take on those files, then you should be able to monitor the directory with a shell script without virtually any load.

To function as a daemon, that loop above needs to be nested inside of a larger infinite loop so that once inotifywait runs, and the while loop processes its output, the script doesn't just close and inotifywait launches again watching for changes.  Then you can just launch that script containing the nested loop inside the infinite loop as a forked process for it to run as a daemon, and use 'kill' along with its PID to shut it down.  As long as you run kill with -TERM, it will send the terminate signal to all its children PID ( inotifywait ) and exit gracefully.

Something like this...

```
#!/bin/bash

while : ; do 
        inotifywait -m /path -e create -e moved_to |
            while read path action file; do
                echo "The file '$file' appeared in directory '$path' via '$action'"
                # do something with the file
            done
done

```

Are you on a version of Ubuntu more recent than 14.04?  Because 16.04 and beyond use systemd instead of the sysvinit style scripts.  In any case, just learn how to launch a process forked into the background with whatever startup manager you're using.  I believe it's as simple as affixing '&' on the line you execute your script from with sysvinit and upstart, but with systemd I think it's something funky like "ExecForked".


I never realized inotifywait existed, I did this once before using an entire shell script with 'if' conditionals and using the test built-in to check for new files.  I'm sure inotifywait does it more gracefully than it can be done with shell scripts.

---

### Post by cyplex on 2018-08-25
Ok, I am not sure but I think I follow you. I'm concerned because I'm running a web server with several domains and lots of files. I'm using Ubuntu 18.04 (but also have a 14.04 I want to test on at least until April next year when I'll be retiring that server). Both are LTS.

---

### Post by SagaciousKJB on 2018-08-25
> **cyplex said:**
> Ok, I am not sure but I think I follow you. I'm concerned because I'm running a web server with several domains and lots of files. I'm using Ubuntu 18.04 (but also have a 14.04 I want to test on at least until April next year when I'll be retiring that server). Both are LTS.

Okay so on 14.04 it's still using the sysvinit scripts so you could make an init.d script to launch it very easily.  Save the script quoted above into a file like /usr/local/bin/dirwatchdaemon and chmod a+x it.

Then make a script in /etc/init.d/directorywatcher (or name it whatever you'd like) like so...
```

#!/bin/bash

case $1 in
start)
;;
dirwatchdaemon &
stop)
kill -TERM $(pidof dirwatchdaemon)
;;
status)
pidof dirwatchdaemon
*)
echo "Usage: start stop or status"
;;
esac

```

...you know the init.d scripts you're familiar with. Then run 'update-rc.d defaults' and it will create the init.d scripts to start and stop it.

With something so simple I also wonder if it couldn't just be launched from /etc/rc.local.  The important part is the '&' to fork it into the background.  That would be exceedingly simple, just add...

```
dirwatchdaemon&
``` to /etc/rc.local

Once you upgrade to 18.04 however, they switched over to systemd, so no longer use init.d scripts and rc.local no longer works.  Creating the equivalent systemd files would only require a glance at the documentation, I only demonstrated it with the init.d style to make it really clear what I meant.  However, you can also enable rc.local as a process with systemd, so it could go back to being that simple and just running the systemctl command to enable rc.local

In your position, I would get it working with /etc/rc.local now so that when you upgrade to 18.04 you only have to enable that as a system service, and that can allow you to keep functionality while you get familiar with the new systemd way of doing things.

---

### Post by cyplex on 2018-08-26
I want to actually forget about 14.04 (come to think of it, I shouldn't have really mentioned it). I want to concentrate on 18.04 and systemd. What documentation should I read? Usually docs are too confusing and I never usually get anywhere. I learn easier by example code that can be run successfully.

---

### Post by SagaciousKJB on 2018-08-26
> **cyplex said:**
> I want to actually forget about 14.04 (come to think of it, I shouldn't have really mentioned it). I want to concentrate on 18.04 and systemd. What documentation should I read? Usually docs are too confusing and I never usually get anywhere. I learn easier by example code that can be run successfully.

I personally haven't messed with systemd very much either, but I have cobbled together a few scripts from sources online.

I'd take a look at this link

[https://wiki.ubuntu.com/SystemdForUpstartUsers](https://wiki.ubuntu.com/SystemdForUpstartUsers)

And the first answer to this one which is very thorough.

[https://askubuntu.com/questions/919054/how-do-i-run-a-single-command-at-startup-using-systemd](https://askubuntu.com/questions/919054/how-do-i-run-a-single-command-at-startup-using-systemd)

For the above example I'd expect you'd end up creating a configuration looking pretty much akin to this...

```
[Unit]
Description=Directory watch daemon

[Service]
Type=forking
ExecStart=/usr/local/bin/dirwatchdaemon.sh &

[Install]
WantedBy=multi-user.target
```

Of course I can't gurantee that would work.  "Type=forking" tells systemd that it should be expecting a process that will call "fork()", which is what you need for a shell script running in the background.  Meanwhile "WantedBy=multi-user.target" is equivalent to running in runlevel 3 in a non-gui environment. 

Obviously you'll have to fine-tune the configuration, but that askubuntu link provides directions on how to enable it as a service and get it to start at boot.

---

