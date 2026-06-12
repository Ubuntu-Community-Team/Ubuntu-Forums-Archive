---
title: "Some weird crashes and reboots..."
date: 2007-12-13
forum: General Help
---

### Post by jesushero on 2007-12-13
I'm currently running Gutsy on a pentium 4 2.6ghz / 512mb ram / asus albatron mboard / western digital 500 gb primary master (root) / western digital 120 gb primary slave / western digital 20 gb secondary slave (swap) / nvidia geforce agp / soundblaster audio.

My system freezes at random approximately once a day with no log entries. Total freeze, no keyboard, nothing. 

Also, when I'm transfering large amounts of data from the WD500 to the WD120 (large = ~80gb), both in GUI and terminal modes, about halfway through it stops with some error messages. fsck does not come up with any errors and an overnight memtest did 47 passes with no errors (a few friends suggested it may be a ram issue). 

It also sometimes logs off at random, with just gedit or firefox running, with the following log entries:
```

-----------------------------------<syslog>-------------------------------------------------------

Dec 14 01:36:56 Levendis gdm[5114]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 

------------------------------<auth.log>----------------------------------------------------------

Dec 14 01:36:56 Levendis gdm[5114]: pam_unix(gdm:session): session closed for user jesus
Dec 14 01:37:00 Levendis gdm[7654]: PAM unable to dlopen(/lib/security/pam_gnome_keyring.so)
Dec 14 01:37:00 Levendis gdm[7654]: PAM [error: /lib/security/pam_gnome_keyring.so: cannot open shared object file: No such file or directory]
Dec 14 01:37:00 Levendis gdm[7654]: PAM adding faulty module: /lib/security/pam_gnome_keyring.so
Dec 14 01:37:06 Levendis gdm[7654]: pam_unix(gdm:session): session opened for user jesus by (uid=0)
```

Another issue is firefox crashing on flash pages like youtube and myspace. 

I've been searching several forums for the past days and found most of these problems mentioned for MUCH older linux versions, some even dating back to 2005! 

Any ideas?????

---

### Post by jesushero on 2007-12-15
One day, 19 views and no replies??????

---

### Post by bojo42 on 2007-12-18
hello jesushero,

for your freezes take a look at [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/157777](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/157777) .  there seems to be a bug in powernowd which results in hard freezes, i've have experienced this on a amd turion and installing cpufreq instead of powernowd helps. altough then i have no "speedstepping", cause cpufreq seems unconfigurated, but no freezes anymore.

for your X restarting see [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/140554](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/140554) . this bugreport is very unspecific, cause most people won't understand that there can be many reasons for a crash of the xserver ;) maybe you can help to sort things out to drivers & hardware specific reasons.

hope this will  help you

cheers

bojo42

---

### Post by jesushero on 2007-12-18
Thank you Bojo42,

I got a bit confused though with cpufreq and powernowd. I've never dealt with either, and having a look today I understand that cpufreq is installed as the server and powernowd as the client, so they are both there. BUT, my processor does not seem to support them so they are actually not doing anything (or at least that's what they say).

So should I uninstall powernowd?

I do have another question about my processor, it is an Intel Pentium 4 at 2.6 GHz with Hyper-threading enabled. Ubuntu sees that as being two identical Pentium 4 at 2.6 GHz, naming them Processor 0 and Processor 1. Is this the way it should be? I never had any other OS seeing that as two processors and the bios only refers to the one processor that is really there. 

I have been having similar crashes with Win XP in the past, now I no longer use Windows, but it had nothing to do with browsers or video. The crashes now seem to be happening only when I am running video applications, such as flash websites or video editing on Kino. 

At first I was not using the restricted drivers for my nvidia card, I later installed them but there was absolutely NO CHANGE. I seem to have an ANCIENT Geforce FX5200. I tried to find drivers from nvidia's website but no luck.

I still haven't spotted what is causing the X server to restart, but it does not happen very often, the full crash is much more often, at least once a day.

Could it have to do with the BIOS??? Is there any use in updating my BIOS? If so, how would I do that?

---

