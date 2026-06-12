---
title: "Not able to login - ubuntu version 14.04"
date: 2015-02-27
forum: General Help
---

### Post by rajkumar4 on 2015-02-27
Hi All
I was facing login issue today morning into ubuntu 14.04, I changed the .Xauthority ownership to me. The same issue persists, I am seeing the below error in xsession-err

[COLOR=#333333][FONT=monospace]Script for ibus started at run_im.[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Script for auto started at run_im.[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Script for default started at run_im.
/etc/X11/Xsession.d/99x11-common_start: line 5 exec: init: not found

request support to resolve the issue[/FONT][/COLOR]

---

### Post by dino99 on 2015-02-27
that file on my vivid system:

# $Id: 99x11-common_start 305 2005-07-03 18:51:43Z dnusinow $

# This file is sourced by Xsession(5), not executed.

exec $STARTUP

# vim:set ai et sts=2 sw=2 tw=80:

---

### Post by Bucky Ball on 2015-02-27
*Thread moved to **General Help**.*

Welcome. You may have more luck here.

---

### Post by philipa on 2015-02-28
I've just resolved this problem myself.

When you login, the /etc/X11/Xsession.d/99x11-common_start runs "init --user". It expects to find "init" in the PATH.

Some update to 14.04 must have changed one of the following:
 - The order in which user profile files are executed vs running Xsession(5)
 - The startup program used by Xsession (now "init")

I guess it was some of the xserver-* changes released about 10 days ago.


The fix is simple - edit your .profile (or .bashrc, etc. depending on your shell) and ensure "/sbin" is in the PATH it sets.

---

### Post by Bucky Ball on 2015-02-28
Thanks for sharing and well done. Please mark the thread as solved to help future travelers by following the second link in my signature. Good luck. ;)

---

### Post by shghatge on 2015-05-26
Hey I am having the same problem. I think I deleted a path variable from some file earlier today. Now I have added the export path = default path back to the bash.bashrc file. However it is still giving me the same error. Even though PATH variable shows sbin. Can you please tell me what is your $STARTUP variable?

---

### Post by Arun_Dhwaj on 2015-12-02
Hello I'm facing same problem in '[COLOR=#000000]ubuntu version 14.04'
[/COLOR]
When I'd installed one software. Reason of it is some how, from .profile, "/sbin" path is missing.


I'd solved this problem by following steps:

Step-1: Go to CLI mode [ command line  mode ] by pressing "ctr+alt+F1",

Step-2: Login using userName, and passwd,

Step-3: Open .profile file.

In bottom, add these lines:

export PATH="$PATH:/sbin"  ## Its add init path to Xsession.


export PATH="$PATH:$HOME/.rvm/bin"  ## Add RVM to Path for scripting

[[-s "$HOME/.rvm/scripts/rvm" ]] && source "$HOME/.rvm/scripts/rvm"  ## Its Load RVM into a shell session *as a function* 


Step-4: Save and execute the ".profile" by
$ . .profile.

Step-5: Reboot the system. 

Now you will able to login in Graphics mode.

---

### Post by Bucky Ball on 2015-12-02
*Thread closed.*

This is an old, dead thread. Thanks for sharing another solution, but back to sleep. :)

---

