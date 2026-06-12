---
title: "Run command on idle?"
date: 2006-11-23
forum: General Help
---

### Post by shingalated on 2006-11-23
Is there a way to run a command (such as 'xtrlock') after my session has been idle for 5 mins?

---

### Post by cantormath on 2006-11-23
> **shingalated said:**
> Is there a way to run a command (such as 'xtrlock') after my session has been idle for 5 mins?

Not quite sure what you mean...

---

### Post by shingalated on 2006-11-23
like instead of running a screen saver after 5 minutes run this command to lock my session (xtrlock)

---

### Post by shingalated on 2006-11-25
bump

---

### Post by CatKiller on 2006-11-25
I believe that you can use DBUS to test whether the session is idle, but I'd have absolutely no idea on how to go about it. Hopefully that will give you something else to search for to point you in the right direction.

It's not that we don't care - I guess the people here just don't know how to do it. Don't forget to let us know how you did it if you do manage it.

Good luck!

---

### Post by syadnom on 2006-11-25
how about this.  make a shell script for the command you want and copy that script into the directory with screensavers.  then set your screensaver as the shellscript(mark the shell script executable!) and set the screensaver at 5 minutes.

---

### Post by shingalated on 2006-11-27
How can I set a shell script as a screensaver?

---

### Post by syadnom on 2006-11-27
im not on ubuntu and the moment(osx) but you just need to find the screensavers(find / | grep nameofascreensaver) and put a script in that directory.  then you can select it on the screensaver menu.

make sure to fork off the program or the screensaver may try to kill it on kb/mouse activity(program &)

---

### Post by shingalated on 2006-12-07
It shows up in the menu, ut all I get is a black screen when it comes on, and I move my mouse and I'm back to my desktop.

---

### Post by syadnom on 2006-12-08
the screensaver program must kill the process or something. 

next though is an if/then shell script run as a cron job.  you will have to do some research here but you can make a script that looks at your username(read up on awk) and compares your idletime to a number you give(15minute or something) and if the idletime is greater, then it will run a program.  i have such a script i will post here later today if i get a chance though you will have to modify it.  my script looks for all BUT root, and some other usernames i run scripts under and kills any user sessions for users logged in for longer than 15miunutes without doing anything.  this is on a digital unix server but the script runs in bash so it should run unmodified for you though you will have to change the 'exemption' list to users on your system you dont want killed such as root, daemon, web... anything like that.  you can do a 'who' to see what users processes are currently running under.

---

### Post by syadnom on 2006-12-08
# kill idle users script by dan 10/14/2002
awk '{
###this is how long in minutes
  IDLETERMINATE=15;
  NAME = $1; PID = $7; IDLE1 = $6; IDLE = split($6,IDLETIME,":");
  if ((NAME != "root") && (NAME != "daemon") && (NAME != "otheruser") && (NAME != "otheruser"))
    {
    if (IDLETIME[1] >= IDLETERMINATE)
       {
####this will print some statement out for the log file
       print "User "NAME" has been idle for "IDLE1" minutes, user will be terminated"
       system("date");
####instead of kill, run your program in the spot below
       system("kill -9 " PID);
       }
    }
}'
# end KILLIDLE

---

