---
title: "Proper Usage of flock"
date: 2015-08-22
forum: General Help
---

### Post by terminator14 on 2015-08-22
I work for a satellite internet provider, and we have a main server that keeps all the info about all the current satellite dishes in a mysql database.
I have multiple scripts that all need to pull data from that database about those dishes.
When I made all those scripts query that server for whatever info they needed, it bogged down the server a lot, and they were pulling a lot of the same data from it.
To make things more efficient, I created a single script that pulls data from that server, and writes all that data to a text file on the local machine every minute. 
All the other scripts just read that text file on the local machine to get all their information.
This seems to work great, but the one problem I ran into is that sometimes, the other scripts read the file while the main script is in the middle of updating it, so they end up getting half-complete data.
I need to make sure that when the main script is writing to that file, the file is locked, so if any other scripts try to read it, they have to wait.

This is what I've come up with. I need to know if it makes sense (I've never used flock before - not sure if the way I think it works is actually the way it works) or if there's a better/cleaner or more efficient way to do it:

Main Script:
```

exec 200>Database               #Opens file descriptor 200 attached to the database textfile it will be writing to
flock -e 200                    #Sets an exclusive lock to it. If it's locked already, waits until it's not 
echo stuff >&200                #Writes to Database file
exec 200>&-                     #Closes Database file (file descriptor), which releases the lock. Only necessary if you don't want to wait until your script exits, which will automatically close it

```

All other scripts:
```

exec 200<Database               #Opens file descriptor 200 for reading. Note the reversed direction of '<' 
flock --timeout 40 -s 200 || exit 1
                                #Waits until there is no lock on the file (in our case, until Main Script is done writing)
                                #If it cannot get a lock in 40 seconds, the flock command exits with error code 1, which causes the 'exit 1' to kill the script
                                #If it does get a lock within 40 seconds, it sets a shared lock, also know as a 'read lock',
                                        which means other things that are trying to get a shared lock can also get one at the same time
TEST=$(while read -u 200 -r line; do echo $line; done)
                                #Reads entire file into a variable
                                        #At this point, you can close the fd if you want - the Main Script can't get an exclusive lock until all shared locks are closed
```

Does this make sense?
What happens if something tries to read the script after the Main Script has run "exec 200>Database" but before it has run the next line (flock ...)?
The exec line will remove the Database file's contents, but the file won't be locked yet. Is there a way to avoid this?

EDIT: I'm working in bash

---

### Post by jim_deadlock on 2015-08-22
You don't mention which language you're using, but in Perl I've found flock to be a bit erratic. What I do is when writing to the file I create a new empty lock file (for example if writing to myFile, create myFile.lock), then in all the other scripts wanting to read the data, I put "sleep 1 while (-e myFile.lock)" (wait while the lock file exists). Then when the writing script has finished it deletes myFile.lock so the others can proceed with the reading.

---

### Post by terminator14 on 2015-08-22
> **jim_deadlock said:**
> You don't mention which language you're using, but in Perl I've found flock to be a bit erratic. What I do is when writing to the file I create a new empty lock file (for example if writing to myFile, create myFile.lock), then in all the other scripts wanting to read the data, I put "sleep 1 while (-e myFile.lock)" (wait while the lock file exists). Then when the writing script has finished it deletes myFile.lock so the others can proceed with the reading.

I'm using bash.
Your way works. It might need a few additional lines to handle:

[LIST=1]
[*]Your script exiting unexpectedly
[LIST]
[*]You need a trap on SIGINT, EXIT, etc to catch that and remove the lock file. Easy enough.
[/LIST]
[*]Your system dying while a lock file is in place
[LIST]
[*]The original script should be okay with clearing a pre-existing lock file
[LIST][*]Since the lock files are meant for other scripts more than the main script (at least in my case), all it really needs to do is delete the lock files if it sees them either at the beginning, or just keep them there until it's done writing to the file and clear them.[/LIST]
[/LIST]
[*]Other scripts timing out if the lock file is in place for too long
[LIST]
[*]Easy enough with a simple
```

        for VAR in {1..30}
        do
                if [ ! -e $LOCKFILE ]
                then
                                break
                fi

                sleep 1
        done

        if [ -e $LOCKFILE ]
        then
                echo "Could not acquire lock in 30 seconds" >&2
                exit 1
        fi

```
[/LIST]
[/LIST]

Anything else I'm missing?
Any advantages to using flock over manually creating lock files, other than the fact that we need to deal with cleaning up lock files manually?

---

### Post by jim_deadlock on 2015-08-22
The writing script creates the lockfile first thing no matter what (overwrites if already existing). It  then does its thing with the writing, then deletes the lockfile last  thing.

As a failsafe you can set a maximum age for the lockfile within the reading scripts. The age of the lockfile is checked first thing - Perl uses the "stat" function for this if it's any help - and removed if it's over a certain age (assuming there's been an error and it was left behind). This also assumes that the reading scripts run much more often than the writer.

Or you could set a cron job to remove stale lockfiles.

Or instead of locking anything, the reading files could check whether the writing script is actually running (fork a system call to `ps`). I've never tried this but it's an option to consider.

I think flock is probably the official/proper way of doing it, but personally I've had a lot of trouble with it in the past and find lockfiles much easier to deal with. Just my opinion.

---

### Post by terminator14 on 2015-08-22
> **jim_deadlock said:**
> The writing script creates the lockfile first thing no matter what (overwrites if already existing). It  then does its thing with the writing, then deletes the lockfile last  thing.

As a failsafe you can set a maximum age for the lockfile within the reading scripts. The age of the lockfile is checked first thing - Perl uses the "stat" function for this if it's any help - and removed if it's over a certain age (assuming there's been an error and it was left behind). This also assumes that the reading scripts run much more often than the writer.

Or you could set a cron job to remove stale lockfiles.

Or instead of locking anything, the reading files could check whether the writing script is actually running (fork a system call to `ps`). I've never tried this but it's an option to consider.

I think flock is probably the official/proper way of doing it, but personally I've had a lot of trouble with it in the past and find lockfiles much easier to deal with. Just my opinion.

I can't think of anything that regular, manually created lock files can't handle for my situation, whereas the flock implementation I outlined above has a flaw, which I also mentioned.
I'm sure there's probably a way to get around the flaw in flock (since it's specifically designed to deal with lock files, I can't imagine that the flaw never occurred to anyone, or that it does a worse job than a regular, manually created lock file), but at this point, I think I'm going to go with the lock files. Thanks

---

### Post by sandyd on 2015-08-22
a) Write data to temporary file
b) Move temporary file to propper location.
c) If temporary file does exist, do not engage, pause 30s and try again

Sample import script
```

#!/bin/bash 

# Generate temp file
touch /tmp/databasefile

# Start import
....

# Move temp file
mv /tmp/databasefile /home/terminator14/databasefile

```

Sample run script
```

#!/bin/bash

# Make sure no other script is reading (crude).....
if [ ! -f /home/terminator14/run/script1 ]; then
    touch /home/terminator14/run/script1
    while [ -f /tmp/databasefile ]
    do
        sleep 10
    done
...
else
    exit 1;
fi
```
Unless you have extremely slow storage, it should copy in milliseconds.

Additional Detail:
If you want it to be even better without all this exiting, setup a mySQL Slave on each host.

---

