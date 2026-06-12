---
title: "Starting X"
date: 2004-11-20
forum: General Help
---

### Post by Jeconais on 2004-11-20
I've been merrily following tutorials on this board, and have everything set up wonderfully - not least the latest firefox and video stuff.

However, I rebooted last night, and when it came to this morning, GDM would not start properly.  It gives me a message saying that there already seems to be an X server on :7, and do I want to either restart it, or chose another run level.

Either option fails, and so far, all I've been able to do is drop to run level one, use kill to destroy an X Processes, and use startx to well, start x.  On start, the ubutu background is not shown, and is replaced with a series of black and white horizontal lines.

Any idea how I can find out what's happening... and stop it?

Cheers,

J

---

### Post by ynef on 2004-11-20
The "is replaced with a series of black and white horizontal lines" part doesn't surprise me, since you (probably) don't have a .xinitrc file in your home directory -- it's the file that tells the system what program(s) you want to run when you start X. Start an editor (if you're not used to vi, then I suggest nano) and write the following two lines and save the file as ~/.xinitrc :
xterm &
gnome-session

I threw that xterm in there just because it gives you the power to do anything, if gnome-session would fail.

Now, as for gdm being broke, we'll need some more info on exactly what you've done -- if you've installed any non-Ubuntu packages, etc. What is the exact error message? What programs are started in your default runlevel?

---

### Post by Jeconais on 2004-11-20
Thanks for the ideas... 

I created a .xinitrc as you suggested, but it didn't help - another installation of Ubuntu I have on a seperate harddrive doesn't have a .xinitrc, and that one is completely clean.  

What appears to be happening, as it that it tries to start X, I get the cursor change to the waiting signal for maybe a second, before the screen goes blank, then black, and then to a "whiptail" yes/no screen.  and the whiptail command it's using is /usr/lib/gdmopen -l /bin/sh -c /usr/bin/whiptail

It then locks itself into a loop, of either failing to start X properly on a different run level, or failing to restart on that level.

I presumed that the problem was with GDM as when I startx, I'm logged in already, and it works (although with the background problem mentioned above) - although that might no be the problem - but it down to me being a relative linux newbie.

I'm running a clean install, with firefox upgraded through hoary to version 1 (instructions in the "How to" forum), mplayer as well as mplayer plugin, and the k7 standard kernel.

The only thing I can think of is somehow the upgrading of mozilla, which did upgrade libpng, has caused this - although that doesn't make sense to me.

---

### Post by kazpox on 2004-11-20
Hi,
I have the same problem with gdm after upgrading firefox.
I installed the following packages:

libglib2.0-0_2.5.6-0ubuntu1_i386.deb
libgtk2.0-0_2.5.5-0ubuntu2_i386.deb
libgtk2.0-bin_2.5.5-0ubuntu2_i386.deb
libgtk2.0-common_2.5.5-0ubuntu2_all.deb
mozilla-firefox_1.0-2ubuntu3_i386.deb

And after reboot I get the errors as described above.

The problem seems to be that two instances of XFree86 is started. When I kill all X process and do a startx, everything works fine though.

---

### Post by Jeconais on 2004-11-20
Thanks, now I know what caused it, I can revert to a previous version and upgrade firefox manually.

---

### Post by kazpox on 2004-11-20
[QUOTE=Jeconais]Thanks, now I know what caused it, I can revert to a previous version and upgrade firefox manually.[/QUOTE]

OK. If you come up with a working solution, please post it here.

---

### Post by dook on 2004-11-21
I am also having the same problem after upgrading firefox and the libgtk packages.  Is there a way I can just stop gdm from running at boot time?  I might rather that anyway :0

---

### Post by ynef on 2004-11-21
[QUOTE=dook]I am also having the same problem after upgrading firefox and the libgtk packages.  Is there a way I can just stop gdm from running at boot time?  I might rather that anyway :0[/QUOTE]
 Sure -- see this other thread: [http://www.ubuntuforums.org/showthread.php?t=5380](http://www.ubuntuforums.org/showthread.php?t=5380)

---

### Post by Swab on 2004-11-21
OK, exactly the same problem here after upgrading Firefox, will removing firefox and reverting to the Warty version fix the problem?

Edit: Can't start Synaptic either:

```
Failed to run /usr/sbin/synaptic as user root: Unable to copy the user's Xauthorization file.
```

---

### Post by Arnb on 2004-11-21
I have the same problem.
I understand some X process must be stopped, but don't exactly know what to kill or how to find the process names. Would someone please post the exact commands  for a newbie to follow so I can get Ubuntu working again without the duplicate X process.

TIA
Arn

---

### Post by Razvan on 2004-11-21
it cant be firefox...i have the original mozilla.org version installed in my home...
and it worked till today...i had the new firefox for since it was released...

but it moght be one of the other packages..i remember installing a new version of libpng......dunno

---

### Post by kazpox on 2004-11-21
Well. Still haven't found a solution, so now I'm living without gdm which is just fine.

However, I would like the machine to log my user into X automatically on boot.

This can of course be done without a *dm, I just don't remember how. I had an installation of Morphix Light 0.4? that did it. It would log in the user automatically, and besides that it would start X if this user logged in in virtual terminal 1 (vt1). This would effectively mean that X was started automatically on boot, but if you killed it, you would be able to login in e.g. vt2 without X starting.

Could anyone point out how to do this?
(I think the autologin part must have been in some boot script and the auto start of X was probably in some of the user's own scripts).

_______________________________________

To the guy who wasn't sure how to kill processes:
You can use "top" or "ps -fe | less" to see running processes.
You could do something like this:

killall -9 gdm XFree86

(add any other daemons you would like killed)

---

### Post by Arnb on 2004-11-21
Thanks for those commands. I got back into the descktop envirionment by killing the suggested processes then doing a startx.

---

### Post by jgaynor on 2004-11-24
[QUOTE=Jeconais]

What appears to be happening, as it that it tries to start X, I get the cursor change to the waiting signal for maybe a second, before the screen goes blank, then black, and then to a "whiptail" yes/no screen.  and the whiptail command it's using is /usr/lib/gdmopen -l /bin/sh -c /usr/bin/whiptail

It then locks itself into a loop, of either failing to start X properly on a different run level, or failing to restart on that level.
[/QUOTE]

  I have the SAME problem.  My ability to boot my machine has become intermittent because of it - today I had a series of 6 clean power-downs/power-ups before GDM started correctly.

  Slight difference between our two situations - I dont succesfully reach the whiptail configuration screen unless I try to power down.  That is - GDM starts, I see the throbber and hear the drums - then I switch to a blank console screen with a blinking cursor.  There it will hang forever unless I soft power-down via the power button or send a ctl-alt-del.  Either of those actions begins the 'sending processes the term signal' sequence and I am presented with the whiptail screen for a few seconds.  Specifically, it is the initial Ubuntu configuration dialogue . . .

  Even when my box does manage to boot,  the whiptail process is still running in the background:

**root      3954  0.0  0.3  2504  988 pts/0    S+   21:37   0:00 whiptail --backtitle Ubuntu Configuration --title Ubuntu base**
This line continues with the entire base configuration whiptail placard (Welcome to your new system!! blah blah blah)

This makes me think that whatever 'switch' was supposed to turn off the initial configuration dialogue never got flipped.  Does someone know how to get this out of the initial startup?  Id appreciate it greatly!


**EDIT:**

 YAY!  Solved the problem.  Base-config uses two different inittab files - one during installation (to allow it to start automatically after the CD install) and one for post-install (/etc/inittab.real).  Base-config should, after completing the initial configuration dialgue, replace the pre-install inittab with the post-install inittab.  For whatever reason that never happened during my installation.  The temporary inittab was starting the configuration dialogue along with two tty lines whenever I entered any runlevel between 2 and 5.  I found it by searching for the running process listed below:

/usr/sbin/termwrap /usr/sbin/base-config new

  By replacing my /etc/inittab with my /etc/inittab.real the configuration process stopped respawning.   Hope this can help someone in the future.

---

### Post by andbert on 2004-11-25
Sounds great, but could you show the specific code to be written to fix the problem?
Newbie here, and not quite sure how to perform these actions....

---

### Post by barb3tta on 2005-01-17
[QUOTE=kazpox]
However, I would like the machine to log my user into X automatically on boot.
...
Could anyone point out how to do this?
(I think the autologin part must have been in some boot script and the auto start of X was probably in some of the user's own scripts).
[/QUOTE]

hi!
did you figure out how to do it?
I'm trying to do an automatic login in a "small-ram" ubuntu installation (xdm+icewm).

I found the following:
[http://members.tripod.com/rpragana/short-commands.html](http://members.tripod.com/rpragana/short-commands.html)
> 
rc.local:
echo "Autologin of user <username>"
cd /home/<username>
su - <username>

~/.bash_profile:
if ["`tty`" = "/dev/console" -o "`tty`" = "/dev/tty0"]
then
    startx
fi 

but:
-rc.local doesn't exists, so I tried to add /etc/init.d/autologin and /etc/rc2.d/S99autologin, but it gives me an error about su- (can't remember the exact error).
-another error is "/dev/console: no such file or directory"...

at least i got an autologged terminal. but if I try to "startx" it gives me a bunch of errors...

cheers

---

### Post by kazpox on 2005-01-19
I never got around to find a solution. (I posted a request on the Morphix.org forums, but got no reply. If you would bother to install Morphix Lite, you could probably work out how it works.)
My system broke after an update, so I did  a new install and am back with good old gdm.

However, I *think* the solution lies here:
[http://www.desktop-linux.net/debian-rclocal.htm](http://www.desktop-linux.net/debian-rclocal.htm)

Something like this may work:

Open a root a root terminal:

# nano /etc/init.d/local

Paste the text from your quote:

```

echo "Autologin of user <username>"
cd /home/<username>
su - <username>

~/.bash_profile:
if ["`tty`" = "/dev/console" -o "`tty`" = "/dev/tty0"]
then
startx
fi 

```

...and make it excecutable:
# chmod +x /etc/init.d/local

And see what happens on boot.

---

