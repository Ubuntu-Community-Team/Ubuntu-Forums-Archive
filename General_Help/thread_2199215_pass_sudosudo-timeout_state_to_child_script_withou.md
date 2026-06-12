---
title: "pass sudo/sudo-timeout state to child script without re-entering password, possible?"
date: 2014-01-12
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2014-01-12
Is there any way for a bash script to pass on to a child script it calls what you might call the "sudo/sudo-timemout state"? Kind of like exporting a variable? In other words make the parent script tell the child script "The user has another 7 minutes before sudo times out. Don't bother him with a password request for sudo prefixed commands for another 7 minutes" or something like that.

I believe I could call the child script with sudo and it wouldn't ask for passwords at all, no matter how long it ran. That should be about like using "sudo su" or "sudo bash" at the beginning of a script. But if the child script, which might be written with the intent that it could be run directly by the user and later re-used by scripts written later, creates any files (which a lot of mine do) they will be owned by root, so such scripts would have to be revised to conditionally, depending on who's running them, chown the files. Or make another version of the script to be run as root in which the commands that would be prefixed with sudo in the user's version wouldn't be and the commands that wouldn't be now would, but sudo'ed to user instead of to root.  Or rewritten to ALWAYS run as root. That, I suppose, would be the non-Deban, and hence non-Ubuntu way. But as long as I'm working within the universe of the ALL=(ALL:ALL) ALL powerful sudo, all of these approaches seem very inelegant, not to mention a lot of work. Of course, I could adapt the language of the child script and incorporate it INTO the parent script rather than call it as a child.  But the same objection applies to that, cubed. It also certainly wouldn't be the "(U|')nix way". The best idea I've come up with is to put a wmctrl statement at the head of all my scripts that use any sudo'ed commands to grab focus for the script and sudo -v right off the bat. If I run it directly, that won't be any problem and if I call it from another script at least it won't hide in the background waiting for a password. But it STILL means I can't give the parent script a password and walk away assuming all the sudo'ed commands will be run while I'm away. So it still sucks.

Now that I've explained why I'd want to do it, I reiterate: Is there any way for a bash script to export the state of sudo to a child script? And if not, can anyone suggest any better work-around than the ones I've listed?

Thanks for reading.

---

### Post by ian-weisser on 2014-01-12
Well, one way used quite often is to used dbus or a socket to trigger the root-level script instead of a user-level shell.
For example, if you have a network-manager icon or a battery-monitor icon, those are user-level applications that interact with system(root)-level applications. They exchange commands and data using dbus and PolicyKit instead of shell and sudo.

Here's an example of the process using dbus:
1) User runs user-level application.
2) User-level application makes a dbus request to the system-level application (that isn't running yet)
3) Dbus starts the system-level application
4) Dbus sends to the request to the (running) system-level application
5) System-level application does stuff
6) System-level application sends a dbus reply to the user-level application
7) (Optional) System-level application finishes and shuts down
8) User-level application shows response to user, finishes, and shuts down

The user script can often do all the dbus communication in one or two lines using the **gdbus** or **dbus-send** command.
The system-level application can be a bit more complex - there is no good shell command for receiving dbus messages, so I recommend python or C for that.
Er, since dbus handles all communication, the two applications can easily be written in different languages.


Here is an example of the process using sockets and Upstart-socket-bridge:
1) User runs user-level application.
2) User-level application connects to the socket
3) Upstart detects the connection on the socket and starts the system-level application
4) The system-level application connects to the socket
5) User and system applications do stuff and exchange data across the socket 
6) User-level application disconnects from the socket
7) (Optional) System-level application finishes and shuts down
8) User-level application shows response to user, finishes, and shuts down

I wrote a blog post about how to use sockets and Upstart-socket-bridge: [http://cheesehead-techblog.blogspot.com/2013/12/upstart-socket-bridge.html](http://cheesehead-techblog.blogspot.com/2013/12/upstart-socket-bridge.html)
Like the other example, the user- and system- applications can be written in any language you wish. Unlike dbus, socket servers *can* be written in shell.

---

### Post by Dreamer Fithp Apprentice on 2014-01-13
Thanks, Ian. You put a lot of effort into that. I also read your blog post. So far, I understood maybe a third of it. I confess I still can't see how to apply it. I'm beginning to wonder if I might be better off in the future to write all scripts from the beginning with the assumption they'll be run by ```
sudo path/script.sh
```and not use sudo internally at all. That's not the canonical way but it would certainly make it easier to use them from another script.

I'll read through it again when I've ingested about a hogshead of black coffee and maybe I'll understand a bit more of it.

---

### Post by ian-weisser on 2014-01-13
Yes, sudo up front instead of buried is an effective workaround.
The down side is that much more runs as root than you need.
Depends on what your script does.

---

