---
title: "gDesklets Daemon error"
date: 2005-04-09
forum: General Help
---

### Post by austinz on 2005-04-09
I installed gDesklets through Synaptic and I can't seem to get it to run.

If I start it through the gnome panel the gdesklets window opens but there's nothing at all inside.

If I run gdesklets from terminal I get:

Austin@zedulus:/$ gdesklets
Starting gdesklets-daemon...
Cannot establish connection to daemon: timeout!
The log file might help you solving the problem.

I'm a fairly new to linux so i'm not sure which log to look at.  I figure it's probably in /var/log or something but specifically....

Thanks in advance for the help!

Cheers
AUstin

---

### Post by Xian on 2005-04-09
[QUOTE=austinz]If I start it through the gnome panel the gdesklets window opens but there's nothing at all inside.[/QUOTE]
You mean the daemon manager appears? You'll need to install some desklets using that manager.

---

### Post by austinz on 2005-04-09
Yes, well, kind of.  The window opens, but it's just a blank window with the title "gDesklets Shell" and nothing else.
Here's a screenshot:

[[IMG]http://img27.exs.cx/img27/3473/screenshot9bp.th.png[/IMG]](http://img27.exs.cx/my.php?loc=img27&image=screenshot9bp.png)

also when I run it from terminal I get the same "failure to start daemon" message that I wrote about earlier.

Thanks again.

---

### Post by austinz on 2005-04-09
hoo ha

I found the log, and here's the output:

> Log messages of /home/austin/.gdesklets/gdesklets:0.0.log

==========================================================[04/09/05-15:16:13]===
=== Error in the core! Please report this bug!

[EXC]exceptions.ImportError:
[EXC]No module named gconf
in /usr/lib/gdesklets/gdesklets-daemon: line 114 ?
in /usr/lib/gdesklets/gdesklets-daemon: line 101 _gdesklets_main
in /usr/lib/gdesklets/utils/ErrorFormatter.py: line 119 _new_imp
in /usr/lib/gdesklets/main/Starter.py: line 3 ?
in /usr/lib/gdesklets/utils/ErrorFormatter.py: line 119 _new_imp
in /usr/lib/gdesklets/display/Display.py: line 1 ?
in /usr/lib/gdesklets/utils/ErrorFormatter.py: line 119 _new_imp
in /usr/lib/gdesklets/config/DisplayConfigger.py: line 4 ?
in /usr/lib/gdesklets/utils/ErrorFormatter.py: line 119 _new_imp
in /usr/lib/gdesklets/config/GConfBackend.py: line 2 ?
in /usr/lib/gdesklets/utils/ErrorFormatter.py: line 119 _new_imp
[---]/usr/lib/gdesklets/utils/ErrorFormatter.py
[---]  114 # give us an absolute path.
[---]  115 #
[---]  116 _old_imp = __import__
[---]  117 def _new_imp(name, globs = {}, locls = {}, fromlist = []):
[---]  118 
[ERR]> 119     module = _old_imp(name, globs, locls, fromlist)
[---]  120     # builtin modules have no "__file__" attribute, so we have to check for it
[---]  121     if (hasattr(module, "__file__")):
[---]  122         module.__file__ = os.path.abspath(module.__file__)
[---]  123     return module
[---]  124 
[---]  125 import __builtin__ 


any ideas?

Thanks!

---

### Post by penguinchrissy on 2007-04-12
Sorry I can't help but I'm having this exact same problem if I find a solution I'll be sure to post. Your not alone though.

---

### Post by penguinchrissy on 2007-04-12
I organially had gdesklets installed through automatix I uninstalled it through automatix then use synaptic to install it. At one point I think I had it installed both ways. But try uninstalling it and deleting the .gdesklets file from your home directory. Press crtl+h to be able to see it then reinstall it through synaptic. This worked for me hope it works for you.

---

### Post by diafanos on 2007-04-22
I have the same problem. 
Even though I removed them (with automatix) and reinstalled them with apt-get problem still exists.
My log file says:
> 
Log messages of /home/konstantine/.gdesklets/logs/gdesklets%3A0.0.log
/usr/lib/gdesklets/main/__init__.py:118: GtkDeprecationWarning: gtk.threads_init is deprecated, use gtk.gdk.threads_init instead
  gtk.threads_init()

==========================================================[04/22/07-13:14:27]===
Could not import tiling module!




Any suggestions?

---

### Post by krzys1825 on 2007-04-28
The same problem. White window when I run from gnome and info about failed start of daemon when I do it from console. Below logfile:

[I]krzys@Turion64:~/.gdesklets/logs$ more gdesklets%3A0.0.log 
Log messages of /home/krzys/.gdesklets/logs/gdesklets%3A0.0.log
/usr/lib/gdesklets/main/__init__.py:118: GtkDeprecationWarning: gtk.threads_init
 is deprecated, use gtk.gdk.threads_init instead
  gtk.threads_init()

==========================================================[04/28/07-08:56:56]===
Could not import tiling module!

[/I]

my configuration is:
ubuntu7.04, AMD64, HP pavilion dv8000


I can't wait to solve this problem :) 



KP>

---

### Post by bazzer on 2007-05-15
Anyone? Same here, amd64 install not working.....

---

### Post by Rui Pais on 2007-06-13
Hi,
this is a little old, but to not leave it without an answer... I deal with that problem today.

Here is the Launchpad bug entry:
[https://bugs.launchpad.net/ubuntu/+source/gdesklets/+bug/110103](https://bugs.launchpad.net/ubuntu/+source/gdesklets/+bug/110103)

one of the entries have this [package]("http://launchpadlibrarian.net/7542161/gdesklets_0.35.4-1ubuntu1_amd64.deb").
It works either install it or replace the original Ubuntu /usr/lib/gdesklets by the one that it's contained on package (open with file-roller or alike and extract package data.tar.gz, it's inside)

Hope this help anyone who found this thread with this problem.

---

### Post by ubonetu on 2007-07-01
That worked for me :-)

Thanks

---

### Post by xdarkxanarchyx on 2007-07-05
Thank you!!:popcorn:

---

### Post by Rui Pais on 2007-10-18
Oh hell...

new release, new revisitation of old bugs :(

Still the same for Gutsy, workaround still works.

---

### Post by jhenager on 2007-11-03
> **penguinchrissy said:**
> I organially had gdesklets installed through automatix I uninstalled it through automatix then use synaptic to install it. At one point I think I had it installed both ways. But try uninstalling it and deleting the .gdesklets file from your home directory. Press crtl+h to be able to see it then reinstall it through synaptic. This worked for me hope it works for you.
Deleting the .gdesklets folder was the key to the fix for me. Thanks!

---

