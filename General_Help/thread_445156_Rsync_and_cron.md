---
title: "Rsync and cron"
date: 2007-05-15
forum: General Help
---

### Post by rock lobster on 2007-05-15
Hello all,
My problem is with Cron and Rsync. Separately they work together they dont its very odd. To give you an example: I can rysnc 2 directories and it will work fine, but if i take that same command and add it into crontab it wont run properly. I am trying to do a type of incremental back up only transferring new files to the other directory 

so my crontab looks something like this * * * * * /usr/bin/rsync -ab /fileserver/My\ Music /hdb/My\ Music >> /hdb/cron.log

(its not going to run every min thats just there for testing)

as you can see i made the output get kicked out to a log file so i can track the problem, the strange thing is i dont see anything about failure in the log the only entries i get are: 

building file list ... done
file has vanished: "/fileserver/My Music/Random Music"

sent 156798 bytes  received 42 bytes  104560.00 bytes/sec
total size is 17165417681  speedup is 109445.41
rsync warning: some files vanished before they could be transferred (code 24) at main.c(892) [sender=2.6.8]

But it never actually backs up the new files i add on the sender side. 

If i take that same command and put in the shell it works like a charm no problems..  Any idea guys? 

I hope that is a descriptive enough.

---

### Post by stylishpants on 2007-05-15
```
fhanson@fhanson:~/issp$ cat /etc/crontab
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
...

```

It looks like cron uses /bin/sh to run commands, whereas you are probably using /bin/bash, which is the default.

Type "sh" to run /bin/sh, and then try your rsync command again from that shell.

---

### Post by rock lobster on 2007-05-15
Yeah, no luck its not a problem to run it in the shell its more so a problem to run it in cron. Where it just doesnt want to mirror.. Could there be an issue with permissions? Because the folder im trying to backup is a mounted windows share.. 

But that still wouldnt make sense that i could do it manually but not set it as a cron job.. :confused:

---

### Post by stylishpants on 2007-05-15
I don't know what you mean by "no luck".  Did the command succeed when you ran it manually from a /bin/sh shell, or did it fail as expected?

I understand that it usually works when you run it in your normal shell, and the problem only shows up in crontab.  The point of trying to run it manually in /bin/sh is to see if it fails, indicating that the shell is the problem. 

If the command actually worked when you ran it from within /bin/sh, then I'm stumped.  I don't have any windows shares around to check against.

---

### Post by qpieus on 2007-05-15
Unfortunately I don't know why your rsync command is not working correctly from cron, but as an alternative you could put your rsync command into a script file and have cron run the script. That's how I have my backup set up and it works fine. I have not tried my rsync command entered directly in my crontab like you are trying though (it's too lengthy, so it was easier to put the code into a script).

---

### Post by rock lobster on 2007-05-15
Doing the Rsync command in sh doesnt work it does the same thing that it would in crontab, i see what you are saying now. So can i do to correct this?

---

### Post by rock lobster on 2007-05-15
> **qpieus said:**
> Unfortunately I don't know why your rsync command is not working correctly from cron, but as an alternative you could put your rsync command into a script file and have cron run the script. That's how I have my backup set up and it works fine. I have not tried my rsync command entered directly in my crontab like you are trying though (it's too lengthy, so it was easier to put the code into a script).

So i could just setup a bash script for my backups. hmm i didnt think of that. How would i go abouts doing that? i have never run a bash script before

---

### Post by qpieus on 2007-05-15
It's a piece of cake. First make a new text file and place it in a directory of your choosing. Call it backup.sh for purposes of this discussion. Open up the file in your favorite text editor and put this in the first line:```
 #!/bin/bash
``` That line indicates that this will be a bash script.
Next, put in your backup command in your text file. In your case it would be:```
rsync -ab /fileserver/My\ Music /hdb/My\ Music >> /hdb/cron.log

```
Save the file and make it executable.
```
chmod u+x /path/to/backup.sh
```
Then make your crontab look like this:```
* * * * * /path/to/backup.sh
```
putting in the appropriate times of course.
That should do it.

Here's my script for example:```
#!/bin/bash

# script for cron job to backup home directory

rsync -av --exclude=podcasts --exclude=.mozilla/firefox/r9lsjyw0.default/Cache --exclude=vmware --exclude=dvds --exclude=.thumbnails --exclude=.local/share/Trash --delete /home/username /mnt/sda3/rh_backup >> /mnt/sda3/$(date +%Y%m%d)_rsync.log
```

---

### Post by rock lobster on 2007-05-15
Wow i didnt thank it was that easy.. So its pretty much like writing a quick batch file.. Is there any syntax needed to tell the computer where the script ends? or does it just end of file?

---

### Post by qpieus on 2007-05-15
yep, it's easy for something simple like what we're talking about. People can make some pretty complex scripts though. I'm not one of those people!
I don't think there's any syntax needed to end the script. I don't have anything like that in my scripts and my pc hasn't choked on them. Technically, I think there is a way to end the script - I've seen scripts ending in "exit 0" for example. I don't bother with that though. Here's a link to a good online guide to bash scripting for your reading pleasure: [http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html]("http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html")

---

### Post by rock lobster on 2007-05-16
I haven't had a chance to read through that Scripting guide yet, but i keep getting the error " bin/sh: bad interpreter: No such file or directory" when i try to run the script.. what does that usually mean? :confused:

---

### Post by qpieus on 2007-05-16
Please post your script text and your crontab entry.

---

### Post by rock lobster on 2007-05-16
```
#!bin/sh

#script to sync music directories

rsync -abv /fileserver/My\ Music/ /hdb/My\ Music/ >> /hdb/backup.log

```

That is the script i put together. 

```
# m h  dom mon dow   command
#* * * * * /etc/backup.sh

```

That is the crontab file, it has been commented out right now because it doesnt run. and the *'s are just for testing purposes.

---

### Post by stylishpants on 2007-05-16
The first line is wrong.   It should read : 

    #!/bin/sh

You are missing the first slash.

---

### Post by rock lobster on 2007-05-16
> **stylishpants said:**
> The first line is wrong.   It should read : 

    #!/bin/sh

You are missing the first slash.

Thanks that did work but the script still isnt running properly and not transferring the files :confused:

---

### Post by stylishpants on 2007-05-16
Oh, of course it isn't working.

We already know that the problem is the /bin/sh shell.  It works fine in /bin/bash, it fails in /bin/sh.

So, if you set up your script to be run with /bin/sh, then the command will fail.

You have to set up your script to run with bash instead, or else experiment with running your command in sh until you figure out what's wrong.

---

### Post by qpieus on 2007-05-16
Make the first line in your script:```
#!/bin/bash
```
That will make the script run with bash instead of sh.

---

### Post by rhodry on 2007-05-16
> **qpieus said:**
> yep, it's easy for something simple like what we're talking about. People can make some pretty complex scripts though. I'm not one of those people!
I don't think there's any syntax needed to end the script. I don't have anything like that in my scripts and my pc hasn't choked on them. Technically, I think there is a way to end the script - I've seen scripts ending in "exit 0" for example. I don't bother with that though. Here's a link to a good online guide to bash scripting for your reading pleasure: [http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html]("http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html")
Just to advise on one really small detail that tricked me up on occasion when first writing scripts.

When you write the script in your preferred editor (in particular gedit), make sure you finish the file with a carriage return to a blank line. Do not end the file at the end of the last line of code.

You can do a Google search on "ubuntu bash scripting" and you will find a number of very good tutorials from beginner to expert. Such a powerful little tool.

Cheers,
Paul.

---

### Post by qpieus on 2007-05-16
Thanks for the tip  rhodry, I did not know that. I must have got lucky in the few scripts I've made.

---

