---
title: "How to unlock files?"
date: 2018-01-19
forum: General Help
---

### Post by alwaysaproblem on 2018-01-19
Like my username says- there's always a problem! :P:D I'm new to ubuntu. My friends set me up with this computer and I find it so frustrating after being so used to windows. Its much harder to do anything. 
So far, I've managed to delete things from the recycle bin that I didn't want deleted, tried to restore it using photorec, and now I've locked myself out of all my folders while trying to get it all back! I tried sudo chown/home/nebula/videos/recup_dir.5 and now all my folders are locked and I can't access them. I'm scared that if I try to follow any more web tutorials, I'll make things much worse.

---

### Post by TheFu on 2018-01-20
Welcome to the forums.

Unix (and Linux) are multi-user operating systems.  That means they are built from the start to deal with lots and lots of users.  Just because you are a single-user of the computer doesn't mean it can't have 2,000 users and be happy.
You are certainly learning the harder things earlier than most new users would.  Sounds a little self-inflicted. 

The basic idea behind Unix is that the system does what we tell it to do, even if that might be a bad idea.  Unix expects the user to know what is smart/clever and what is computer destroying.  That is part of the Unix-way.  If you don't know what you are doing, best not to hit <enter> on any chown/chmod sudo command.  Please.

But those capabilities mean that single-user ways of thinking just get you into trouble.  I promise, there is an elegance to Linux (and Unix), but the learning curve is steep.  Following disjointed tutorials isn't the best way to learn Linux.  When you are new, it is dangerous because lots of things on the internet are posted by people who don't know much more than you.  Or the posts are from 5 yrs ago and don't apply to your situation.  The hard part is that many things from 20+ yrs ago which are on the web ARE perfectly correct today.  How can you tell the difference?  You can't.

So - how should you proceed?  Short of taking a 3 week Beginning Linux course (for $2000), I can only recommend finding a reputable beginning linux book and following that from the beginning.  Of course, a few primers BEFORE starting with the book would be helpful too - you do need to have a tiny big of background just to know how Linux is different from Apple and Windows.  That there is a different F/LOSS culture which you may have never experienced before, and that thinking multi-user is necessary to really get comfortable with any Unix-based system.

I get asked almost the same question every week, so here's an article written with my best, shortest, advice: 
[http://blog.jdpfu.com/2017/03/31/learning-linux-condensed](http://blog.jdpfu.com/2017/03/31/learning-linux-condensed)

After you become familiar with Linux, you'll find using Windows very frustrating. Everything takes longer and you really don't have much control.  Plus every 3 yrs, you are expected to buy a new computer.  Linux frees you from those things.  Linux runs about the same on a $35 Raspberry-Pi or a $5M supercomputer.  The same commands and same ideas fit.  Your smartphone runs a version of Unix, so this knowledge works there too.  Basically, all the popular computers in the world that don't run MS-Windows - guess what they run?  Linux.  Your phone, TV, Bluray player, car, watch, router, camera, all run a form of Unix/Linux.

Be very careful using sudo, please.  The command you posted above doesn't make sense.  If you post the output from 'id' (open a terminal and run that), then we can probably help correct stuff.  It is always a smart idea to have backups BEFORE doing dangerous things - sudo chown is a dangerous thing, BTW.

Good luck and I hope this helps.

---

### Post by yancek on 2018-01-20
>  sudo chown/home/nebula/videos/recup_dir.5 

Not sure what that command would do if anything.  The command 'chown' means change ownership and you don't show any user name to change the ownership to but simply the path to the file you want to change.  If you had a user named nebula, for example, you would run this command:

> sudo chown nebula /home/nebula/videos/recup_dir.5

Did you get that directory using Photorec?  If you have a user named nebula, anything in an under it's home directory should be owned by nebula.  Exception is if you copied something there as root user.

---

### Post by alwaysaproblem on 2018-01-20
> **TheFu said:**
> Welcome to the forums.

Unix (and Linux) are multi-user operating systems.  That means they are built from the start to deal with lots and lots of users.  Just because you are a single-user of the computer doesn't mean it can't have 2,000 users and be happy.
You are certainly learning the harder things earlier than most new users would.  Sounds a little self-inflicted. 

The basic idea behind Unix is that the system does what we tell it to do, even if that might be a bad idea.  Unix expects the user to know what is smart/clever and what is computer destroying.  That is part of the Unix-way.  If you don't know what you are doing, best not to hit <enter> on any chown/chmod sudo command.  Please.

But those capabilities mean that single-user ways of thinking just get you into trouble.  I promise, there is an elegance to Linux (and Unix), but the learning curve is steep.  Following disjointed tutorials isn't the best way to learn Linux.  When you are new, it is dangerous because lots of things on the internet are posted by people who don't know much more than you.  Or the posts are from 5 yrs ago and don't apply to your situation.  The hard part is that many things from 20+ yrs ago which are on the web ARE perfectly correct today.  How can you tell the difference?  You can't.

So - how should you proceed?  Short of taking a 3 week Beginning Linux course (for $2000), I can only recommend finding a reputable beginning linux book and following that from the beginning.  Of course, a few primers BEFORE starting with the book would be helpful too - you do need to have a tiny big of background just to know how Linux is different from Apple and Windows.  That there is a different F/LOSS culture which you may have never experienced before, and that thinking multi-user is necessary to really get comfortable with any Unix-based system.

I get asked almost the same question every week, so here's an article written with my best, shortest, advice: 
[http://blog.jdpfu.com/2017/03/31/learning-linux-condensed](http://blog.jdpfu.com/2017/03/31/learning-linux-condensed)

After you become familiar with Linux, you'll find using Windows very frustrating. Everything takes longer and you really don't have much control.  Plus every 3 yrs, you are expected to buy a new computer.  Linux frees you from those things.  Linux runs about the same on a $35 Raspberry-Pi or a $5M supercomputer.  The same commands and same ideas fit.  Your smartphone runs a version of Unix, so this knowledge works there too.  Basically, all the popular computers in the world that don't run MS-Windows - guess what they run?  Linux.  Your phone, TV, Bluray player, car, watch, router, camera, all run a form of Unix/Linux.

Be very careful using sudo, please.  The command you posted above doesn't make sense.  If you post the output from 'id' (open a terminal and run that), then we can probably help correct stuff.  It is always a smart idea to have backups BEFORE doing dangerous things - sudo chown is a dangerous thing, BTW.

Good luck and I hope this helps.

Hi. Thanks for the welcome! You're right- it does feel dangerous to be following all these web tutorials and mucking around with the terminal, sometimes it works, and sometimes it doesn't. :( I don't exactly have $2000 for a course though. I'm a student with a very low income ;):KS

There's one thing I don't understand. With windows you can download any program with just a click of a button and run through the instructions. But with Linux it seems a whole lot more complicated, yet everyone tells me its easy!? 
So I guess there's nothing I can do about my emptied files in the recycle bin, and all my home folders etc. are locked "you don't have permission to use this folder.":(:-&

> **yancek said:**
> Not sure what that command would do if anything.  The command 'chown' means change ownership and you don't show any user name to change the ownership to but simply the path to the file you want to change.  If you had a user named nebula, for example, you would run this command:



Did you get that directory using Photorec?  If you have a user named nebula, anything in an under it's home directory should be owned by nebula.  Exception is if you copied something there as root user.

Hi. Yes I was using photorec. I'm a bit hesitant to try anything else now that I've locked myself out of all my folders. I'm thinking of maybe getting someone in to fix it if I can.

---

### Post by alwaysaproblem on 2018-01-20
I didn't do anything except shut down last night and switch on this morning- now I'm locked out of my account and can't get back in!!! How on earth does that happen??? Every time I type in the password, the screen goes black, and then goes straight back to the lock screen!

---

### Post by Impavidus on 2018-01-21
> **alwaysaproblem said:**
> I don't exactly have $2000 for a course though. I'm a student with a very low income ;):KSI learned Linux as a student with no income by using it in the company of people who already knew. As the entire science faculty was already Linux/Unix based (a lot of science software doesn't work on Windows), they weren't hard to find.
> There's one thing I don't understand. With windows you can download any program with just a click of a button and run through the instructions. But with Linux it seems a whole lot more complicated, yet everyone tells me its easy!? With just a few clicks or a single text command you can install anything that's in the repositories, which is simpler and more secure than the Windows way. It only gets harder than the Windows way when you want to install from source code, but that's really the last resort.
> **alwaysaproblem said:**
> I didn't do anything except shut down last night and switch on this morning- now I'm locked out of my account and can't get back in!!! How on earth does that happen??? Every time I type in the password, the screen goes black, and then goes straight back to the lock screen!
Sounds like you messed up permissions of your home directory so badly that the graphical session crashes as soon as you attempt to login.

Try to switch from the graphical login screen to the console (ctrl+alt+F1). Login using your username (I assume that's nebula) and your password. Nothing will show whilst typing your password, not even ****, but it should be accepted when you hit enter. Then try to fix ownership of your home directory:```
sudo chown -R nebula /home/nebula
```Make sure you get the spacing right. That command can't harm. It will set ownership of all files and directories in your home directory, including the home directory itself, to you. Unless you have very specific needs, that should be the right way. Logout from the console (use the **exit** command) and return to the GUI (ctrl+alt+F7). Then try to login.

---

### Post by TheFu on 2018-01-21
+1  - ```
$ sudo chown -R nebula /home/nebula
```
But only if your userid is actually nebula and the HOME directory is /home/nebula.

The **id** command would validate the userid.

To validate the HOME directory, use:
```
$ getent passwd|grep nebula
```

---

### Post by dragonfly41 on 2018-01-21
Also take note that Linux is *case sensitive.*
i.e.
You will not find /home/nebula/videos (as you wrote)
but you will find /home/nebula/[COLOR=#ff0000]**V**[/COLOR]ideos (which I believe may be the default at least in my 16.04 installation)

---

