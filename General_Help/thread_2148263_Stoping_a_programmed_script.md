---
title: "Stoping a programmed script"
date: 2013-05-24
forum: General Help
---

### Post by Bojack5 on 2013-05-24
Hi there I'm new on this forum and found this amazing! 
I have a problem on a server I am configuring, 
I created a script and set /etc/crontab to run it always by filling it with *'s
this is the script

#! /bin/bash

MIN=$(date +%M)

let b=$MIN%5  

echo $b 

if [ $b == 0 ]

then

bash /home/bojack/scripts/dropbox_lunes.sh

fi

so the script runs every 5 minutes and makes a copy of some files to the dropbox folder

"bash /home/bojack/scripts/dropbox_lunes.sh"

the problem is that another person (with no knowledge at all of linux) updates the databases 

and theres a conflict because my script is using the files, is there a way of making a script to stop JUST THAT COMMAND 

on the /etc/crontab for about half an hour ?  is it possible to run this script on a windows computer on the same network?

tx in advance

---

### Post by pqwoerituytrueiwoq on 2013-05-24
so you have 
[FONT=courier new]*/5 * * * * /path/to/script[/FONT]
in your crontab
script contains
```
#!/bin/bash
MIN=$(date +%M)
let b=$MIN%5  
echo $b 
if [ $b == 0 ]; then
   bash /home/bojack/scripts/dropbox_lunes.sh
fi
```
and you want it to not run during a set time?
you could add something like this to the script
```
time=$(date +%H:%M)
if [ ${time:0:2} -eq 12 ] && [ ${time:3} -lt 31 ];then
   exit
fi
```
that would make the script exit if the time is between 12:00 and 12:30 (middle of the day)
edit: that includes 12:00 and 12:30

---

### Post by Bojack5 on 2013-05-25
thank you very much for your answer, is there a way to make a script so that when you run the script it stops for the next half hour? and if so is there a way to run it from a windows computer?

---

### Post by Impavidus on 2013-05-26
Create a script that touches a file:```
touch $HOME/.blockscript
```In fact, a simple alias would do. The file .blockscript has no contents. We are only interested in it's modification timestamp.

Then add some code to the script running every 5 minutes:
```

#Get the current time in seconds since the epoch
elapsedtime=$(date +%s)

#Get the time at which the file was touched in seconds since the epoch
touched=$(stat --format=%X $HOME/.blockscript)

#Calculate the difference
(( elapsedtime -= $touched ))

#If difference is less than 1800 seconds, exit
if [ $elapsedtime -lt 1800 ]; then
    exit
fi

```
This relies on the file access time stored in the Linux file system. I'm not sure how this works from a windows system, but the general idea may be adaptable.

---

### Post by Bojack5 on 2013-05-28
> **Impavidus said:**
> Create a script that touches a file:```
touch $HOME/.blockscript
```In fact, a simple alias would do. The file .blockscript has no contents. We are only interested in it's modification timestamp.

Then add some code to the script running every 5 minutes:
```

#Get the current time in seconds since the epoch
elapsedtime=$(date +%s)

#Get the time at which the file was touched in seconds since the epoch
touched=$(stat --format=%X $HOME/.blockscript)

#Calculate the difference
(( elapsedtime -= $touched ))

#If difference is less than 1800 seconds, exit
if [ $elapsedtime -lt 1800 ]; then
    exit
fi

```
This relies on the file access time stored in the Linux file system. I'm not sure how this works from a windows system, but the general idea may be adaptable.

thank you very much! That will do the job I'll give it a try and change the title to [solved] 

:D

---

### Post by BlinkinCat on 2013-05-28
> **Bojack5 said:**
> thank you very much! That will do the job I'll give it a try and change the title to [solved] 

:D

Here's how you mark as solved in your first post -

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Cheers - :)

---

