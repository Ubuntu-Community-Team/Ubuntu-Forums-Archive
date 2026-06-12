---
title: "[known bug] sudo command problem"
date: 2014-09-01
forum: General Help
---

### Post by WB0HYQ on 2014-09-01
Every time I try to execute a command using 'sudo', I get this:

bill@bill-UBU:~$ sudo -v
[sudo] password for bill: 
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
bill@bill-UBU:~$ 

and the command sometimes fails - as this one did.

This error will appear even whether I am logged in under Ubuntu (default configuration) or Xubuntu (using xfce4.1).  Anyone have any idea what is causing this?

Bill

---

### Post by deadflowr on 2014-09-01
it's a known bug
see
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1257186](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1257186)
and the dupe bug report here
[https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/1274680](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/1274680)

---

### Post by WB0HYQ on 2014-09-01
Ah. Okay. I did a search here and in the buglists, but apparently I didn't get the terminology right. Looks llike Samba has some 'splainin' to do.

Thanks, DF

Bill

---

### Post by WB0HYQ on 2014-09-20
I now have even more to report on this "known bug":

```

sudo gedit  (((a file)))
[sudo] password for bill: 
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory

(gedit:9206): IBUS-WARNING **: The owner of /home/bill/.config/ibus/bus is not root!

((( when I close Gedit, I get the following )))

(gedit:9206): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(gedit:9206): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
bill@bill-UBU:~$ 


```

I would really like to know a) why this is happening, and b) what can I do to stop it.

Bill

---

### Post by mc4man on 2014-09-20
> **WB0HYQ said:**
> I now have even more to report on this "known bug":

```

sudo gedit  (((a file)))
[sudo] password for bill: 
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory

(gedit:9206): IBUS-WARNING **: The owner of /home/bill/.config/ibus/bus is not root!

((( when I close Gedit, I get the following )))

(gedit:9206): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(gedit:9206): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
bill@bill-UBU:~$ 


```

I would really like to know a) why this is happening, and b) what can I do to stop it.

Bill

b. - Stop opening gedit with sudo (basically those are just warnings but still a poor idea ) use either gksudo, pkexec, or 
sudo -H gedit

---

### Post by WB0HYQ on 2014-09-20
Your last command (sudo -H gedit ...) still produced the same exact verbiage.

otherwise:

```

bill@bill-UBU:~$ gksudo gedit ((( file )))

((( dialog to enter password )))

(gedit:10883): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(gedit:10883): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
bill@bill-UBU:~$ 


```

and:

```

bill@bill-UBU:~$ pkexec gedit ((( file )))
error: XDG_RUNTIME_DIR not set in the environment.

((( dialog to enter password )))

(gedit:10899): Gtk-WARNING **: cannot open display: 

((( command failed -- no gedit appeared )))

bill@bill-UBU:~$ 


```

No matter what, I get warnings.

Bill

---

### Post by WB0HYQ on 2014-09-20
I don't know if this is tied in somehow, but I also get "Malformed file.  Press any kay to continue..." on booting up.  After ten seconds or so, this dissappears and boot starts up normally.

Bill

---

### Post by mc4man on 2014-09-20
Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: ect... is as mentioned just an irrelevant warning
(though shouldn't show when running a root gedit until  either an edit is started or until changes are saved & gedit is closed

The main reason *now* for not using sudo gedit is it uses your User preferences instead of root's. (may also create ~/.gvfs & other such nonsense.
Note that you can't use pkexec unless you set it up or get an enabled gedit package, it will get the warning also.

If you don't want to see the warning then
don't look
use a cli editor like nano
use alt+F2 with gksudo or pkexec

---

### Post by WB0HYQ on 2014-09-20
I didn't indicate (but should have) that the warnings did appear after I changed the file and saved/closed gedit (as you say).

Kind of hard not to see the warnings if I have a terminal window open.  They are right there in front of me :)

Before the upgrade of my system from 12.04 to 14.04 I did not get all those warnings and such so my feeling is that the upgrade didn't quite got all the places it should have.  Remember, as I say in my sig, I'm really new to the whole Linux thing, so I really don't know what/how to "set it up or get an enabled gedit package".  I'm assuming that "cli" means 'command line interpreter'.  I'll look into nano and see how to use it.

Alt-F2/Alt-F6 will, in fact, give me a giant terminal, and I can see how that might be useful, but until I learn a whole lot more about the inner workings of Linux, I won't be getting that detailed.

Thanks,

Bill

---

### Post by mc4man on 2014-09-20
There's been changes since 12.04 that cause that warning to show, to not would require source changes in affected apps (not going to happen) & this one is really meaningless to a user. Also now sudo gedit is not advised, if you were to make some change to your user's  gedit preferences you'll see that very clearly when using sudo gedit.

In an ubuntu (unity) session alt+F2 should open a command dialog, not really a terminal (it also stores previous commands - see screen for small example, double clicking on a history item will run it.

So in your current case I'd stick with gksudo gedit, sudo -H gedit or gksudo nautilus, sudo -H nautilus, either from a cli terminal or alt+F2 for gksudo
(- you can also just use a root nautilus to open in gedit, either by browsing or directly -  example - 
```
gksudo nautilus /etc/fstab
```
Then press enter on keypad to open in gedit (or whatever is your default gui text editor

Obviously you should be careful when using root to do anything.

---

### Post by WB0HYQ on 2014-09-20
I only see that thunbnail if I log out and log back in, but start a default Ubuntu session.  Currently, I am using an XFCE session and don't get that screen.

You are right about Alt-F2.  I was thinking of Ctrl-Alt-F2/F6 switching from desktop environment to terminal environment and back.  Alt-F2 under Xubuntu/XFCE doens't do a thing.

I am well aware of what damage being root can do.

It boils down to knowing that all the textual blather in the terminal window is/are warnings and, as such, can be ignored.  It was just a cleaner interface before I upgraded and I wondered if there was something I could do about it.

Bill

---

### Post by vasa1 on 2014-09-20
> **WB0HYQ said:**
> ...
It boils down to knowing that all **the textual blather in the terminal window** is/are warnings and, as such, can be ignored. ...
If you're interested, look at [http://askubuntu.com/a/422400](http://askubuntu.com/a/422400)

---

### Post by WB0HYQ on 2014-09-21
Very interesting thread you posted, Vasa1.  Intellectually, I knew that these were just warnings and such, but seeing them being spit out while working is a bit unnerving.  Thanks for that bit of input.  Learning how to use a terminal/cli is my goal.  I'm getting there, but slowly.

Bill

---

