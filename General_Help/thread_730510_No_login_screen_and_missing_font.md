---
title: "No login screen and missing font"
date: 2008-03-20
forum: General Help
---

### Post by Zatarhi on 2008-03-20
Hi all,
	First of all, I'd like to start by thanking this community - this is the first time I've posted, but I've found the info, help, and tips here to be totally indispensible.
	Long time listener, first time caller - how cliche!

Anyhow, I have my first Ubuntu related problem that's totally stumping me.

Everything's run great for the most part until yesterday.  I was having issues printing to both my PDF printer and the networked HP Deskjet I have here.  Sending  a test page from the printer control panel just popped up a message that went something along the lines of "Test page added to queue at number x". The queue listed no jobs.  So, I uninstalled both printers and restarted and that's where the fun began, and where I need some assistance.

The computer boots up the the point of the login screen - the screen initializes and I get a split second view of the spinning wait icon, and then a graphical error box presented against a black background.

Now normally I would be able to figure things out from the error box message, but the normal font has been substituted with empty rectangular boxes - the kind you see when your computer tries to render a font that it does not have.

The box (well, boxes - more on that in a moment) has(have) the round red warning icon in the top left, the one with the white bar through the middle.  The box has a clickable button that I assume usually reads "OK", as it has two boxes.

Clicking on the faux OK box brings up another window with fontless contents, sometimes with another screen reinit.  Doing this enough times in a row yields the message "The display server has been shut down about six times in the last 90 seconds.  It is likely that something bad is going on.  Waiting for 2 minutes before trying again on display :0".

Dropping down to a command prompt and trying anything with restarting the X server for any user yields the following messages:

"stoXlib: connection to ":0.0" refused by server"
"Xlib: Invalid MIT-MAGIC-COOKIE-1 key"
"giving up"
"xinit: unable to connect to X server"
"xinit: No such process (errno 3):Server error"

From looking around, I understand that this is an authorization problem with the X server (and it's in use and running) - unfortunately, I can't seem to shut it down (or haven't used the right command to).

So...restart in recovery mode.

In recovery mode, there are no X authorization errors - X can be started by any user, using startx.  Progress.  I can access my desktop, but no network and there still seem to be some authorization problems - accessing anything requiring root access from the desktop fails with the message "The configuration could not be loaded.  You are not allowed to access the system configuration".

Either I have a borked config file, or...
I have a feeling these will go away once the following problem is solved and the computer's boot process is again normal:

If I run /etc/init.d/gdm start, with any user, I get the initial problem (unreadable error boxes).  It happens when it's the first thing you do once logged in, and also if you drop down to the command prompt from an X session that's been started manually from the command line (as that's all that can be done right now).

So I think I've narrowed it down to that particular part of the boot process - everything boots perfectly until the login window is supposed to appear.  If this step is skipped by booting into runlevel 1 and then starting X from there, it's bypassed and most things work normally except for what was noted previously.

Narrowing it down further, if you start X and then drop back down, I have one solitary error message:

"Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!"

And indeed, there is no cyrillic folder in that directory.  I have the sneaking suspicion that the error messages use the cyrillic font...

I also can't access my network/the internet and thus can't apt-get anything, including X fonts.

I ran the command to refresh gdm and got the following message:

"The generated cache was invalid".

Any help would be appreciated, and I will post any more info that is needed.  I'm still learning my way around, so I'm not sure what files in specific to examine, so just ask.  
The one exception here is the xorg.conf file - I have both copied the known good original and run dpkg-reconfigure xserver-xorg and tried using vesa drivers.  I've also commented out the wacom stuff.

I also can't access my network/the internet and thus can't apt-get anything, including X fonts.

---

### Post by Zatarhi on 2008-03-21
...anyone? :sad:

---

### Post by Zatarhi on 2008-03-23
Slowly tracking down the source of the problem...
dbus is not running on startup.  In addition (and I think due to this as well) HAL is not starting, either.  I'm thinking because none of this is running (I can open the system services panel, but no changes are sticking and they're all off by default) GDM will not run right either (on startup or at all).

Am I going in the right direction?  I'm still trying to work this out...and I could still use some help...;);)

Thanks!

---

### Post by Zatarhi on 2008-04-01
...can anyone help me from a week's work of poking around or a purchase from Canonical?
I run a computer business, and I had switched to Ubuntu and loved it - I've been experimenting with Linux since 1996, and despite the fact that I loved the idea and the mentality, it never quite did it for me.  This is the first time that a Linux distro has really hit the sweet spot for me, but now it's turning a bit sour...I'm not a fly by night tech, I pride myself on knowing my stuff and using that knowledge to help myself and my clients but I'm soaking up info as fast as I can here and nothing seems to work out this problem.
It's a bit frustrating - a month after I totally embrace Ubuntu and switch my business apps over and get Virtualbox running XP with Agendus and my Zodiac (which doesn't have Linux drivers...d'oh)...a month after I evangelize this system to everyone I know, it fails for no reason whatsoever.  Once I know this system inside and out I'll help anyone I can, as I usually do - all I ask is some help with this.  Anyone?

I'm tired of booting into XP and not having Agendus here to sync my Zodiac to...I'm doing SD card backups every day for insurance against catastrophe here...I miss booting into Ubuntu.  

My confidence in this OS and support is a bit shaken too.  XP isn't the greatest, but it rarely fails for no apparent reason - there's always a cause.  Not only that, I can do a repair install if all else fails.  That would be great in this situation!  I dislike MS a great deal, I always have as I grew up with alternative computers and their OS's (Atari) and I know what could have been and what should be now.  Ubuntu was that to me - something, finally, that was just right - efficient, user friendly, and flexible.

...however, a failure stemming somehow from uninstalling (built-in!) print drivers is akin to your car not starting because you took the spare tire out of the trunk.  It's both mildly nonsensical and frustrating!

Please help - I will learn from this one way or another, but I would like to learn how to service and like Ubuntu, instead of learning how to walk the beaten path (MS) a bit further.  Thanks...

---

### Post by SyncMaster on 2008-04-17
Hi Zatarhi

Your post could be mine - I am sorry I can not help you. I have the same problem. I use Ubuntu since 5.04, and now I am stuck. Although I have a second machine and I can ssh to the failed pc. But this gave me not many clues. 
Did you got it to work finally?

Regards
Rainer

---

### Post by Zatarhi on 2008-04-22
Nope, I'm still plugging away at it, as I've been pretty much ignored here ;).

I think I'm making progress, and when I do manage to straighten it out I'll post back so I can help you out.  I figure instead of complaining about the lack of any help here (not even an "I can't help you"), I might as well try to contribute so someone else doesn't have that same experience.

Anyone else listening?

---

### Post by Zatarhi on 2008-04-22
Just re-read everything, as I couldn't quite remember where I had left off when I gave up watching my post for some aid.

I can start dbus by hand, can manipulate services, get online, start x, and so on - basically get things going the way they were, almost.  And, all by hand.  Can't get her to go automatically - GDM 's still borking up on startup with the fontless error message.

I had to abandon efforts for a bit as I was too busy working to spend time poking around - I needed something that was at least functional so I had to fall back to XP on my other hard drive.

I'm reviewing all of my notes and bringing myself back up to speed on my problem as we speak - I'm pretty sure I'm close to figuring it out (and have narrowed it down to a handful of things), but it will still probably be a bit.  I'll let ya know.

---

### Post by Zatarhi on 2008-04-29
Well, I've tracked down the source of the problem.

hal-cups-utils.  Originally, I changed my printer setup, restarted, and all hell broke loose.  Now, hal-cups-utils cannot be manipulated (reinstalled, removed, used, etc).

I've managed to upgrade the whole system to 8.04 via CD (and then some network tomfoolery) - hoped it would help, but it didn't.  At least things aren't worse.

Getting there.  At this point it would be easier to start the &^&*^*&^ over, but I'm too far in and I'm damn well going to use this as a learning opportunity.

---

### Post by Zatarhi on 2008-04-29
Alright, so apparent chain of events:

hal-cups-utils breaks
hald does not load
weird, wild stuff happens.

The hal-cups-utils package is TOTALLY BROKEN.  I cannot seem to figure out how to reinstall it, as any apt-get operation relating to it (reinstall, remove, force install, etc.) yields something similar to the following:
$ sudo aptitude reinstall hal-cups-utils
[sudo] password for (username): 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

running "dpkg --configure -a" does not work - it spits out another message to run dpkg --configure -a!

running "sudo dpkg --configure -a && sudo apt-get -f install" does not work, either, AS IT TRIES TO START HALD FIRST.  Obviously, it won't run when hal-cups-utils is broken.

At this point, any kind of operation I've tried either tells me to run dpkg --configure -a, or tries to start hald.  Vicious circle.

On the bright side, I've got enough running to be posting this from the broken Ubuntu installation.

Can anyone lend a hand?  Thanks.

EDIT:

dpkg: dependency problems prevent configuration of hal-cups-utils:
 hal-cups-utils depends on hal; however:
  Package hal is not configured yet.
dpkg: error processing hal-cups-utils (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 hal
 hal-cups-utils

---

### Post by Zatarhi on 2008-04-29
I managed to purge hal-cups-utils.
HAL still won't start.

Now, when trying to start hald (verbose) I get the following:

# hald --daemon=no --verbose=yes
03:55:34.945 [I] hald.c:669: hal 0.5.11rc2
03:55:34.945 [I] hald.c:734: Will not daemonize
03:55:34.945 [I] hald_dbus.c:5381: local server is listening at unix:abstract=/var/run/hald/dbus-owQjdokkam,guid=68aee8d27c72ceca481e0f9d4816d476
03:55:34.948 [E] ck-tracker.c:367: Error doing GetSeats on ConsoleKit: org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.ConsoleKit was not provided by any .service files
03:55:34.948 [E] ck-tracker.c:792: Could not get seats and sessions
03:55:34.948 [W] hald_dbus.c:5806: Could not initialize seats and sessions from ConsoleKit
Runner started - allowed paths are '/usr/lib/hal:/usr/lib/hal/scripts:/usr/bin'
03:55:34.951 [I] hald_runner.c:301: Runner has pid 9734
03:55:34.951 [I] hald_runner.c:182: runner connection is 0x80a7368
03:55:34.951 [W] osspec.c:373: Unable to open /proc/mdstat: No such file or directory

** (process:9733): WARNING **: Failed to add monitor on '/usr/share/hal/fdi/preprobe': Permission denied

** (process:9733): WARNING **: Failed to add monitor on '/usr/share/hal/fdi/information': Permission denied

** (process:9733): WARNING **: Failed to add monitor on '/usr/share/hal/fdi/policy': Permission denied
03:55:34.952 [I] mmap_cache.c:279: cache mtime is 1209452958
Error binding udev_event socket: Address already in use

Any ideas?

---

### Post by Zatarhi on 2008-04-29
Bump

---

