---
title: "XGL/Compiz.... bad timing?"
date: 2006-09-08
forum: General Help
---

### Post by sLLiK on 2006-09-08
I'll preface this post with the admission that I'm barely above noob status with regards to Linux, though I do try to do my homework.  I've been struggling with getting my system to run XGL\Compiz on my machine at work for a while now off and on, with breaks in between for the sake of my work productivity.  I figured once I got it running once here, I'd just remove the repos and stop updating, but I have yet to get it initially running.  I've looked through multiple how-to's, followed some of them, and gotten nowhere.  Before I go further, be assured that I HAVE gotten it working properly before on other systems (at home), so I'm no stranger to the process.  I would guess that the root cause of my problem is either a) the combination of hardware I'm currently attempting to utilize, or b) bad timing, with all the various myriad changes to the code that have happened lately.

Most recently, I've tried to go back to basics.  I've removed all signs of anything else I've tried doing according to prior how-to's, and I'm now back to completely removing all prior packages and reinstalling them from scratch.  Since this is my work machine, I've got backups of all my needed data, but I'm not overly inclined to blow the OS install away and start from scratch unless I am forced to.  The /usr/bin/compiz-start that the latest updates create for me only manage to kick me back out to the login screen.  I've tried doing a manual recreation of the methods using an xnest-type method, and I get hit or miss results but cgwd almost always crashes after a minute or two.  Here's how far I've gotten:

[INDENT]> Xgl :1 -ac -accel glx:pbuffer -accel xv -fp /usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,
/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,
/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,
/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType &[/INDENT]

...spawns an Xgl environment on screen 1 (ie same monitor, just in a window)

[INDENT]> DISPLAY=:1 cgwd &[/INDENT]

....instantiates cgwd via screen 1.  This seems to work like 30% of the time.

[INDENT]> LD_LIBRARY_PATH=/usr/lib/opengl/xorg-x11/lib/ DISPLAY=:1 compiz --replace dbus &[/INDENT]

...launches compiz accordingly.

[INDENT]> DISPLAY=:1 xterm[/INDENT]

...spawns an xterm window, wobbly effects, themed and all.  If I can get this working (though not very reliably), then why does /usr/bin/compiz-start throw me back to the gdm greeter?  My Xorg logs in /var/log give me absolutely nothing to go on.  I have DRI disabled, I'm running at 24-bit color depth, and I have pixmap support.  The nohup.out file that gets created in my home dir truthfully doesn't give me much to go on either:

[INDENT]"(cgwd:12929): Gtk-WARNING **: cannot open display:  
The application 'cgwd' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application."[/INDENT]

I originally had intentions of making this work with TwinView, but I've scaled back and commented out the portions in my xorg.conf file that enabled it in the hopes of getting Xgl\Compiz working on one monitor.  Any suggestions?

I noticed in one guide I found on the net that it mentioned I shouldn't have the symlink for libGL.so.1 pointed to the nvidia proprietary driver libGL.so.1.0.8762 because it breaks XGL\Compiz, but I know of two other systems I've examined recently that are working just fine using that link.  The same guide I mention also says that you can fix the problem by changing the symlink so that it points to libGL.so.1.2, but I have no such file and can't seem to find it.  For reference, I'm using a NVIDIA Corporation NV17 [GeForce4 MX 440] inside a Dell Precision 360, with a Dell 2005FPW monitor.  I know for a fact that (at least a few weeks ago) the MX 440 card I am trying to use worked with XGL in another system without problems, so I'm in a quandry over why this is now so difficult to get working properly.

Update:  Actually, interestingly enough, in the process of going back over my efforts and double-checking everything, it seems that something has changed after removing and reloading all the compiz/cgwd packages.  When I do glxinfo, texture_from_pixmap support is no longer present, and "direct rendering: Yes" but I think it used to be (and was required to be) "No" for GLX to work properly.  If I haven't changed my Xorg since I started unloading and reloading everything, why would that change?  I'm including my xorg.conf file as well, for reference (added .txt at the end for the sake of uploading purposes).

---

### Post by Choad on 2006-09-08
could you break up that long directory string? it messes up the formatting of the page and i am not reading that much text having to scroll side to side all the time!

---

### Post by kpkeerthi on 2006-09-08
Please edit your post and make it little readable. Just break that long path name somewhere in the middle... please.

---

### Post by sLLiK on 2006-09-14
Ack, my apologies.  Just now coming back to my post and didn't realize the formatting was making things unreadable.  I've hopefully made the necessary changes.

---

### Post by sLLiK on 2006-09-15
I keep plugging away at it, making little discoveries over time.  My most recent breakthrough is that, despite all the various howtos I've tried to follow, nvidia-glx was not installed (which is a biggie if you want the texture_from_pixmap functionality that is required for Xgl.

Now, I've run into what I think is the last hurdle, but unfortunately it seems to be the one that has the fewest posts/responses when I start searching google for answers.  I can select my Xgl session from the gdm greeter, login, and I get no obvious errors.  but when I invoke the original commands I outlined in my first post and put in either DISPLAY=:0 or DISPLAY=:1, I get errors saying that Xgl could not create a server lock file at /tmp/.X0-lock (or .X1-lock, as applicable).  If I use :2, it works as it originally did.

So that led me to think that display 0 and 1 are both in use.  I figured X was one of them, and Xgl is most likely the other.  Doing ps -ef | grep X gets me:

root     13416 13411  2 18:21 tty8     00:00:35 /usr/bin/X :0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt8
me     14198 14149  0 18:34 ?        00:00:00 [Xgl] <defunct>

...and ps -ef | grep xgl yields:

me     14193 14149  0 18:34 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/startxgl
me     14197     1  0 18:34 ?        00:00:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/startxgl
me     14718 14286  0 18:48 pts/0    00:00:00 grep xgl

I'm more hopeful than before.. but now I'm also more confused than before.  I read somewhere that Xgl needed longer to start, so I reconfigured my gdm conf to wait for 30 instead of 10.... but it gets into a desktop awfully fast, imho.  If that configuration denotes seconds, then Xgl is becoming 'defunct' almost instantly by comparison.  As a last-ditch leap of faith, I simply executed /usr/bin/compiz-start from a command line and it still just kicks me back out to the gdm greeter as it always has.

Any tips/tricks anyone can think of?  Any help is, of course, appreciated.

---

### Post by sLLiK on 2006-09-19
Got ahold of the most recent kernel and nvidia drivers released some time in the past 24 hours with crossed fingers, but still no changes in behavior.  Am I so far out on the bleeding edge that there's nobody to catch me if I fall?  ;p  I'm about to resort to doing a rebuild, but it bugs me that I would need to do that to fix this problem.  Seems to me that this should be fixable without falling back to that method repeatedly.

---

### Post by sLLiK on 2006-09-21
Since I'm mostly just using this post as a single point of reference and nobody is offering up any assistance at this point, I'll outline the final steps of what I did.

Nuked my box, reinstalled Ubuntu, and followed the directions located here to the letter:  [http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit](http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit)

I payed special note to what was said about the specific kernel I should be running, so I made sure to use 686.  Whether this was the silver bullet that fixed things or was just coincidence and the root cause was a messy box because of all the various (disparate) attempts made to get Xgl running, I can't say for sure.  I thought I was pretty thorough, but there's always the chance I missed it or something else was going on behind the scenes that I wasn't aware of.

To make a long story slightly shorter, Xgl is now working on one screen.  I'm to the point where when I try to make use of nvidia-xconfig to get Xgl and Twinview working together, it causes the dreaded :93 error, but switching back to a saved xorg.conf lets me run Xgl again on a single screen.  So I'm down to (hopefully) just needing a proper xorg.conf to make TwinView and Xgl get along.  Anyone have a winning combination out there that I can learn from?

---

