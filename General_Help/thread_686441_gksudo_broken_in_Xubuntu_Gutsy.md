---
title: "gksudo broken in Xubuntu Gutsy?"
date: 2008-02-03
forum: General Help
---

### Post by jjalocha on 2008-02-03
I'm trying to share f-spot between different users, so I created a new user 'photos', and added the old users to this group. In '/etc/sudoers' I added lines like:

```

john ALL=(photos) ALL

```

When I try to run f-spot as user 'photos', I get different errors, like:

```

john$ gksudo -u photos f-spot
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified
(gcalctool:5845): Gtk-WARNING **: cannot open display:  

```

Of course, f-spot works OK if I run it logged in a 'photos' session, But it doesn't work as another user.

I also tried to run other applications such as gcalctool, mousepad, and gucharmap, without success. Sometimes I get the same error message, sometimes it just says nothing but doesn't run.

I've never used gksudo as another (non-root) user before, so I don't know if I'm doing something wrong. Any ideas?

---

### Post by jjalocha on 2008-02-04
bump...

---

### Post by jjalocha on 2008-02-05
I forgot to mention that this problem only happens when I try to run gksudo as a non-root user. Without the '-u' option, or with '-u myself', it works as expected.

---

### Post by jrib on 2008-02-05
I'm guessing running ```
xhost +local:
``` makes it work?

I'm not sure this is the best way to do what you want though.  Why don't you just symlink user's ~/Photos to a common directory?

---

### Post by jjalocha on 2008-02-05
Thank you, Jason, for your reply!

I am using sudo, because I run into permission problems when using different users with sym-links. F-Spot (as well as any other Linux application?) creates all new files with 'user:user' ownership and 'g-w' permissions. Thus, before I can share the photos between different users, I have to change file permissions and/or ownership manually, even if I mutually add all users to all user-groups. I still could run a script that changes permissions automatically, but that seems less elegant to me than the solution with sudo. Still, any thoughts or insights are very appreciated!

Thanks for your hint, this goes in the right direction! After using xhost, all simple applications finally work. Sadly, F-Spot still doesn't run properly. I get the following error message:

```

F-Spot Encountered a Fatal Error:
F-Spot cannot find the Dbus session bus. Make sure dbus is configured properly or start a new session for f-spot using "dbus-launch f-spot"

```

With the following error details:

```

An unhandled exception was thrown: F-Spot cannot find the Dbus session bus.  Make sure dbus is configured properly or start a new session for f-spot using "dbus-launch f-spot"

  at FSpot.Driver.Main (System.String[] args) [0x00000] 
.NET Version: 2.0.50727.42

Assembly Version Information:

gdk-sharp (2.10.0.0)
gnome-vfs-sharp (2.16.0.0)
Mono.Addins (0.2.0.0)
NDesk.DBus.GLib (1.0.0.0)
NDesk.DBus (1.0.0.0)
System (2.0.0.0)
Mono.Posix (2.0.0.0)
atk-sharp (2.10.0.0)
gtk-sharp (2.10.0.0)
Mono.Addins.Setup (0.2.0.0)
glib-sharp (2.10.0.0)
gnome-sharp (2.16.0.0)
f-spot (0.4.0.0)
Mono.GetOptions (2.0.0.0)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.22-14-rt i686 unknown GNU/Linux

Distribution Information:

[/etc/debian_version]
lenny/sid

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.10
DISTRIB_CODENAME=gutsy
DISTRIB_DESCRIPTION="Ubuntu 7.10"

```

I will dig into this 'dbus-launch' now, and come back later with my findings.

---

### Post by jrib on 2008-02-05
If you want to try to resolve the permissions issue, you may be able to use ACL (Access Control Lists).  It takes a few steps to setup but I'm pretty sure that will let you set a default permission for files created in a directory.  There's a gui for it called eiciel.  Let me know how that goes.  I think I'll play around with that later too because I'm not too familiar with it.

---

### Post by jjalocha on 2008-02-05
Jason, with your help, I can finally share F-Spot among different users:

[LIST]
[*]Create user 'photos' from the GUI tool or the command line:
```

$ sudo adduser photos

```

[*]Add any users you wish to the group 'photos' with the GUI tool or from the command line:
```

$ sudo adduser john photos

```

[*]Run f-spot at least once logged-in as user 'photos'. (Not really sure if this is still necessary.)

[*]Add the needed users to '/etc/sudoers' using 'visudo':
```

john ALL=(photos) ALL

```

[*]Execute f-spot from the command line:
```

$ xhost +local:
$ export HOME=/home/photos
$ gksudo -u photos dbus-launch f-spot

```

[*]Or add a menu entry similar to '/usr/share/applications/f-spot.desktop' with the above changes.
[/LIST]

I think ACL is probably overkill for me in this situation, but it's still nice to know there are ways to do a finer access control!

---

### Post by jjalocha on 2008-02-05
I forgot to explain that the 'export HOME' line is necessary, because gksudo and sudo do not set the HOME and USER variables, and f-spot tries (and fails) to access the (incorrect) files at /home/john/.gnome2/f-spot.

To me, this looks like an error in Ubuntu, since according to the gksudo man page the '--preserve-env' variable should be used exactly to preserve john's variables. And with sudo, you should get the desired target user's variables with the '-H' option. But the output doesn't look right to me:

```

$ sudo -H -u test echo $HOME
/home/john

```

---

