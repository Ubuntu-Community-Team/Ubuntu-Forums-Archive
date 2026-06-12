---
title: "VERY Unhappy System - 12.04"
date: 2013-06-27
forum: General Help
---

### Post by artphotodude on 2013-06-27
Just got done a month ago building a 32-bit 12.04 system for my Mom and it seemed pretty bullet-proof (with the exception that the second hard drive used for back-ups is not too great-meant to replace in a month or two), but now the system is completely broken.  

Always starts off with an error message about a system problem, **Software Center** won't launch, Several panes in **System Settings** won't open. If I attempt to click on one of the problem settings panes and attmpt to close it, the **System Settings **program keeps reopening and jumping to the front (have to restart to close it).  Have run a package check in Recovery mode, but it cannot see anything is wrong and when booting from the live CD it says the system is 'Clean'.  I am assuming this must be a corrupt preference file or possibly a permissions problem somewhere.  

- Where should I begin?  I would rather NOT just rebuild it, but instead find out what is actually wrong.
- What should I be looking for on the Log file?

Any Help VERY Much Appreciated!!!!!!!!!!!!!!!!!!!!!!

---

### Post by snowpine on 2013-06-27
What does the "error message about a system problem" say?
Depending on the problem, that could have a ripple effect that is causing the other symptoms.

---

### Post by grahammechanical on 2013-06-27
There is something installed in Ubuntu 12.04 that is detecting those problems but it is disabled from reporting to you. The utility is called Apport. Read about it.

[https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport)

Look for the heading 12.04 and Later. You will need to edit the apport configuration file. The instructions are included. Nano is a text editor. There are two Nano commands that you need to know about.

Crtl+O = writeout or save
Ctrl+X = Exit

With Apport reporting enabled you will get more information about what is crashing.

Regards.

---

### Post by TNFrank on 2013-06-27
Did you do your updates after install? That's the first thing I did after install and I also do updates about twice a week just to keep up on any bugs that are fixed or newer versions of things. I've been running 12.04.2 for about a month now and it's been very stable and bullet proof IMHO.  Any Op System is only as good as the person taking care of it. Heck, I've got a buddy that swears by (and no AT) Windows 7 but he keeps his anti-virus up to date and puts a lot of work into keeping it running right.  
 I'd rather not work that hard, that's why I love Linux. I'm sure you'll figure it out, probably just one or two little tweaks and you'll be back to the good side of things. ;)

---

### Post by artphotodude on 2013-06-27
> **snowpine said:**
> What does the "error message about a system problem" say?
Depending on the problem, that could have a ripple effect that is causing the other symptoms.

Thanks for the quick reply!  It just says "system program problem detected."

---

### Post by artphotodude on 2013-06-27
> **grahammechanical said:**
> There is something installed in Ubuntu 12.04 that is detecting those problems but it is disabled from reporting to you. The utility is called Apport. Read about it.

[https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport)

Look for the heading 12.04 and Later. You will need to edit the apport configuration file. The instructions are included. Nano is a text editor. There are two Nano commands that you need to know about.

Crtl+O = writeout or save
Ctrl+X = Exit

With Apport reporting enabled you will get more information about what is crashing.

Regards.

THANKS! that is exactly what I needed to hear.  Will do it immediately.  The normal log files just didn't seem to have relevant messages, and they also where not appearing in response to the problems.  This should be great.

---

### Post by snowpine on 2013-06-27
I googled "system program problem detected" and found some very helpful links from askubuntu.com; have you tried those fixes yet?

---

### Post by artphotodude on 2013-06-27
> **TNFrank said:**
> Did you do your updates after install? That's the first thing I did after install and I also do updates about twice a week just to keep up on any bugs that are fixed or newer versions of things. I've been running 12.04.2 for about a month now and it's been very stable and bullet proof IMHO.  Any Op System is only as good as the person taking care of it. Heck, I've got a buddy that swears by (and no AT) Windows 7 but he keeps his anti-virus up to date and puts a lot of work into keeping it running right.  
 I'd rather not work that hard, that's why I love Linux. I'm sure you'll figure it out, probably just one or two little tweaks and you'll be back to the good side of things. ;)

Did all the updates available after installation, but my Mom using it offline over the last few weeks (just doing Gimp & some casual games).  After the problems started, did a full dpkg and everything seems to be OK.  Am guessing there MUST be some unified cause of this - like a module that all the effected software depends on.  Have done 4 other installs and nobody else has had a problem.  Really wanting to get this licked.

---

### Post by artphotodude on 2013-06-27
> **snowpine said:**
> I googled "system program problem detected" and found some very helpful links from askubuntu.com; have you tried those fixes yet?

All I could find was references to the Log file, which has not told me  anything, but will go on to try Apport - hopefully that will reveal the  issue.

---

### Post by artphotodude on 2013-06-27
BTW - Thanks AGAIN for all the quick, helpful time you all took to reply to this.  Will let you all know how it goes.  I must say after being involved with 15 years of high-level Mac (and some PC) repairs and maintenance, I have never run into such a helpful crowd as all of you.  Looking forward to being knowledgeable enough to help-out here myself.  

In the meantime, if any of you have a Mac that is being testy, Will gladly help any of you sus-up what is wrong - just email me at:  <snip>  Have very extensive scripting/hardware & software experience on Mac systems from OS 8.6 to present.

---

### Post by artphotodude on 2013-06-27
OK, so wound up finally getting some log feedback using the 'tail' command.  On trying to both click on an effected preference pane and launch software center got the following log response:
[COLOR=#b22222]
[/COLOR][COLOR=#b22222]   [/COLOR][COLOR=#b22222]Jun 27 14:02:49 MomsLinuxBox goa[1892]: goa-daemon version 3.4.0 starting [main.c:112, main()] [/COLOR]
[COLOR=#b22222] [/COLOR][COLOR=#b22222]Jun 27 14:02:52 MomsLinuxBox NetworkManager[1219]: <info> (eth0): IP6 addrconf timed out or failed. [/COLOR]
[COLOR=#b22222] [/COLOR][COLOR=#b22222]Jun 27 14:02:52 MomsLinuxBox NetworkManager[1219]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled... [/COLOR]
[COLOR=#b22222] [/COLOR][COLOR=#b22222]Jun 27 14:02:52 MomsLinuxBox NetworkManager[1219]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started... [/COLOR]
[COLOR=#b22222] [/COLOR][COLOR=#b22222]Jun 27 14:02:52 MomsLinuxBox NetworkManager[1219]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete. [/COLOR]
[COLOR=#b22222] [/COLOR][COLOR=#b22222]Jun 27 14:02:52 MomsLinuxBox ntpdate[1744]: step time server 91.189.89.199 offset -0.711932 sec [/COLOR]
[COLOR=#b22222] [/COLOR][COLOR=#b22222]Jun 27 14:03:47 MomsLinuxBox dbus[890]: [system] Activating service name='org.freedesktop.PackageKit' (using servicehelper) [/COLOR]
[COLOR=#b22222] [/COLOR][COLOR=#b22222]Jun 27 14:03:48 MomsLinuxBox dbus[890]: [system] Activated service 'org.freedesktop.PackageKit' failed: Launch helper exited with unknown return code 1 [/COLOR]
[COLOR=#b22222] [/COLOR][COLOR=#b22222]Jun 27 14:07:49 MomsLinuxBox kernel: [  362.501297] type=1400 audit(1372367269.992:26): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=1068 comm="cupsd" pid=1068 comm="cupsd" capability=36  capname="block_suspend" [/COLOR]

Does this point to any particular cause?

---

### Post by artphotodude on 2013-06-27
Well looking like this is Unfixable.  Too Bad.  Had high hopes that Ubuntu would be a suitable replacement from the Apple Money Machine, but is just seem too fragile and difficult to debug when something goes really wrong.  Thanks everyone for the attempts to help.

---

