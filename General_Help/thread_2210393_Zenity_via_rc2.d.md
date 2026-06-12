---
title: "Zenity via rc2.d?"
date: 2014-03-10
forum: General Help
---

### Post by BuntuSeriously on 2014-03-10
Greetings.

Consider the following example script fired off via rc2.d:

```
#!/bin/sh

while ! pgrep -c -x xfdesktop > /dev/null
do
    sleep 1
done

zenity --info --text=Test. --title="INFO"
```

After messing around with this for a good amount of time, it seems that zenity is launched at the proper point, closes after some undiscernible mischief, and then the script exits without further adieu.  Adding a loooong sleep after the while loop, or attempting to launch another dialog after the first does nothing to address the problem: Zenity simply croaks every time *and at any point* without doing its job when called from an init-launched script @ runlevel 2.

So, apart from resorting to an "application autostart" scenario, is there a "secret handshake" to get zenity to run correctly from a script which is fired off at runlevel 2?  Conversely, did I miss the mark: Is there another runlevel which would work without issue in a zenity/script context such as this?

Thanks!

---

### Post by ian-weisser on 2014-03-10
Running zenity as root from rc2.d means that it won't know what DISPLAY to put the notification onto.
Looks like you are using WHILE to wait for xfdesktop to start.

xfdesktop in 13.10 is started as a user-level Upstart job.
Example:
```
$ initctl list | grep xfce           # Note the lack of sudo
startxfce4 start/running, process 25201
```

That particular job is at ls /usr/share/upstart/sessions
Good info on Upstart (user-level) session jobs is at [http://upstart.ubuntu.com/cookbook/#session-job](http://upstart.ubuntu.com/cookbook/#session-job)
Since Upstart is the trigger, I would also use Upstart to fire the Zenity job. That would incidentally fix the permission and wait issues.

---

### Post by BuntuSeriously on 2014-03-10
@ian-weisser:

Thanks for the input!  Always good to get a hand with things like this . . .

Unfortunately, though, I'm still running 12.04; and will be here for quite a bit ;)  Among other things, you mentioned that zenity wouldn't know which display to get this out to: Do you know of a commandline parameter which could just herd it all over to the default for a quick fix?  Didn't see anything like this in the manpages, but I've learned that isn't always the last word...

If not, do you have a couple of quick tips as to how we'd be able to pull off an rc2.d-type Upstart launch???


Thanks again --

---

### Post by ian-weisser on 2014-03-10
The DISPLAY environment variable tells applications which of all the possible displays you are at. On newer systems, consolekit provides that information also. 13.10 and later, consolekit is replaced by systemd-logind. Consolekit and systemd-logind are accessed using dbus (which also prevents permission problems)

The DISPLAY variable is assigned by X after it starts, which occurs after you login. In other words, what you're trying to use zenity to signal anyway.
```
$ printenv | grep DISPLAY
DISPLAY=:0.0
```

Try this from two places:
1) An x-based terminal window:
```
$ zenity --notification --text="Foo"
``` 
It works. Your x-based terminal already knows the DISPLAY.

2) A tty (CTRL+ALT+F1)
```
$ zenity --notification --text="Foo"
(zenity:2276): Gtk-WARNING **: cannot open display: 

$ DISPLAY=:0.0 zenity --notification --text="Foo"

```
The first try doesn't work, and it tells you why: "cannot open display" The TTY doesn't know the DISPLAY.
The second try works when the DISPLAY is explicit.

Running Zenity from rc2.d is problematic, because the DISPLAY has not been assigned yet. It might be the same as last time, but it might not.
Generally, I think you should run login and X stuff from your ~/.autostart (depends on your desktop environment) instead of rc*.d.

---

### Post by tgalati4 on 2014-03-10
There are several ways to create notifications.  Zenity is an old framework that was designed for User Space.  So trying to run it as root without an X-Display would be problematic.

There are dbus notifications, notfify-osd/notify-send frameworks, and *wall*, *write*, and *talk*, and probably a few that I missed.

What is the script supposed to do?  What is the Use Case?

---

### Post by BuntuSeriously on 2014-03-12
Sorry for the delay in response: "Life Happens."


@ian-weisser:

Thanks for the insights.

Strange discovery: "DISPLAY=:" is not recognized on stock 12.04...

In any event, running zenity as I had envisioned here looks to be quite a wrangle.  Better paths ahead ;)


@tgalati4:

Thanks for expanding my palette here.  Didn't know there were so many choices out there messageboxwise.

Unfortunately, in this instance, "look-and-feel" dictates recourse to zenity.  On that note, it looks as though I've come up with a serviceable solution involving a root-fired helper script.  More to follow:


The use case is within a larger scripting scenario involving what ultimately winds up being a multiple-instance debacle.  Indeed, I had hoped to solve the whole matter with a single script.  In a nutshell, when taking recourse to an "application autostart" scenario (spawned to each new identity/user on a target system via skel), multiple instances of the script/program wind up in the task list.  Interactively pruning these instances becomes a permissions nightmare -- unless the pruning process is opened as root.

So, without digging into a potential security debacle stemming from running each "autostarted" instance as root, I settled on just running a separate helper script from rc2.d to stand by & take out the trash as needed...

On that note, I've been wanting to pose this question for a while: Apart from taking recourse to something like Perl, is there a "bash-centric" way of effecting a "sleep" delay without littering the task manager with multiple "sleep" processes?  I tried sending things to the background via "&" and weaving in "watch", but nothing seems to work.

Just an aside, if anyone knows :)


Thanks again; and have a great day --

---

