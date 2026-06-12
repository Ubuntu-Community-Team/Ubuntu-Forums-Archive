---
title: "Ubuntu Software Center"
date: 2013-02-26
forum: General Help
---

### Post by scarabcoder on 2013-02-26
Hey, I am having trouble opening the Software Center. Every time I do, it just crashes and closes. I am trying to install a thing called "Scratch". Any way to open the Software Center without it crashing? Also, I tried running: "sudo software-center", and it still crashes. Thanks,
Scarabcoder
Oh, and when I ran the code, I get:
2013-02-26 16:07:02,037 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2013-02-26 16:07:02,058 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2013-02-26 16:07:02,566 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2013-02-26 16:07:02,576 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51, 'find_module')'
2013-02-26 16:07:02,575 - root - ERROR - Could not find any typelib for LaunchpadIntegration
2013-02-26 16:07:02,821 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2013-02-26 16:07:02,827 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()

---

### Post by ubudog on 2013-02-26
Try running the following:
```

cd ~/.cache; rm -r software-center 

```

Regards,
ubudog

---

### Post by scarabcoder on 2013-02-26
I did that, but I still get the problem. Is there something I should do afterwards? Do I need a restart?

---

### Post by ubudog on 2013-02-26
Perhaps try:
```
unity --reset
```

---

### Post by scarabcoder on 2013-02-26
I get this when I run the code:
ERROR: the reset option is now deprecated

---

### Post by TripDaRipper on 2013-02-26
Maybe you have an invalid source?

---

### Post by matt_symes on 2013-02-26
Hi

> 2013-02-26 16:07:02,037 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2013-02-26 16:07:02,058 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2013-02-26 16:07:02,566 - softwarecenter.backend.reviews - WARNING -  Could not get usefulness from server, no username in config file
2013-02-26 16:07:02,576 - softwarecenter.fixme - WARNING - logs to the  root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51,  'find_module')'
2013-02-26 16:07:02,575 - root - ERROR - Could not find any typelib for LaunchpadIntegration
2013-02-26 16:07:02,821 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2013-02-26 16:07:02,827 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()

Is that all the information you get before it crashes ?

Can you run software-center from the terminal again as your user and post back everything that appears on the screen please, just to double check. 

I would expect to see a call stack if its crashing.

Kind regards

---

### Post by scarabcoder on 2013-02-26
Ok, this is what I got:
2013-02-26 18:04:28,034 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2013-02-26 18:04:28,049 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2013-02-26 18:04:29,018 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51, 'find_module')'
2013-02-26 18:04:29,017 - root - ERROR - Could not find any typelib for LaunchpadIntegration
2013-02-26 18:04:29,385 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2013-02-26 18:04:29,390 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
Segmentation fault (core dumped)

I ran "software-center". Is there a way to re-install the software center?

---

### Post by matt_symes on 2013-02-26
Hi

> I ran "software-center". Is there a way to re-install the software center?

I'm not sure reinstalling would fix your problem as i suspect its the is with the data aptcache.open() is manipulating.

If you wanted to reinstall software center though, you can do that with this terminal command.

```
sudo apt-get install --reinstall software-center
```

Enter your password. It will not be echoed to the screen.

I suspect that will not fix the problem as i suspect it's the symptom and not the cause.

I may well be wrong though as there is no stack trace so i think reinstalling is worth a shot.

Kind regards

---

### Post by scarabcoder on 2013-02-27
Here is what I get:

Reading package lists... Done
nicholas@scarabcoder:~$ ... 0%

(I put in the last bit, it doesn't usually have the ... 0% after it)
Also, it still crashes.

EDIT: I tried to install my program with sudo apt-get install, but it just outputs this: 
Reading package lists... Done
nicholas@scarabcoder:~$ ... 0%
There is probably some missing file in the computer. Any way to fix?

---

### Post by matt_symes on 2013-02-27
Hi

> Also, it still crashes.I suspected as much.

Please run these commands

```
sudo apt-get clean
``````
sudo apt-get auto-remove
```> Maybe you have an invalid source?This is a good idea.

Please post the output of these commands.

```
grep -v "^#" /etc/apt/sources.list /etc/apt/sources.list.d/
``````
sudo apt-get check
``````
sudo dpkg --audit
```Please don't use the software center or run any other apt command until we have had a chance to look at this output.

EDIT: Just to add; because we are not getting a python call stack, i think it's crashing in one of the c libraries it must be using.

Kind regards

---

### Post by scarabcoder on 2013-03-01
Ok, I fixed the problem! Thanks for the users at IRC #ubuntu-beginners

---

### Post by matt_symes on 2013-03-01
Hi

Fancy sharing the solution for others who come along after you with the same problem ?

Kind regards

---

### Post by peshko-lnx on 2013-05-05
well it seems we will never know what is the fix....and it is nice to know since I have the same issue...

2013-05-05 09:18:18,726 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2013-05-05 09:18:19,114 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2013-05-05 09:18:19,115 - softwarecenter.plugin - INFO - activating plugin '<module 'webapps_activation' from '/usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc'>'
2013-05-05 09:18:19,119 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51, 'find_module')'
2013-05-05 09:18:19,119 - root - ERROR - Could not find any typelib for LaunchpadIntegration
2013-05-05 09:18:19,155 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
2013-05-05 09:18:20,664 - softwarecenter.ui.gtk3.views.lobbyview - WARNING - skipping exhibit for: 'u'steam-launcher'' not available
2013-05-05 09:18:20,665 - softwarecenter.ui.gtk3.views.lobbyview - WARNING - skipping exhibit for: 'u'splice'' not available
2013-05-05 09:18:20,665 - softwarecenter.ui.gtk3.views.lobbyview - WARNING - skipping exhibit for: 'u'fluendo-dvd'' not available
2013-05-05 09:18:20,665 - softwarecenter.ui.gtk3.views.lobbyview - WARNING - skipping exhibit for: 'u'stormcloud'' not available

(software-center:3764): Gdk-ERROR **: The program 'software-center' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadDrawable (invalid Pixmap or Window parameter)'.
  (Details: serial 3286 error_code 9 request_code 62 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the GDK_SYNCHRONIZE environment
   variable to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Trace/breakpoint trap (core dumped)

---

### Post by peshko-lnx on 2013-05-05
Any help would be appreciated!

---

### Post by matt_symes on 2013-05-05
Hi

@[**[COLOR=#000000]peshko-lnx[/COLOR]**]("http://ubuntuforums.org/member.php?u=1075545")

Was this a fresh install or an upgrade from a previous version ?

How long have you had this error ?

Did it happen directly after an update ?

Kind regards

---

