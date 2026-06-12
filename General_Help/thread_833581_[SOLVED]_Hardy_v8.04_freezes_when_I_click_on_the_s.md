---
title: "[SOLVED] Hardy v8.04 freezes when I click on the shutdown button"
date: 2008-06-18
forum: General Help
---

### Post by RonB123123 on 2008-06-18
Hardy v8.04 freezes when I click on the shutdown button. In version 7.10, it would also freeze. Each time it freezes, I can't do anything about it except for pressing Ctrl + Alt + Backspace to restart grub.

The computer doesn't freeze *every* time but it does about half the time. Is there any way to fix this?

sowelie found that after shutting off unneeded startup services he experienced the same problem. **He enabled Power Management in System > Preferences > Sessions.** Logged off and logged back in. And clicking on the shutdown button was no longer an issue. This fix worked for me as well. :)

randy78 found a [bug report](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/203668/?loggingout=1) that entails this problem. In some cases, if you disable Power Management from System > Preferences > Sessions, it should fix the problem. It didn't work for me, however, according to the bug report, it has helped others.

---

### Post by randy78 on 2008-06-18
I experience it too...

Will be keeping an eye on this thread, so if you get it figured out, please post the solution!

Take Care

---

### Post by RonB123123 on 2008-06-18
I hope to find it soon. This is really bothering me and I was hoping so much that it would be fixed in Hardy. 

Someone post please. :)

---

### Post by phoenix23 on 2008-06-19
Having the same problem too. Subscribed.

---

### Post by RonB123123 on 2008-06-21
Bumping this topic again. Seems like others are experiencing the same problem. Hopefully somebody has a fix.

---

### Post by soxs on 2008-06-21
I read about freezings with the fglrx driver when trying to shutdown or logout(changlog fromx 8x to 8.6).
So you may try fglrx 8.6...

---

### Post by randy78 on 2008-06-21
Anybody?

---

### Post by supertails on 2008-06-21
Having the same problem. Is all of you guys experiencing firefox shutting down and unable to get it back up without a restart and some muting with VLC and other media players.

---

### Post by randy78 on 2008-06-21
> **supertails said:**
> Having the same problem. Is all of you guys experiencing firefox shutting down and unable to get it back up without a restart and some muting with VLC and other media players.

no.

---

### Post by lanzailan on 2008-06-22
[SIZE="4"][COLOR="DarkOrange"]same problem.. :([/COLOR][/SIZE]

---

### Post by randy78 on 2008-06-22
Going to file bug report today

---

### Post by randy78 on 2008-06-22
Ok, just an update...

It seems as if this bug has already been reported: [https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/203668/?loggingout=1](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/203668/?loggingout=1)

I am on a desktop and did not have Gnome-Power-Management enabled, but I just disabled ACPI power management from the Services menu to see if that will aid in correcting this problem.

I'll report back my findings

---

### Post by randy78 on 2008-06-22
Alright, 

After unchecking the acpi Power Management in Menu>System>Administration>Services and rebooting, it seems to be solved on my end.

Note that I don't have a laptop and do not require Power Management, so if you're on a Desktop and are experiencing this problem, give it a shot.

Laptop users proceed at your own risk!

Take Care

:guitar:

---

### Post by randy78 on 2008-06-23
Well, it was working fine and now it's up to its old tricks again...

Please post a solution if you find it!

---

### Post by spitzanator on 2008-06-24
Same.

Might it have been caused by the last set of upgrades that got shipped?

---

### Post by RonB123123 on 2008-06-25
My acpi service is already off and I still experience it. :(

Thanks for finding that bug report randy78, I'll add that to the front post w/ that solution in case it fixes anybody else's problem.

---

### Post by randy78 on 2008-06-26
Community is something that should never be taken for granted...

Let's keep working together til it's fixed!

:)

---

### Post by toddr on 2008-06-27
Greetings:)
I too am having the same issue. I have a Toshiba Satellite with 2.4ghz processor and an Intel graphics. I have been crawling different threads for a solution. Here are some of the threads: [http://ubuntuforums.org/showthread.php?t=5193&highlight=shutdown+problem](http://ubuntuforums.org/showthread.php?t=5193&highlight=shutdown+problem)
[http://ubuntuforums.org/showthread.php?t=767833&highlight=hardy+shutdown&page=2](http://ubuntuforums.org/showthread.php?t=767833&highlight=hardy+shutdown&page=2)
[http://ubuntuforums.org/showthread.php?t=586277&page=2](http://ubuntuforums.org/showthread.php?t=586277&page=2)
[http://ubuntuforums.org/showthread.php?t=623237&highlight=shutdown+problem&page=2](http://ubuntuforums.org/showthread.php?t=623237&highlight=shutdown+problem&page=2)
It seems to be a bug with acpi. I'm sorry I don't have a definitive answer, but maybe with the right combination it will work. I hope I can find an answer or maybe I'll switch to another distro. The funny thing is, this laptop worked perfectly with Dapper. But from Fiesty on, it has not shutdown properly. I have done upgrades and clean installs and have the same issue.:(

---

### Post by randy78 on 2008-07-02
Bump

---

### Post by soccerboy on 2008-07-02
since it is a known bug with acpi, switching distros probably won't help but you can try.  The best would be to go to the already open bug report and post a confirmation of your problem along with your dmesg log after hitting shutdown (when you experience the problem).  That could facilitate finding the bug.

---

### Post by toddr on 2008-07-04
Perhaps you could explain to me how I could post dmesg when the screen goes totally black, and no key combinations work. As a matter of fact, the only thing that does work is to do a hard shut down with the power button. As far as moving to a different distro, I found that other distros are having similar problems. It must be a kernel issue. As I explained earlier, this has been going on since Fiesty. Dapper worked perfectly.:confused:

---

### Post by toddr on 2008-07-08
For anyone interested, this worked:
[http://ubuntuforums.org/showthread.php?t=772733&page=2](http://ubuntuforums.org/showthread.php?t=772733&page=2)

:D:D

---

### Post by carl_pr on 2008-07-08
this happened to me. In my case it was an audio issue. I solved it following some instructuions how to fix pulseaudio.Now it never freezes anymore.

it might be your case too, maybe not.

---

### Post by sowelie on 2008-07-13
I was having this issue and I figured out it was my own fault.  I read an article about optimizing hardy.  One of the steps was to turn off unneeded startup services, so I went through the list (System -> Preferences -> Sessions).  I should have read through the list in more detail because I turned off the power management service.  When I turned this back on my issue went away, not sure if you guys have the same issue but I figured I'd mention my fix.

---

### Post by randy78 on 2008-07-20
> **sowelie said:**
> I was having this issue and I figured out it was my own fault.  I read an article about optimizing hardy.  One of the steps was to turn off unneeded startup services, so I went through the list (System -> Preferences -> Sessions).  I should have read through the list in more detail because I turned off the power management service.  When I turned this back on my issue went away, not sure if you guys have the same issue but I figured I'd mention my fix.

Yep! This worked for me :D

Thanks for the heads up...

---

### Post by RonB123123 on 2008-07-24
Thanks a lot sowelie! It worked for me too! I'll add the fix to the first post.

---

### Post by jwferk on 2008-07-24
I had the same problem.  It just popped up one day.

Power management was off.  I followed the system > preferences > sessions and turned it back on.  I had to reboot before it took hold.

I had also lost my "restart" and "hibernate" applets on the shutdown panel.  Those were replaced with

sudo apt-get install --reinstall gnome-applets

Thanks much to all of you.  This was frustrating.

---

