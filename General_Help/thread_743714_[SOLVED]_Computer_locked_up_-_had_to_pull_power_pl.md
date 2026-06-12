---
title: "[SOLVED] Computer locked up - had to pull power plug - is this bad?"
date: 2008-04-02
forum: General Help
---

### Post by Mike Brennan on 2008-04-02
I'm new to Ubuntu. I made the switch from Windows a few weeks ago. There are definite rough edges, but overall I like it.

However, there have been a few occasions, so far, where I've had to do a hard reboot. On two of those occasions, even pressing the power button on my PC didn't work (it's a Dell with Ubuntu pre-installed). I had to literally unplug the power cord and plug it back in.

Is that bad? On Windows after doing something like this I would need to use ScanDisk afterwards to fix any file system corruption. Do I need to do anything like that on Ubuntu?

If it matters, I have just one partition on my filesystem, and it is an ext3 filesystem.

One of those occasions I was trying to awaken the computer after suspending it and the screen simply remained black; I never got the screen asking for my password. Usually suspending works fine, but it is inconsistent; sometimes it has problems. Is there a way to deal with this without having to do a hard reboot?

The other time I was using an RSS Reader and I think I tried dragging a link from a page to the desktop (or something like that -- I don't remember for sure). Gnome completely locked up on me. I could not access any menus, could not close any windows, nothing. I tried pressing Ctrl-Alt-Del to see if that works as on Windows, but apparently not. So again, is there a graceful way of dealing with this (which has only happened once, so far) without having to unplug the power and plug it back in?

Thanks.

---

### Post by sports fan Matt on 2008-04-02
Welcome to Ubuntu-:)

AS a person who has repaired computers for about 4 years unless im wrong, literally pulling the plug isnt a good thing...Was the machine spinning the hard drive at all when you pulled the plug or the fan spinning before you unpluggged it--(What i mean is sometimes it can come back to life)

Hibernation depending on a few things could be problematic at best.  There are numrous threads where hibrnation simply doesnt work (I suffer from this)

I'm sorry I cant be more help, maybe others will help more

---

### Post by NT4usB on 2008-04-02
Is your keyboard and mouse completely dead? Numlock light or caplock light doesn't go on and off when you press the buttons?
If they still work, Ctrl+Alt+F1 to get to a terminal, log in there and ```
sudo shutdown now -r
``` to restart or ```
 sudo shutdown now -h
``` to turn it off.
If the keyboard is dead, try unplugging and plugging into another port (USB?)
Hold the power button in for six seconds *should* power off.
I get hard lockups (no keyboard/mouse) occasionally and (so far) hard booting hasn't broken anything.
The filesystem will automatically run a check every X number of boots (25?) unless you've disabled it.
You can force a check by```
sudo shutdown now -r -F
``` iirc... might want to read the man page on the -F command though. Not sure about that one...

---

### Post by sujoy on 2008-04-03
well i never needed to "unplug" to shutdown the PC, boy thats too rough a procedure to follow

---

### Post by danwood76 on 2008-04-03
Pressing ctrl + alt + del initiates a restart but it does the normal shutdown process, so if your system is running it may take a few minutes to restart.
Normally doing this will make the hard drive light flash so you know if its doing something.

Hibernation and suspend has been an issue in the linux kernel for a while, fortunatly the latest kernel version seems to have some bug fixes for this although ubuntu wont have it for another 6 months.

Out of interest are you the Mike Brennan that used to teach in Sutton Benger primary school?

---

### Post by stefangr1 on 2008-04-03
If your system is completely frozen (so that Ctrl-Alt-backspace or Ctrl-Alt-F1 don't work) the first thing you should do is try to restart the computer using the build in system control functions, that are on a lower level in the kernel.

You should use the following key combinations to do this, leaving some time between each step.

Alt-SysRq-R
Alt-SysRq-E
Alt-SysRq-I
Alt-SysRq-S
Alt-SysRq-U
Alt-SysRq-B

This should stop all running processes, unmount the filesystems, and finally reboot the system.

If it doesn't work, try shutting down the system by pressing the on/off key for 5-10 seconds. I think the chance that pulling the plug out breaks your system is not really that large, however, hard freezes are an indication for a serious problem. Maybe you should make use of your warrenty.

---

### Post by ed-koala on 2008-04-03
I have had to pull the plug on my system a number of times when my DVD drive was going bad.  It certainly isn't recommended doing that, but it never broke anything on my PC.   That being said, you should always wait until everything stops spinning and the PC is "dead" before plugging the power back in, should you ever do it again.

---

### Post by niteshifter on 2008-04-03
To amplify on stefang1's post:

You may have to use Ctl + Alt + SysRq + letter_key (yes, that's a finger-breaking 4 key combo). I have to (Dell 1420n / 7.10)

What these do and when and why you should pause:

Key
R - Turns of keyboard translation. 

E - Sends a terminate (SIGTERM) signal to all processes (except init). Pause a few seconds here, and keep an eye on your hard drive activity lamp. Proceed when it goes out for 2 - 3 seconds.

I - Sends a kill (SIGKILL) signal to all processes (except init). Pause and watch HD activity like above.

S - Attempts to sync (complete file writes). Watch for HD activity to cease for 10 - 15 seconds here.

U - Attempts to remount all mounted filesystems as read-only (to enable shutdown scripting). Watch like "S" above.

B - Reboot.  O here will turn power off.

---

### Post by davidpbrown on 2008-04-03
Ctrl+Alt+Backspace to restart only the X helps sometimes (not the same as Ctrl+Alt+Del).. not sure if it would work resuming from suspend though.

---

### Post by Mike Brennan on 2008-04-03
> **danwood76 said:**
> Pressing ctrl + alt + del initiates a restart but it does the normal shutdown process, so if your system is running it may take a few minutes to restart.
Normally doing this will make the hard drive light flash so you know if its doing something.

How about that. I just tried ctrl + alt + del now and it brought up the shutdown window (or whatever you call it -- the one that let's you select whether you want to log off, shutdown, suspend, etc.). That didn't work at all in the 2 instances when it completely locked up. It wouldn't respond to keyboard events then.

> **danwood76 said:**
> Out of interest are you the Mike Brennan that used to teach in Sutton Benger primary school?

No, sorry. Mike Brennan is actually a pretty common name. I get asked quite often "Are you the Mike Brennan that...". But no, I'm not a teacher.

Thanks.

---

### Post by Mike Brennan on 2008-04-03
> **sox fan Matt said:**
> Welcome to Ubuntu-:)

AS a person who has repaired computers for about 4 years unless im wrong, literally pulling the plug isnt a good thing...Was the machine spinning the hard drive at all when you pulled the plug or the fan spinning before you unpluggged it--(What i mean is sometimes it can come back to life)

Hibernation depending on a few things could be problematic at best.  There are numrous threads where hibrnation simply doesnt work (I suffer from this)

I'm sorry I cant be more help, maybe others will help more

Actually, the problem happened when trying to wake up the machine after suspending, not hibernating. Hibernating doesn't work at all on my machine. Suspending usually works fine, although I sometimes get  a message that it didn't suspend fine (even though everything seems OK, as far as I can tell). In the one case where it didn't wake up, I did here the fan startup and the disk start spinning and my monitor even switched from sleep mode. But the screen remained black. I waited for a bit to see if the screen would show something but it never did. It just remained black. Fortunately, that only happened once, but I didn't know how to handle it gracefully; didn't know what else to do but pull the plug and plug it back in again.

---

### Post by Mike Brennan on 2008-04-03
> **NT4usB said:**
> Is your keyboard and mouse completely dead? Numlock light or caplock light doesn't go on and off when you press the buttons?
If they still work, Ctrl+Alt+F1 to get to a terminal, log in there and ```
sudo shutdown now -r
``` to restart or ```
 sudo shutdown now -h
``` to turn it off.
If the keyboard is dead, try unplugging and plugging into another port (USB?)
Hold the power button in for six seconds *should* power off.
I get hard lockups (no keyboard/mouse) occasionally and (so far) hard booting hasn't broken anything.
The filesystem will automatically run a check every X number of boots (25?) unless you've disabled it.
You can force a check by```
sudo shutdown now -r -F
``` iirc... might want to read the man page on the -F command though. Not sure about that one...

Cool. I didn't know about that Ctrl+Alt+F1 trick. Unfortunately I just tried out of curiosity while I was reading your post and couldn't figure out how to get back out of that terminal mode. Is there a way to do that? Anyway, I'll keep that in mind for the future. One of the times this happened to me I suspect it was just Gnome that was locked up. I couldn't access any menus and nothing seemed to work, but perhaps that Ctrl+Alt+F1 trick would have worked.

When I tried it just now, I went ahead and did a "sudo shutdown -r now" and when it restarted it said I was restarting for the 26th time and forced a scan of the disk. (How's that for a coincidence; when I rebooted while reading your post, it just happened to be the 26th time I've rebooted.)

Thanks.

---

### Post by Mike Brennan on 2008-04-03
> **stefangr1 said:**
> If your system is completely frozen (so that Ctrl-Alt-backspace or Ctrl-Alt-F1 don't work) the first thing you should do is try to restart the computer using the build in system control functions, that are on a lower level in the kernel.

You should use the following key combinations to do this, leaving some time between each step.

Alt-SysRq-R
Alt-SysRq-E
Alt-SysRq-I
Alt-SysRq-S
Alt-SysRq-U
Alt-SysRq-B

This should stop all running processes, unmount the filesystems, and finally reboot the system.

If it doesn't work, try shutting down the system by pressing the on/off key for 5-10 seconds. I think the chance that pulling the plug out breaks your system is not really that large, however, hard freezes are an indication for a serious problem. Maybe you should make use of your warrenty.

Cool. Thanks. I'm going to print out this info and keep the list handy in case this happens again.

---

### Post by Mike Brennan on 2008-04-03
> **niteshifter said:**
> To amplify on stefang1's post:

You may have to use Ctl + Alt + SysRq + letter_key (yes, that's a finger-breaking 4 key combo). I have to (Dell 1420n / 7.10)

What these do and when and why you should pause:

Key
R - Turns of keyboard translation. 

E - Sends a terminate (SIGTERM) signal to all processes (except init). Pause a few seconds here, and keep an eye on your hard drive activity lamp. Proceed when it goes out for 2 - 3 seconds.

I - Sends a kill (SIGKILL) signal to all processes (except init). Pause and watch HD activity like above.

S - Attempts to sync (complete file writes). Watch for HD activity to cease for 10 - 15 seconds here.

U - Attempts to remount all mounted filesystems as read-only (to enable shutdown scripting). Watch like "S" above.

B - Reboot.  O here will turn power off.

Thanks for the info. This is very helpful.

---

### Post by Mike Brennan on 2008-04-03
> **davidpbrown said:**
> Ctrl+Alt+Backspace to restart only the X helps sometimes (not the same as Ctrl+Alt+Del).. not sure if it would work resuming from suspend though.

Great tip. Thanks. Perhaps it won't work resuming from suspend, but perhaps it would have worked the other time. I appreciate it.

---

### Post by danwood76 on 2008-04-03
Ctrl + Alt + F7 will get you back from the terminal.
You have 6 terminals (F1 - F6)  plus a graphical interface in ubuntu (F7). all of which you can log into.

---

### Post by Mike Brennan on 2008-04-03
> **danwood76 said:**
> Ctrl + Alt + F7 will get you back from the terminal.
You have 6 terminals (F1 - F6)  plus a graphical interface in ubuntu (F7). all of which you can log into.

Thanks!

---

