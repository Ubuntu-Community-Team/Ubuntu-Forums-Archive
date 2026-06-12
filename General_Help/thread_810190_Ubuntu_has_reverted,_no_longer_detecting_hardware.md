---
title: "Ubuntu has reverted, no longer detecting hardware"
date: 2008-05-28
forum: General Help
---

### Post by gaylapdancer on 2008-05-28
Hi Guys.

My ubuntu (Gutsy) has been running fine since I installed it, (Waaaaay back when it was released :P ) But today it has started to play up. Today when I booted, all my themes, borders, buttons etc have reverted back to some ugly configuration, and my sound is not being detected anymore. When I try to open a utility to fix the problem, like the sound config, I get the message:

```
Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take
 effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. 
KDE) settings manager may already be active and conflicting with the GNOME
 settings manager.
```

I am a bit lost as to what to do. It was working fine yesterday, and there was only one update to run yesterday. Any ideas on what is wrong? Or how to fix it?

Thanks in advance
GLD

---

### Post by pointone on 2008-05-28
Have you tried simply restarting or logging out and back in? I used to periodically experienced this problem while running Gutsy, but logging back in always fixed it.

---

### Post by gaylapdancer on 2008-05-28
Thanks for the reply pointone.

I did try restarting and log-out/in, but it still stays the same.

Any more ideas?

Thanks
GLD

---

### Post by layingback on 2008-05-30
Have same problem.  Started same time with that 1 update to kernal.

gnome-settings-daemon is running (any attempt to start it fails with ```
** ERROR **: You can only run one xsettings manager at a time; exiting
```

Have tried all the solutions I could find here for same or similar problems:

 - hosts file is ok, and I've tried the various applicable suggestions
 - network loopback is working
 - selecting new [GNOME session]("http://ubuntuforums.org/showthread.php?t=579167&page=2#15") during login doesn't help
 - re-installing [dbus]("http://ubuntuforums.org/showthread.php?t=579167&page=3#26") doesn't have any effect
 - installing dbus-x11 doesn't help
 - show actions is set as described [here]("http://ubuntuforums.org/showthread.php?t=579167&page=2#13")
 - editing start up files as suggested [here]("http://ubuntuforums.org/showthread.php?t=579167#8") doesn't help.

I could live with no theme (even the green running man for logout ;-) ), and no sound, but the other impacts are severe:  slow loading, no screensave (monitor stays on), and no shutdown ability - have to use terminal for shutdown now command, and then manually switch off the box.

AMD64 Ubuntu 7.10 which has been performing fine for months - until 2 days ago, and hasn't booted right since - in, oh, say 30 tries.

It appears to be a race condition, and something in that update changed the timing just enough .. .

Anyone have a link to an actual fix?  Does anyone know if upgrading to 8.04 foxes, or just carries the problem through?

---

### Post by layingback on 2008-05-31
OK, I needed a fix fast (couldn't use factory installed Vista now could I?).

I upgraded to 8.04 from a broken 7.10 AMD64 with no panels showing!  Used CD as I'm on a slow (rural) broadband, with new updates pulled from 'Net.  I allowed upgrade to reset all configured files that it asked about.  The end of upgrade reboot failed to shutdown the system, which was 1 of the symptoms of this gnome-settings-daemon - dbus bug, so I carefully shutdown manually, then rebooted . . .

 . . . and end result was a working 8.04!!!

Have tried about 8 reboots since and no dbus/daemon error.  The same or very similar error was fixed in 8.04 beta, so hopefully this is now all behind me.

An extreme workaround, but an upgrade to 8.04 was planned anyway, just I really didn't have the time for it right now.  Hopefully this post helps give somebody hope.

---

