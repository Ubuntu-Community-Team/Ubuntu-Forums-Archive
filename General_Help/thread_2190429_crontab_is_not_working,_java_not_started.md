---
title: "crontab is not working, java not started"
date: 2013-11-27
forum: General Help
---

### Post by AdrianPtchv on 2013-11-27
I know the question is asked in many variants and I have read them, but still cannot find an answer to my problem.

I have a jar file which I want to run at startup as root. I have tried in rc.local, but no matter what I try it does not work.

So I tried crontab.

I open it as root: sudo crontab -e

And put the following in: @reboot sudo /usr/bin/java -jar /home/lead/Shutdown_3.0.1.jar hide

The command works if executed right from the terminal, but at reboot it does not work. I have tried @reboot sudo java -jar /home/lead/Shutdown_3.0.1.jar hide too with no success.

Any advise please?

Thanks!

-- P.S. I tried to set a simple cronjob to work on exact hour - /usr/bin/vlc It does not work. As it seems the crontab itself does not work. This is Ubuntu 13.10 by the way.

No errors or useful information in syslog neither.

---

### Post by ian-weisser on 2013-11-27
I see four common mistakes, but one is fatal:

1) [FATAL] You did not export or assign the DISPLAY environment variable when using an application that requires screen or console to work.
> /usr/bin/vlc

Here is an example of two crontab entries: The first will fail, the second will work.
Try them. They don't need to run as root.
```
* * * * * /usr/bin/vlc
* * * * * DISPLAY=:0.0 /usr/bin/vlc
```

I learned the DISPLAY variable of my current monitor by using the command [B]printenv
[/B]



2) The 'sudo' doesn't do anything. The root crontab is already run by root.
3) You created a new user-style crontab for root instead of using the existing /etc/cron.d . 
> @reboot [COLOR=#ff0000]sudo[/COLOR] /usr/bin/java -jar /home/lead/Shutdown_3.0.1.jar hide

Root crontabs created by the **sudo crontab -e** command are prefectly valid, but it's up to you to remember that they exist.

Most root cron jobs live in /etc/cron.d and are not created by the crontab command. The big advantage to that is programs can add/remove crontabs as they need. And users can use links to keep track of where they put cron jobs.
They have a slightly different format - a username field is added.
So a file in /etc/cron.d with username 'root' replacing that sudo would be perfectly valid syntax...for a non-**crontab**-generated file.




4) You did not redirect error output to a log file. So cron discarded it.

---

### Post by AdrianPtchv on 2013-11-27
Thanks Ian,

> 1) You put a command requiring a password or user console input into the command

I thought that when I write the job as root (i.e. sudo crontab -e) that should take care of the sudo part in the command

> 2) You created a new user-style crontab for root instead of using the existing /etc/cron.d
I am afraid I don't understand this - in the instructions about cron this was the way it is supposed to be done - open crontab -e, write command

> 3) You did not assign the DISPLAY environment variable when using an application that requires screen or console to work.
Could you please advise how should this look like, or, better even point a more exhaustive crontab manual?

> 4) You did not redirect error output to a log file. So cron discarded it.
I would be very grateful if you could point how this can be done, so I might see the errors generated.

Thanks!

---

### Post by ian-weisser on 2013-11-27
> **AdrianPtchv said:**
> I thought that when I write the job as root (i.e. sudo crontab -e) that should take care of the sudo part in the command

It will. But you *also* put sudo in the command.


> **AdrianPtchv said:**
> I am afraid I don't understand this - in the instructions about cron this was the way it is supposed to be done - open crontab -e, write command

A user (not root), can ONLY create cron jobs using the **crontab** command.
Root can use either/both of two methods:
- Root can use  the **crontab** command, just like any user. (That's what you did)
- Root can also use the format in /etc/cron*.  Take a look at any job in /etc/cron.d for an example. It's a normal crontab, with one additional username field, and it doesn't use the **crontab** command.

Both methods have advantages and disavantages. The big disadvantage to using the **crontab** command as root is that you might forget it's there, and then wonder why your system keeps doing this job when you want it to stop. You will look in your /etc/cron* jobs, but it won't be there. And you may find that frustrating someday.


> **AdrianPtchv said:**
> Could you please advise how should this look like, or, better even point a more exhaustive crontab manual?

You have probably already seen all the exhaustive manuals.
Start small, and build up until it breaks. Then you know what the problem is.

```

* * * * * /bin/date >> /tmp/testfile            # Works
* * * * * /usr/bin/vlc                          # Doesn't work, and we don't know why
* * * * * /usr/bin/vlc > /tmp/cron-log 2&>1     # Redirect error messages to a logfile. Still doesn't work, but now we can find out why!
* * * * * DISPLAY=:0.0 /usr/bin/vlc  > /tmp/cron-log 2&>1  # Get display from the 'printenv command'

```

See how we build on each working component?
The logfile tells us right away what the problem is: vlc won't start without a display.
Cron doesn't know anything about displays - it doesn't need one.
So we pass along the display information to the job, and vlc works great.

You want to start a java file. I don't know what it does. Is it interactive? Does it require a display?

You are asking the right questions!

---

### Post by AdrianPtchv on 2013-11-27
Actually, an exact hour - for example: > 15 12 * * * DISPLAY=:0.0 /usr/bin/vlc 
works for me. I.e. crontab works.

However same expression but without hour -  > @reboot DISPLAY=:0.0 /usr/bin/vlc 
does not work for some reason.

The other java job does not work with or without exact hour and with or without sudo.
I tried to put a script called shut in /etc/cron.d containing:

> #!/bin/sh -e

/usr/bin/java -jar /home/lead/Shutdown_3.0.1.jar hide

exit 0

It does not work.
The java has a display, which I want hidden - that is why I put "hide" at the end of command (it is advised by the author).

I must say I have no experience with scripting and cron.
So I'll need a bit of time to digest your answers :)
At the moment the mystery is why in a working cron job the command @reboot does not work.
Thank you!

---

### Post by ian-weisser on 2013-11-27
@reboot jobs that require a display will fail.

Think about the boot process: 
1) The system boots, 
2) The system thinks a while, 
3) The system lets you login,
4) The system thinks a while,
5) The system is ready to work.

@reboot jobs happen during step 2.
DISPLAY variables are not assigned until step 3.

You wouldn't want to run vlc as root anyway. (cvlc, however, should work)


> **AdrianPtchv said:**
> The java has a display, which I want hidden - that is why I put "hide" at the end of command (it is advised by the author).

Even if you don't use the display, the DISPLAY variable probably still needs to be assigned and valid. Your java application will look for that display (even if it never uses it), and quit when it doesn't find one. Depends how the application is written.
Usually that means running as a (logged-in) user instead of as root. Perhaps, perhaps not - I don't know anything about the application you are tyring to run.

It's more complex than assuming "the system has one user and one display." Lots of Ubuntu systems run headless (no displays) or single-user-and-display, or multiheaded (multiple displays), or simultaneously multiheaded and multiuser.

If you can describe what the java application does, perhaps we can suggest a path that may be easier for you to implement?

---

### Post by AdrianPtchv on 2013-11-27
OK, this proved to be exceedingly hard thing to do :) albeit I have a very simple goal: I want to start a small java applet at boot as root.
Obviously rc.local doesn't do the trick (and is not advised as an old system) and cron wouldn't do it neither.
I hear there is something called Upstart and it seems to me even more complicated and not suitable for the task.

What the java application does is to connect with android software through SAMBA over the LAN and allow for computer shut down. It basically, as I understand, issues a shut down command when a button on the android device is pressed and that is why it needs root - [this is the site of the programmer]("http://www.android-powerpoint.com/shutdown")

This is kind of frustrating.

Could you please advise what would be the best and simplest and the most elegant method to start a jar file at boot with root privileges?

Thanks!

---

### Post by ian-weisser on 2013-11-27
Thanks for the link. It explains much.

The short answer is that it's not a cron (@reboot) or Upstart (/etc/rc.local) issue. Those work fine.

The application seems to crash due to a bug that needs to be reported to the developer.
Specifically, the application still seems to require a DISPLAY environment variable despite the "hide" flag. Therefore it cannot be autostarted by a cron or Upstart/sysvinit/systemd job. It only works if input at a terminal with a DISPLAY assigned.

There are other ways to remote-shutdown a system.
For example, I use SSH. It's easy to use and secure, though the initial setup is a bit complicated.

---

### Post by AdrianPtchv on 2013-11-27
Thank you!
I was considering SSH, but it is not worthy just for the simple task to shut down the system.
And still I would like to know how should one start a small java applet at boot as root if the program requires display?

I also still don't understand why rc.local dose not work.
I tried to put > /usr/bin/java -jar /home/lead/Shutdown_3.0.1.jar hide  (with and without sudo) in rc.local  but nothing happens. What might be the reason for this?

---

### Post by ian-weisser on 2013-11-27
> **AdrianPtchv said:**
> And still I would like to know how should one start a small java applet at boot as root if the program requires display?
Unless you are willing do some fairly radical reconfiguring (creating a special user to start X before any humans log in, and having root use that user's DISPLAY), you cannot.

...*IF* the lack of DISPLAY is really the problem. Then it really  is a bug in the application, and the developer needs to revisit the  issue.

You *can* autostart it at login instead of boot. A DISPLAY exists then.
One way to set it up: [http://greeennotebook.com/2010/06/run-application-as-root-at-startup/](http://greeennotebook.com/2010/06/run-application-as-root-at-startup/)

At that point, you are using a webserver, java, samba, visudo, X, startup applications, and a lot of workaround. It may be fragile. And that's a lot of overhead (and attack surface) for a simple function that has root access to your system.



> **AdrianPtchv said:**
> I also still don't understand why rc.local dose not work.
I tried to put   (with and without sudo) in rc.local  but nothing happens. What might be the reason for this?

Well, I'm not psychic. My guess would be the same reason it fails for cron: No DISPLAY. rc.local runs at boot, not at login.

---

### Post by AdrianPtchv on 2013-11-28
Dear Ian, thanks for all the efforts!
I think I've collected now information for most of the methods involved at start-up so I can choose from.
Probably the one with giving no password root only for one application and, of course, the classic method with SSH are the most sensible.

Personally, I think the usage of SSH with private key is too complicated for this purpose so I've done it with editing sudoers. It works perfectly now.

Thanks again for the patience with the novice :-)

---

### Post by ian-weisser on 2013-11-28
Happy to see your system working the way you want it to!

---

