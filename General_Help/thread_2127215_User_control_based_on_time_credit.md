---
title: "User control based on time credit"
date: 2013-03-19
forum: General Help
---

### Post by kickit2 on 2013-03-19
My kids are getting BADLY addicted to their computers and their chores are beginning to be neglected.  The typical monetary rewards for chores seem to hold little allure so I thought perhaps a reward system in which they must complete their chores for computer time would work nicely.  So I'm wondering if there is a manner of user management in which the user has a time balance and they can only use the computer while that balance is >0.  

For instance - say they have 60 minutes on their account; they could either have 4-15 minute logins or 1-60 minute login but in either case they would be logged off when they hit 0.  I also want this to hold true over the course of days - I.E. NOT a time limit per day, a time limit that I have to manually increment up.  If they are out of time and haven't earned more then they haven't earned more time - regardless of it being a new day.  In this manner I could attribute differing time amounts to different chores.

Does anyone know if a system like this exists?

Thanks

---

### Post by ibjsb4 on 2013-03-19
I know of kshutdown, its in the software center.

[http://kshutdown.sourceforge.net/](http://kshutdown.sourceforge.net/)

[http://gshutdown.tuxfamily.org/en/index.php](http://gshutdown.tuxfamily.org/en/index.php)

---

### Post by kickit2 on 2013-03-19
As far as I can tell this just schedules shutdowns / logoffs at specific times and doesn't draw from any kind of "balance".  Some system that would allow login based on a "minute balance" and run it down while logged in is really what I'm looking for.  I know there is also the pam_time module but that again controls logins based only on time of day / week.  While I'd probably use this in conjunction, again its lacking.

---

### Post by HermanAB on 2013-03-19
You can use PAM Time:

[http://serverfault.com/questions/139789/how-can-i-limit-the-login-times-in-linux-for-certain-users](http://serverfault.com/questions/139789/how-can-i-limit-the-login-times-in-linux-for-certain-users)

---

### Post by kickit2 on 2013-03-19
pam_time controls what times of the day / week that logins are permitted.  It does not control how long they can be logged in for.   

Lets see if I can explain this better.  For instance - Joe does X,Y and Z in regards to chores and earns 6 hours of computer time because of it.  I would enter this into the computer and then he would be free to use that time as he sees fit.  Perhaps he would use all 6 hours in one sitting, or maybe an hour here and there, but regardless of the combination he would be locked out when the total 6 hours was used even if it took a week for him to do so.  I would like the tracking to span multiple days (not just give more time each day) so the children have to earn additional time (and not just wait until the next day).  

The more I look into this the more I feel like I am going to end up having to write this with some pam tie-in to check/update a database and go from there.

---

### Post by zero2xiii on 2013-03-19
Hay,

Just to help clarify the point the OP is trying to make.

He is looking for software similar to what you used to get at internet cafys. You buy 30mins computer time, and after that 30minutes are done, your session gets locked and you either need to buy more time, or abandon your session.

@OP

I think this will be a very simple thing to script. if "security" is not the biggest concern:

Thinking in the lines of:

```
cat time.txt
60
```
then jumping into a timed loop reading the file, and the current system time, subtracting the difference eg:

at logon:
logon_time=13:00

then after every 60 seconds:
current time - log on time
eg
Current_time - logon_time = 19

then reduce file value:
echo 60-19 > time.txt

after file time.txt reaches zero (or sub zero depending on the polling time)
run the logoff or shutdown command. Or simply lock the screen, refusing unlock if file time.txt is not bigger than 0.


This should be a relatively simple thing to script if some form of software is not available.

Cheers

---

### Post by haqking on 2013-03-19
I know some people who have had success with mkahawa which is a newer version of cafe con leche

[http://sourceforge.net/projects/mkahawa/](http://sourceforge.net/projects/mkahawa/)

---

### Post by zero2xiii on 2013-03-19
Hay again,

Sorry for multi posts again admins. It is just to keep things clear.

At OP again.

[http://manpages.ubuntu.com/manpages/hardy/man5/timeouts.5.html](http://manpages.ubuntu.com/manpages/hardy/man5/timeouts.5.html)
[http://manpages.ubuntu.com/manpages/dapper/man8/timeoutd.8.html](http://manpages.ubuntu.com/manpages/dapper/man8/timeoutd.8.html)

I realise that these only allow for a "daily" time limit. But I think it should be, adjustable, with some scripting.
However I can not seem to find a "unspecified time" option.

Writing about 3 scripts may solve this issue:
Storing MAX time allowed in a file
After log off modify MAX time
After a new day begins, read MAX time and adjust daily limit untill daily limit becomes zero.

It seems this might be an easier solution. Just interfering (yep) with the already there aplications, than trying to write a new "program" for this purpose.

Will a daily limit not suffice?

Cheers

---

### Post by Impavidus on 2013-03-19
I'm not aware of any utility that will do it for you, but I think this would be the idea:

You need a deamon, started automatically at boot and running as root so the kids can't kill it, that checks every minute who is logged in. If it's one of the kids, subtract one minute from their quotum and stores the new quotum in a file owned by root, so they don't have write permissions on that file. Then the deamon sleeps for one minute and starts again.

When the quotum is zero they will be logged out. I'm not sure how to do that, but sending the SIGHUP to the desktop manager may work. You can even put an applet in a panel to show them their time remaining.

Of course, you would have a simple tool to change their quotum manually as a reward (or punishment...).

Edit: OK zero2xiii, that's almost exactly what I was describing.

---

