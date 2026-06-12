---
title: "Ubuntu 7.04 command line system boot order"
date: 2007-06-26
forum: General Help
---

### Post by randall_l on 2007-06-26
Hi folks, I've got a strange issue with Ubuntu 7.04 installed as a 'command line system' from the i386 alternate CD...

The boot order is a bit jumbled.  It boots, displays the login prompt, then displays more boot messages, burying the login prompt.  I'll try attaching a screenshot from VM Ware (it happens both in VM Ware and on the machine directly).

If the screenshot doesn't take, the messages follow:

BEGIN MESSAGES
...
* Loading ACPI modules
Ubuntu 7.04 ubuntu tty1

ubuntu login:

* Starting ACPI services...

* Starting system log daemon...

* Starting kernel log...

* Starting deferred execution scheduler atd

* Starting periodic command scheduler crond

* Running local boot scripts (/etc/rc.local)
END MESSAGES

Any way to resolve this?  I can't remember how to change the boot order so if that's all it takes, reminders will be appreciated.

Thanks in advance for any help.

Randall

---

### Post by letkemanp on 2007-06-26
Once your are certain that is has fully booted up you can try accessing a different terminal by pressing 

CTRL+ALT+F1
or
CTRL+ALT+F2
or
CTRL+ALT+F3
or
CTRL+ALT+F4

You may be able to go up CTRL+ALT+F8. The key combination my be slightly different because you are using the command line version only. However once you get logged in you might gain some valuable insight from looking at some of the logs. I think you can find the system log here /var/log/syslog

I know that this does not answer your question but it may help you access your system.
Pete

---

### Post by randall_l on 2007-06-26
Thanks for the quick response Pete.

I can log in fine.  I just type in the username, tap the ENTER key and it prompts for my password.

The issue is that the 'nologin' file is removed prior to the completion of the other boot scripts.  It's definitely something new with Feisty--Edgy boots as it should.

No information about the boot script order was found in the log files (syslog, dmesg, messages, kern.log).  I wouldn't expect it to be logged.

I guess it's just a matter of poking around in the init scripts until I find where it happens.  If anyone has any ideas for a resolution, I'd be glad to hear them.

Thanks.

Randall

---

### Post by Ragazzo on 2007-06-27
I believe this is caused by [upstart]("http://upstart.ubuntu.com/") that Ubuntu is moving to. The same thing happens to me (logging messages after login screen on tty1).  There are some files in /etc/event.d that you might find interesting.

---

### Post by randall_l on 2007-06-27
Thanks Ragazzo, I completely forgot about upstart. Brilliant!

All the scripts in /etc/event.d do are run the scripts in /etc/rc*.d

I tried grepping for "nologin" in the startup scripts.  The only scripts "nologin" occurs in are bootmisc and rmnologin.

It's happening immediately after the ACPI modules are loaded and before ACPI services are started.  Funny enough, run levels 2-5 start with S10acpid.  This leads me to believe that it's happening between the end of the execution of the scripts in rcS and the beginning of the executino of the scripts in rc[2-5].

I even commented out the line in /etc/init.d/rmnologin that removes the /etc/nologin file without change.  I guess that eliminates the init scripts as the issue, doesn't it?

I'll get the source of upstart 3.7 and grep it for nologin, just in case upstart itself is removing the /etc/nologin file.

Coincidentally, Edgy uses upstart 2.7 without the issue.  Maybe I'll get the source for 2.7 and figure out what the differences are.

---

### Post by Railsbuntu on 2007-11-06
The problem is still here in Ubuntu 7.10 :(

---

### Post by Vorl the Magnificent on 2008-02-12
I'm running 7.10 rather than 7.04; but as Railsbuntu notes, this problem persists in Gutsy.

So you'll know: Vorl = utter noob, especially to BASH (I've installed the CL version to learn).  Please consider the good-natured noobishness before you before framing a vitriolic reply.  End of defensive preamble and request.

I have devised a purely cosmetic workaround for this problem in the Gutsy 7.10 CL install.  The screen still doesn't drop straight to a login entry as one might like, but at least with this solution the screen tells the user what he or she needs to do to log on.

You'll need to edit your machine's rc.local script.  Once you've logged in, sudo in to the file in your favorite CL editor (vi, emacs, etc).  I use nano.

```
sudo nano /etc/rc.local
```

If you haven't done anything to it, rc.local should look something like this:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0
```

In the line right above "exit 0", put:

```
clear
echo "PRESS <ENTER> TO LOG IN"

```

This should print "PRESS <ENTER> TO LOG IN" at the top of your screen after the boot sequence...with the pesky "[ OK ]" letting you know the script ran.  Anyway, nothing's perfect.

Additionally: after discovering that my install responds to the "setterm" command, I modified the script to make the message a little more colorful and direct, substituting the following for the two simple clear/echo lines above:

```
clear
echo
echo
echo
echo
echo
echo
echo
echo
echo
echo
echo
echo
setterm -foreground green
echo -n "                            PRESS"
setterm -bold on
setterm -foreground magenta
echo -n " <ENTER> "
setterm -bold off
setterm -foreground green
echo -n TO LOG IN
setterm -bold off
setterm -foreground white
```

On a 1024x768 lcd, this puts your message in green and bright magenta right in the middle of the screen.

FYI -- an echo man page:
[http://www.ss64.com/bash/echo.html]("http://www.ss64.com/bash/echo.html")

FYI -- a setterm man page:
[http://linux.die.net/man/1/setterm]("http://linux.die.net/man/1/setterm")

If anyone has a more elegant solution to the Gutsy CL login issue -- namely, the solution which drops the user straight to a clear screen and the login prompt without having to press enter -- please post.

*--VoTMagn*

---

