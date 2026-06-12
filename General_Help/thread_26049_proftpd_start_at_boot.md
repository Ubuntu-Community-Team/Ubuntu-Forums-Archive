---
title: "proftpd start at boot?"
date: 2005-04-11
forum: General Help
---

### Post by graigsmith on 2005-04-11
i got proftpd working, but how do i make sure it starts up on boot?

is there a file i can edit?

---

### Post by Arbiter on 2005-04-11
Hey all,

If anyone is experiencing problems with XMMS playback using ALSA or OSS, I used a simple workaround.

Apparently the GNOME sound server is interfering with XMMS.  If you disable it, you'll lose GNOME sounds, but everything else will still work.

Go to System -> Preferences -> Sound
 
The Sound Preferences window will appear.  Under the General tab, uncheck "Enable Sound Server Startup".

After doing this XMMS worked flawlessly, as did its offshoot Beep Media Player.

---

### Post by jobezone on 2005-04-11
[QUOTE=graigsmith]i got proftpd working, but how do i make sure it starts up on boot?

is there a file i can edit?[/QUOTE]
 Damn, I had such a good response here, and somehow it got screwed up. Anyway, here's the 2nd, shortest version:)
Go to /usr/share/doc/proftpd and you'll find good documentation on the application. Start by reading the README.Debian file there, if it exists, because it may contain explanations and comments by the Debian (or Ubuntu) maintaner of the package on how it is is integrated in Debian. Of course, the other contents in that directory will be usefull for you. It will most probably be explained there where and how does proftpd runs as a service in Debian(Ubuntu). Well, if it was automatically added as a service, it will be in the /etc/rc.*/ directories, where rc.2 is probably the runlevel you are running at.

I don't have the application, so I'm figuring it has installed documentation, like packages do in a Debian system, to /usr/share/doc/ . 
You'll probably get help also by running "man proftpd" which brings the man(ual) page of the application.

---

### Post by Gandalf on 2005-04-11
[QUOTE=jobezone]Damn, I had such a good response here, and somehow it got screwed up. Anyway, here's the 2nd, shortest version:)
Go to /usr/share/doc/proftpd and you'll find good documentation on the application. Start by reading the README.Debian file there, if it exists, because it may contain explanations and comments by the Debian (or Ubuntu) maintaner of the package on how it is is integrated in Debian. Of course, the other contents in that directory will be usefull for you. It will most probably be explained there where and how does proftpd runs as a service in Debian(Ubuntu). Well, if it was automatically added as a service, it will be in the /etc/rc.*/ directories, where rc.2 is probably the runlevel you are running at.

I don't have the application, so I'm figuring it has installed documentation, like packages do in a Debian system, to /usr/share/doc/ . 
You'll probably get help also by running "man proftpd" which brings the man(ual) page of the application.[/QUOTE]
if you run:
```

sudo update-rc.d proftpd defaults

```isn't better??

---

### Post by jobezone on 2005-04-11
it's simpler, eh.. but I'm not sure of what it does.
I told what I wish people told me when I started using linux, stuff that proved to be very helpful for me ever since.

---

### Post by Gandalf on 2005-04-11
[QUOTE=jobezone]it's simpler, eh.. but I'm not sure of what it does.
I told what I wish people told me when I started using linux, stuff that proved to be very helpful for me ever since.[/QUOTE]
 well it creates symlinks aytomatically in /etc/rc.* folders no need to manually create them using ln -s
it's better like this, and of course the proftpd must be in /etc/init.d folder you can't inlcude anither target ubless there's an option
check [COLOR=Blue]man update-rc.d[/COLOR]

---

### Post by jobezone on 2005-04-11
[QUOTE=Gandalf]well it creates symlinks aytomatically in /etc/rc.* folders no need to manually create them using ln -s
it's better like this, and of course the proftpd must be in /etc/init.d folder you can't inlcude anither target ubless there's an option
check [COLOR=Blue]man update-rc.d[/COLOR][/QUOTE]
 Doesn't debian (and ubuntu) automatically do that? Or usually it asks?

---

### Post by Gandalf on 2005-04-11
[QUOTE=jobezone]Doesn't debian (and ubuntu) automatically do that? Or usually it asks?[/QUOTE]
 well about proftpd install by apt-get yes it does (if you select daemon) but anyway if not use that function to easly install a service on linux boot

---

### Post by az on 2005-04-11
[http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=proftpd&version=hoary&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=proftpd&version=hoary&arch=i386)

It would seem that there is already an init.d entry as part of the package install:

etc/init.d/proftpd

---

### Post by Gandalf on 2005-04-11
[QUOTE=azz][http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=proftpd&version=hoary&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=proftpd&version=hoary&arch=i386)

It would seem that there is already an init.d entry as part of the package install:

etc/init.d/proftpd[/QUOTE]
 well of course there is but if there's no symlink to /etc/rcX.d directory (where X is the current runlevel check /etc/inittab to know it) it will not be executed on startup, check [color=blue]man update-rc.d[/color] to find out more about this

---

