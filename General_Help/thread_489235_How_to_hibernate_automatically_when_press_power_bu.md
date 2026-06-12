---
title: "How to hibernate automatically when press power button?"
date: 2007-07-01
forum: General Help
---

### Post by UJoe4 on 2007-07-01
Using Kubuntu Feisty. When I press the power button on my laptop, it brings up a "Logout/Suspend/Hibernate/Restart/Turn off" menu. I'd like to change that so it hibernates automatically instead.

I may just be missing something obvious, but I haven't been able to find a way to do this with the GUI. In the Power Manager there are settings for what to do when the lid is closed, but not when the power button is pressed. And I couldn't find anything in the System Settings options either.

In "/etc/acpi/powerbtn.sh", the command that it runs is: 

/usr/bin/dcop --all-sessions --all-users ksmserver ksmserver logout 1 2 0

This is what brings up that Logout menu. So I tried replacing that line with "/etc/acpi/hibernate.sh", but that doesn't quite work. It hibernates fine (and the computer powers off), but on resume it logs me in immediately to my previous session rather than giving me a login prompt (which is what I get when I resume from a normal hibernation). There may be other differences that I haven't noticed as well.

So are there different options I could pass to /usr/bin/dcop to get it to hibernate immediately instead of displaying the menu? Or is there a command I could put at the end of hibernate.sh (or in one of the scripts called by resume.sh) to bring up a login screen on resume (but that would presumably mean I'd have to go through 2 login screens after hibernating via the menu)?

Thanks!

---

### Post by UJoe4 on 2007-07-01
Bump...

---

### Post by Di@blo on 2007-07-01
What version of Ubuntu are you running? Because I know @ least 6.06 and up it's in the Power Management section under System -> Preferences.

---

### Post by UJoe4 on 2007-07-01
Thanks, I'm running Kubuntu 7.04 Feisty Fawn. The "Power Manager" (that you get to by clicking the battery icon at the bottom of the screen) doesn't have it, and I couldn't find anything in System Settings either.

For Gnome users this option does seem to be in the "Power Management" section (found a picture here: [http://spidertools.com/ub_pow3.png]("http://spidertools.com/ub_pow3.png")), but what I'm looking for is the equivalent in KDE.

Or alternatively just how I could modify that /usr/bin/dcop line to hibernate automatically rather than displaying a menu.

---

### Post by phoenixjim on 2007-07-01
I too hope to see an answer to this question - but I hope it does not limit itself to gui-based solutions...

I'm running Fiesty 7.04 Server. Love the OS - and the Distro :) But "for the life of me" I can't seem to find a howto on getting the power button to hibernate this thing - and it's headless, so I've been ssh'ing in and "halt"ing it. I'm going to look elsewhere, and if I find anything helpful I'll post it here btw.

TIA for any tips :D

Jim

---

### Post by cookies on 2007-07-01
> **UJoe4 said:**
> Thanks, I'm running Kubuntu 7.04 Feisty Fawn. The "Power Manager" (that you get to by clicking the battery icon at the bottom of the screen) doesn't have it, and I couldn't find anything in System Settings either.

For Gnome users this option does seem to be in the "Power Management" section (found a picture here: [http://spidertools.com/ub_pow3.png]("http://spidertools.com/ub_pow3.png")), but what I'm looking for is the equivalent in KDE.

Or alternatively just how I could modify that /usr/bin/dcop line to hibernate automatically rather than displaying a menu.

I don't have a Laptop, but K Menu > System Settings, And in there is > Power Control > Laptop Battery, which has options.

---

### Post by UJoe4 on 2007-07-02
> **cookies said:**
> I don't have a Laptop, but K Menu > System Settings, And in there is > Power Control > Laptop Battery, which has options.
Strange, I don't have that...

"System Settings > General" is divided into:
- Personal (4 options)
- Look & Feel (5 options)
- Computer Administration (6 options)
- Network & Connectivity (3 options)

"System Settings > Advanced" is divided into:
- System Administration (4 options)
- Advanced User Settings (4 options)

And none of those options contain anything like Power Control or Battery (I've gone through them carefully). The closest are the various shutdown options in "Login Manager" and "Session Manager", neither of which include power-button options.

As I mentioned before, I could just change it in /etc/acpi/powerbtn.sh, if only I knew what it is exactly that KDE does when you click on Hibernate in the GUI. It doesn't just run /etc/acpi/hibernate.sh: it somehow logs you out or locks your session before running it. 

As a test, if you temporarily replace hibernate.sh (ie, the suspend and resume procedures) with a blank file and then choose Hibernate via the K Menu, the screen will go black and nothing further will happen (it's calling the empty script). Then, any mouse movement will bring back the login prompt, and you're back where you were without the computer having powered down.

KDE is blanking the screen, logging you out, and then calling hibernate.sh... so I just need to know what commands to run to duplicate the "blanking the screen and logging you out" part.

---

### Post by phoenixjim on 2007-07-02
Ok - I don't have time to check this out right now but here's a link that may provide some help:

[http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/](http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/)

Specifically for Fiesty.

Still looking...

Jim

---

### Post by t-dome on 2007-07-08
Hi,

you have to install the package "kpowersave", which appears as an icon in the system tray (see the attached "pm-icon.jpg").
I have a desktop system so this was not installed by default on my PC.

Then, right click the icon and select "Configure KPowersave". On my PC there is the option "Save to Disk" (see "pm-kpowersave.jpg).

---

### Post by phoenixjim on 2007-07-08
This looks to be the option for kde users (kpowersave) when it works - I'm wondering though what a server installation would require to get it working... no gui, only ssh access from another machine on the same subnet.

Thanks though :)

---

### Post by UJoe4 on 2007-07-09
t-dome: Thanks, that's exactly what I was looking for! The power manager that ships by default with Kubuntu (kde-guidance-powermanager) doesn't include that option, so it's good to know there's a KDE program that does. The GNOME power manager includes it.

I've switched pretty much full-time to Xfce now anyway, where I'm not running a power manager at all (using the acpi scripts instead), but it's still good to know.

phoenixjim: I don't know how server setups work, but if Ubuntu Server works the way regular Ubuntu does, the power button will call /etc/acpi/powerbtn.sh. That script goes through several options in turn:

1) If it's already in the middle of resuming (acpi flag set), then do nothing and exit.

2) Otherwise, if gnome-power-manager, kpowersave, or klaptopdaemon are running, then do nothing and exit so that they can handle it.

3) Otherwise, if KDE is running but without kpowersave or klaptopdaemon, bring up the shutdown menu. (This was my original situation: Running KDE without either of those two applications.)

4) Otherwise, shutdown (/sbin/shutdown -h now). I changed this line to "/etc/acpi/hibernate.sh" to make it hibernate instead of shutdown in Xubuntu when no power manager is running.

So if Ubuntu Server works the same way, and you're not running KDE or gnome-power-manager (which I assume you're not), you could try doing what I did. Comment out the last line of that script and replace it with a call to /etc/acpi/hibernate.sh.

If that doesn't work, I'm not sure. But you could have a look around in /etc/acpi to see if there's anything else that looks promising.

---

### Post by phoenixjim on 2007-07-09
UJoe4 - Thanks - very helpful info there - I'm reinstalling ubuntu now (well, kubuntu). Getting more space free on the fast big drive :)

This info should do the trick. I'll check back after the install to let everyone know.

Edit: On kubuntu fiesty, with current updates, tried out kpowersave. Set power button press to suspend to disk, and voila - it seemed to suspend perfectly. Unfortunately, once it resumed to desktop it instantly suspended again - and again.

Had to edit the boot line and add noresume temporarily to get in and stop the cycle. I decided (for my purposes) that just shutdown would be fine, since a full boot sequence takes only 45 seconds anyway.

If asked I can try to provide any info desired to look into why it would spontaneously suspend upon resume...

---

### Post by shadwstalkr on 2007-07-18
The same thing happened to me with kpowersave.  I managed to break the cycle by quickly killing kpowersave before it suspended a third time.

---

### Post by shadwstalkr on 2007-07-18
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/kpowersave/+bug/126707](https://bugs.launchpad.net/ubuntu/+source/kpowersave/+bug/126707) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I filed a bug report for the continuous suspend problem.

---

### Post by UJoe4 on 2007-07-18
> In Button Events in kpowersave's configuration, set the power button to suspend to disk. When I push the power button, the system suspends. When I turn the computer back on, the system comes back to the log in screen. After unlocking the screen, the system responds for about 30 seconds, then immediately suspends again. This repeats until "noresume" is added to the boot parameters, or kpowersave is killed while the system is responding.
Thanks for filing this. I don't have KDE set up anymore, but I noticed this too when I did. Two things about it that I remember:

1) I couldn't figure out how to disable the default Kubuntu power manager (kde-guidance), and was unable to uninstall it because a lot of other KDE services seemed to depend on it. So that means that when I experienced that continous-hibernation behavior I had two power managers running simultaneously: kde-guidance and kpowersave. Could someone who's managed to disable or uninstall kde-guidance check whether this bug still happens with only kpowersave running?

2) I found what was causing the delay before hibernating again (during which the system behaved normally), and was able to change it to however long I wanted. But I couldn't figure out how to disable the re-hibernation entirely. I *think* it was the "sleep 10" in "/etc/acpi/resume.d/98-acpi-unlock.sh". Could someone test this: Change it to "sleep 100" or whatever and see whether it gives you the extra time?

When I was playing around with this I wasn't able to figure out how to fix it, and now I no longer have KDE... But I wonder whether adding something like "killall kpowersave && kpowersave" right before the "sleep 10" line in that script would work? (And you might need to change the XAuthorization line in your sudoers file to be able to re-open kpowersave like that.) Could someone try and see whether that works?

---

