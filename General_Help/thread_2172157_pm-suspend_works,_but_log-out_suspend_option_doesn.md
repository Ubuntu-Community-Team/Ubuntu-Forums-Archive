---
title: "pm-suspend works, but log-out suspend option doesn't work"
date: 2013-09-03
forum: General Help
---

### Post by opus1 on 2013-09-03
In general, my questions are:
1. If "sudo pm-suspend" works, but using the "suspend" option from the log-out menu doesn't, how can I get the log-out menu to point to just "pm-suspend" instead of whatever script it's currently using?
2. How can I get the power manager to use just "pm-suspend" to suspend the computer after a certain length of inactivity instead of whatever script it's currently using?
3. Is it safe to allow other users to use pm-suspend, since it requires sudo privleges? (There's usually a good reason if something has sudo privleges)

Details:
I have upgraded my computers to xubuntu 12.04 from Lucid and they will not suspend if I choose "suspend" from the top right log-out menu.  While trying to troubleshoot, I discovered "sudo pm-suspend" from the terminal makes all three computers behave as expected (i.e., suspend and resume consistently and correctly).  When I try to suspend from the log-out menu, the computer acts like it's going to suspend (screen blanks, there's a lot of hard drive activity), but then the screensaver comes on. Two weeks of searching in various forums have not produced a problem quite like mine, nor a solution that works.

For the last 2 weeks, I've used a launcher on the panel that uses a script of mine that locks the screen and issues pm-suspend (see script at end of this post).  I don't know how to make it suspend automatically after 10 minutes of inactivity (e.g., the power manager). I used this thread: [https://wiki.archlinux.org/index.php/Pm-utils#Suspend.2FHibernate_as_regular_user](https://wiki.archlinux.org/index.php/Pm-utils#Suspend.2FHibernate_as_regular_user) to allow my user to use pm-suspend without a password.  The thread states:

"Because the pm-utils scripts must be run as root, you may want to make the scripts accessible to normal users by running sudo without the root password. To do so, edit the /etc/sudoers file with visudo as root. 
```

username  ALL = NOPASSWD: /usr/sbin/pm-hibernate
username  ALL = NOPASSWD: /usr/sbin/pm-suspend

```
Or you can enable it for a group, using the following lines, replacing group:
```

%group   ALL = NOPASSWD: /usr/sbin/pm-hibernate
%group   ALL = NOPASSWD: /usr/sbin/pm-suspend

```
Note: These must come after any user privilege specifications, e.g., username ALL=(ALL) ALL, or they will not work.

You can now run the scripts without a password by simply running:
$ sudo pm-hibernate or: $ sudo pm-suspend

Add the following lines, replacing username with your own user name, then save and exit visudo"

My suspend script is as follows:
```

#!/bin/bash
xscreensaver-command -lock
sudo pm-suspend

```

One other thing:  I tried putting an entry in the autostart applications for "xfce4-power-manager --no-daemon", because some people reported that would fix some suspend problems.  It did work for a couple of days, but then stopped working.

I should also note that I've read through the pm-suspend.log several times trying to find a clue about why suspend doesn't work and have not found anything out of the ordinary.

2 computers are new (to me), but one I've had for 2 years now with lucid installed and had no issues with suspend in those 2 years.  the other 2 are: a Toshiba Sattellite laptop and a home-brew desktop. I'm not running any proprietary drivers.  I realize it is helpful to post video card information, kernel version and pm-suspend.log, however which of the 3 computers should I post this info for?

Apologies for the long post.

---

### Post by Toz on 2013-09-03
There could be a number of reasons as to why this is happening. But a few more diagnostic things to try:

1. I believe that Xfce uses dbus to suspend. Perhaps there is a problem with dbus on your systems. Does suspend work if you run the following command as a regular user (sudo not required):
```
dbus-send --system --print-reply --dest="org.freedesktop.UPower" /org/freedesktop/UPower org.freedesktop.UPower.Suspend
```
...and if it doesn't, are any error messages displayed in the terminal window?

2. Or perhaps its an issue with xfce4-power-manager. First, shut down xfce4-power-manager:
```
xfce4-power-manager --quit
```
...then start it up in no-daemon mode to see if there are any error messages:
```
xfce4-power-manager --no-daemon
```
...and post back any error messages you might get. You can also try suspending by clicking on the suspend button in the logout screen and returning to the terminal window to see if any error messages are displayed.

3. xfce4-power-manager isn't running. You can check with:
```
ps -ef | grep xfce4-power-manager
```

---

### Post by opus1 on 2013-09-08
First, thanks for the troubleshooting ideas.  Second, sorry for the late reply -- my elementary school-aged boys started school this week, with all the activites that go along with it!

I tried your troubleshooting:
1) Suspend worked issuing this command.  No warnings in the terminal.  (This is a good one to know, I think).
2) I forgot I'd tried this and got some errors -- thanks for reminding me.  The errors that appeared upon issuing xfce4-power-manager --no-daemon were:
```

(xfce4-power-manager:3802): xfce4-power-manager-WARNING **: could not map keysym 1008ffa8 to keycode


** (xfce4-power-manager:3802): WARNING **: No outputs have backlight property

```
3) xfce4-power-manager is running when I check right after logging in.

Another frustrating wrinkle that may or may not be related:  My panel icon that issues pm-suspend doesn't work once-in-a-while (seemingly at random).  The pm suspend log shows that it finishes the suspend (let's say at 12:50:01) and then starts the resume process immediately afterward (at 12:50:02, for instance).  When I sit and watch it, it just looks like the screensaver comes on.  I have to reboot the machine to get it to work right again.  I can certainly post logs if needed.  Don't know if it's related or not, though.

---

### Post by Toz on 2013-09-08
> **opus1 said:**
> 
1) Suspend worked issuing this command.  No warnings in the terminal.  (This is a good one to know, I think).
Thats good. Dbus is working properly. Lets put that to the side of the table for the moment.
> 2) I forgot I'd tried this and got some errors -- thanks for reminding me.  The errors that appeared upon issuing xfce4-power-manager --no-daemon were:
```

(xfce4-power-manager:3802): xfce4-power-manager-WARNING **: could not map keysym 1008ffa8 to keycode


** (xfce4-power-manager:3802): WARNING **: No outputs have backlight property

```
When you run xfce4-power manager this way, then attempt a suspend by selecting suspend in the logout menu, do any messages appear in the window? Does the suspend work?
> 3) xfce4-power-manager is running when I check right after logging in.
Good.

> Another frustrating wrinkle that may or may not be related:  My panel icon that issues pm-suspend doesn't work once-in-a-while (seemingly at random).  The pm suspend log shows that it finishes the suspend (let's say at 12:50:01) and then starts the resume process immediately afterward (at 12:50:02, for instance).  When I sit and watch it, it just looks like the screensaver comes on.  I have to reboot the machine to get it to work right again.  I can certainly post logs if needed.  Don't know if it's related or not, though.
This happens to me as well, maybe once in 20 tries. Looks like something gets hung up. Next time it happens, have a look at the results of this command:
```
cat /var/log/syslog | grep PM:
```
...maybe it will show some relevant diagnostic information.

---

### Post by opus1 on 2013-09-08
In regards to the --no-daemon option of the power manager, I set it as an autostart option and it behaved as expected for a couple of days before exhibiting the same behavior as the "daemon" option (Is that how to say it?).  Having said that, I tried it again just now through the terminal and it behaved normally (successful suspend and resume) with no errors or warnings listed in the terminal (except for the initial warnings I noted in my previous post). 

It figures... now it behaves...

---

### Post by Toz on 2013-09-08
Keep this thread open in case it happens again. If it does, try to get an error message running --no-daemon from a terminal window. That might yield some useful information. As well as:
```
cat /var/log/syslog | grep PM:
```

---

### Post by opus1 on 2013-09-08
Ok, will do.  I'll post back if I have error information.

On a related topic:  Is it appropriate to post here the scripts I wrote to get what I wanted using just pm-suspend (e.g., suspend after 10 minutes of inactivity, multiple user support, ability to lock screen and suspend from the panel)? It does resolve my initial 3 questions, albiet as a workaround.  It could be useful to someone I suppose.  If not here somewhere else?

Thanks for your help Toz.

---

### Post by Toz on 2013-09-08
> **opus1 said:**
> On a related topic:  Is it appropriate to post here the scripts I wrote to get what I wanted using just pm-suspend (e.g., suspend after 10 minutes of inactivity, multiple user support, ability to lock screen and suspend from the panel)? It does resolve my initial 3 questions, albiet as a workaround.  It could be useful to someone I suppose.  If not here somewhere else?.
I think that would be great - we're always open to sharing of information and if it helps someone else, then by all means. I would suggest creating a new thread in the "Desktop Environments" subforum - it might led to some discussion.

---

### Post by opus1 on 2013-09-22
OK, I had my laptop refuse to respond to pm-suspend.  it would start doing something, but then would kick into the screensaver and not suspend. just like I described in post number 3.  I started the power manager in no daemon mode and no warnings appeared.  I did a "cat /var/log/syslog | grep PM:" and it just said:
```

Sep 16 20:15:09 satellite kernel: [ 2065.869638] PM: Syncing filesystems ... done.
Sep 16 20:15:09 satellite kernel: [ 2065.948031] PM: Preparing system for mem sleep
Sep 16 21:34:49 satellite kernel: [ 6846.249178] PM: Syncing filesystems ... done.
Sep 16 21:34:49 satellite kernel: [ 6846.265159] PM: Preparing system for mem sleep
Sep 16 21:35:25 satellite kernel: [ 6882.039600] PM: Syncing filesystems ... done.
Sep 16 21:35:25 satellite kernel: [ 6882.057679] PM: Preparing system for mem sleep
Sep 16 21:36:02 satellite kernel: [ 6919.590757] PM: Syncing filesystems ... done.
Sep 16 21:36:02 satellite kernel: [ 6919.605278] PM: Preparing system for mem sleep

```
So nothing seemed out of the ordinary.  I tried to suspend using dbus (as described in post #2), but it wouldn't work.  I thought about it and I wondered if there was an issue of some sort with my nfs mounted file server.  I decided to umount it and try to suspend.  I tried to umount and got:
```

umount.nfs: /misc/share: device is busy

```
Not very useful.  I found the solution here: [http://ocaoimh.ie/2008/02/13/how-to-umount-when-the-device-is-busy/]("http://ocaoimh.ie/2008/02/13/how-to-umount-when-the-device-is-busy/").  I had to use the fuser command to find out which process was keeping the device busy:
```

        # fuser -m /dev/sdc1
        /dev/sdc1: 538
        # ps auxw|grep 538
        donncha 538 0.4 2.7 219212 56792 ? SLl Feb11 11:25 rhythmbox

```
The above code was from the website example. In my case it was Opera, which had locked up earlier in the day, but it worked the same. I just had to do a kill -15 <pid> on the opera pid and then the file server would unmount and the laptop would suspend.

---

### Post by opus1 on 2013-09-22
Oh, and I did as you suggested, Toz and started in new thread in the Desktop Environments section that details my rather elaborate workaround for getting my machines to suspend the way I want.  Still would like to find the root cause someday, but it's working for now.  Details here: [http://ubuntuforums.org/showthread.php?t=2176094](http://ubuntuforums.org/showthread.php?t=2176094)

---

