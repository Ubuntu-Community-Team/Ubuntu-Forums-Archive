---
title: "Killing Xorg Logs User Out of Session"
date: 2014-07-16
forum: General Help
---

### Post by kevin102 on 2014-07-16
Hey All,

[COLOR=#000000][FONT=Arial]Experimenting with my ubuntu box, I killed Xorg. The effect was to log me out of my session. If I log back in, the screen goes black for a moment, and then logs me back out. I can log in as guest or anyother user just fine.

I've tried restarting lightdm to no avail.  I can also login into a non-graphical terminal by pressing alt-cntrl-f1 at the graphical login screen.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Any ideas on what to do here?[/FONT][/COLOR]

---

### Post by steeldriver on 2014-07-16
Hello and welcome to the forums

There are a few common causes for the 'login loop' behaviour you're describing - once logged in at the Ctrl-Alt-F1 non-graphical terminal please do

```

ls -ld ~/{,.Xauthority}

```

and post back the results.

---

### Post by kevin102 on 2014-07-16
Thanks for the reply.  Running that command shows, first, the permissions on my home directory.  dwxr-xr-x 139 kevin kevin 

Then it shows the permissions on my .Xauthority file rw------- root root 

If I cat that file it read Kevin-ThinkPad-t4200MIT-MAGICK-COOKIE-1{Gby (and then some ascii and non-ascii characters mixed together that seem to be specs to my machine)

---

### Post by steeldriver on 2014-07-16
You need to restore the ownership of your ~/.Xauthority file or (easier IMHO, because it doesn't need special permissions) delete it and let the system create a new one

```

rm ~/.Xauthority

```

Then use Ctrl-Alt-F7 to get back to the GUI, and see if that fixes it

---

### Post by grahammechanical on 2014-07-16
Reboot? 

> [COLOR=#000000][FONT=Times New Roman]An [/FONT][/COLOR]*X server is a [program]("http://www.linfo.org/program.html") in the [[I]X Window System*]("http://www.linfo.org/x.html") that runs on [*local machines*]("http://www.linfo.org/local_machine.html") (i.e., the computers used directly by users) and handles all access to the graphics cards, display screens and input devices (typically a keyboard and mouse) on those computers.[/I]

[http://www.linfo.org/x_server.html](http://www.linfo.org/x_server.html)

[http://www.linuxcommand.org/man_pages/Xorg1.html](http://www.linuxcommand.org/man_pages/Xorg1.html)

X is one of the first things to run. Every thing else makes use of X. Kill X and it is no use restarting LightDM because it does not have a display server to run on. Your experiment has proved that. I hope that you not experimenting with your only installation of Ubuntu. If you are, then one day you will need to re-install. Be prepared for that.

Regards.

---

### Post by kevin102 on 2014-07-16
Thanks for the advice, I rm'd the file and it worked.

---

