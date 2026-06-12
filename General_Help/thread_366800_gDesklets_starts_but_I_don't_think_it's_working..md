---
title: "gDesklets starts but I don't think it's working."
date: 2007-02-21
forum: General Help
---

### Post by sirchmeister on 2007-02-21
Ubuntu is great. I am just coming back to it after trying it a year or so ago. I am having a problem with gDesklets. I start it, but it simply sits there with a grey screen. I can give you a screenshot of what it is doing.

[[IMG]http://img341.imageshack.us/img341/2297/screenshotxy5.th.png[/IMG]](http://img341.imageshack.us/my.php?image=screenshotxy5.png)

I am currently using Feisty Fawn (Herd 3).

Thank you for your help.

---

### Post by adza on 2007-04-21
same error here, bump

---

### Post by chakkaradeep on 2007-04-21
Are you trying to start gdesklets at **logon** or by going to **Applications-->Accessories-->gDesklets** 

If you can check whether you get any errors dumped to terminal when you execute the command manually from a terminal. Just open the terminal and execute,
**gdesklets** and see for any errors being dumped.

---

### Post by adza on 2007-04-21
Chakkaradeep,

       From the terminal this deamon ran for a while, when i canned it the following was printed.. where would i find the log file it mentions?

adza@adza:~$ gdesklets
Starting gdesklets-daemon...
Connecting to daemon [    ###      ]
==========================================================[04/21/07-20:59:43]===
=== Unhandled error! Something bad and unexpected happened. ===

[EXC]
in /usr/bin/gdesklets: line 397 <module>
in /usr/bin/gdesklets: line 270 parse_command
in /usr/bin/gdesklets: line 174 __open_profile
in /usr/bin/gdesklets: line 155 __client_daemon
in /usr/lib/gdesklets/main/client.py: line 295 get_daemon
[EXC]/usr/lib/gdesklets/main/client.py

[---]  290                 daemon = connection
[---]  291                 if (daemon):
[---]  292                     break
[---]  293             except socket.error:
[---]  294                 pass
[ERR]> 295             time.sleep(0.1)
[---]  296 
[---]  297         print "\r" + " " * 40 + "\r",
[---]  298 
[---]  299         if (not daemon):
[---]  300             sys.exit(_("Cannot establish connection to daemon: timeout!\n"
[---]  301                         "The log file might help you solving the problem."))

---

### Post by chakkaradeep on 2007-04-21
> **adza said:**
> 
where would i find the log file it mentions?


Find it in ur home directory , path to follow is,

**/home/<ur user name>/.gdesklets/logs/gdesklets<some entries>.log**

---

### Post by adza on 2007-04-21
thanks! i've found this entry, does this mean a package is outdated (fresh install today, i doubt it) or that the gdesklets code is outdated?

/usr/lib/gdesklets/main/__init__.py:118: GtkDeprecationWarning: gtk.threads_init is deprecated, use gtk.gdk.threads_init instead
  gtk.threads_init()


okay, so i tried that update as shown here in the __init__.py file. Got a new error message in the log! how do i enable threading in python now it's been installed? (comes pre-installed)


**New log message****
No threading support available in python.
Compile python with --enable-threads. Exiting!

---

### Post by chakkaradeep on 2007-04-21
> **adza said:**
> thanks! i've found this entry, does this mean a package is outdated (fresh install today, i doubt it) or that the gdesklets code is outdated?

/usr/lib/gdesklets/main/__init__.py:118: GtkDeprecationWarning: gtk.threads_init is deprecated, use gtk.gdk.threads_init instead
  gtk.threads_init()

Not sure but i found many threads with the same query un-answered when i did a google search. Just try uninstalling gdesklets and installing them again.

**sudo apt-get remove gdesklets**
**sudo apt-get install gdesklets**

---

### Post by adza on 2007-04-21
still no luck :(  i might try looking for something different about the place...

---

### Post by adza on 2007-04-22
bump... has anyone else experienced this with feisty?

---

### Post by orb9220 on 2007-04-22
Did you install thru synaptic ? with gdesklets-data?.

Run from menu first should open manger where you select desklets. Some may not work.

then just add to sesson startup to run on startup.

If it shows installed in synaptic  then you can right click it properties and see dependencies,Installed files etc...

Runs on feisty,edgy fine on my machine.

[http://gdesklets.zencomputer.ca/](http://gdesklets.zencomputer.ca/)   for only working weather called good weather.

---

### Post by lionel47 on 2007-04-22
Same error here.  Tried installing and reinstalling but no luck.  Does anyone know of something else that works like gdesklets?

---

### Post by colonelPannick on 2007-04-23
This seems to be a bug iin the feisty version of gdesklets
[https://bugs.launchpad.net/ubuntu/+source/gdesklets/+bug/83922]("https://bugs.launchpad.net/ubuntu/+source/gdesklets/+bug/83922")

---

### Post by bg1256 on 2007-04-23
If you can't get this working, you could try compiling from source, or you might give adesklets a try.

---

### Post by adza on 2007-04-24
thanks for the help guys, compiling from source did the trick... no probs now :)

---

### Post by LinuxIsInnovation on 2007-12-15
Bump.
I installed it thru synaptics.. Still doesnt work..

---

