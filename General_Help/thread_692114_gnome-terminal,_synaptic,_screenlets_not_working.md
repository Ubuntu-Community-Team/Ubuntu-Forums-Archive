---
title: "gnome-terminal, synaptic, screenlets not working"
date: 2008-02-09
forum: General Help
---

### Post by afz902k on 2008-02-09
Hello there fellows, I recently (yesterday) was playing with compiz and screenlets, and installed a few screenlets-widgets that were not included in the out-of-the-box screenlets setup (which I uninstalled already), and now gnome-terminal and in some cases synaptic won't run. Screenlets-manager doesn't start either.

I already checked out [this thread]("http://ubuntuforums.org/showthread.php?t=335997"), and [this other thread]("http://ubuntuforums.org/showthread.php?t=74348"), as well as [this one]("http://ubuntuforums.org/showthread.php?t=241673"), but the solutions posted there didn't help me as they seem to be a little outdated.

I am not using nvidia or ati drivers as my graphics card is an Intel Mobile 940/943/945, and I am not using xinerama either.

Here's what happens when I try to run** /usr/bin/x-terminal-emulator** as root or as a regular user using xterm:
```
(gnome-terminal:7254): GnomeUI-WARNING **: While connecting to session manager: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
The program 'gnome-terminal' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
 (Details: serial 1040 error_code 8 request_code 72 minor_code 0)
 (Note to programmers: normally, X errors are reported asynchronously; that is, you will receive the error a while after causing it. To debug your program, run it with the --sync command line option to change this behaviour. You can then get a meaningful backtrace from your debugger if you break on the gdk_x_error() function.)
```

Same happens when I run** /usr/bin/x-terminal-emulator --sync**

Thanks in advance for your help.

Edit: Also listen and System -> Administration -> Software Sources won't run.

---

### Post by afz902k on 2008-02-19
Bump. :confused:. I guess I'll re-install Ubuntu soon, or something.

---

