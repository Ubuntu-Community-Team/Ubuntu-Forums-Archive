---
title: "Blank screen when XDMCP to VMWare Ubuntu Guest from Windows Xming"
date: 2006-12-26
forum: General Help
---

### Post by jwynia on 2006-12-26
What I'm trying to do:
I'm attempting to connect Xming via XDMCP on Windows XP Pro to an Ubuntu Edgy 6.10 installation that resides in a VMWare virtual machine.

What happens:
I get a login screen, am able to authenticate and even get a warning about starting a second session (there's another session running on the VMWare "monitor"). Then, it sits at a blank background for a bit until eventually a single, borderless window with no markings of any sort appears. I get a text insert cursor in that window and a normal cursor outside of it. However, typing in that window does absolutely nothing.


Here's an SWF screencast of the problem in action:
[http://www.wynia.org/screencasts/XmingToUbuntuProblem/](http://www.wynia.org/screencasts/XmingToUbuntuProblem/)


What I expected to happen:
After the login process, the Gnome "loading" bar would go through the motions and I'd get a normal desktop.

Why I expected that to happen:
Up until a few weeks ago, that's exactly what happened using Cygwin/X. Then, for no apparent reason, Cygwin/X stopped working completely and wouldn't even launch any sort of window, etc. I figured it was a Cygwin problem and have been using VNC ever since. However, I'd much rather use XDMCP to connect to the machine than VNC.

What I've already checked:
The Windows host is not running any sort of firewall. XDMCP is enabled on Ubuntu.

---

### Post by Endolith on 2007-02-10
> **jwynia said:**
> What I'm trying to do:
What happens:
I get a login screen, am able to authenticate and even get a warning about starting a second session (there's another session running on the VMWare "monitor"). Then, it sits at a blank background for a bit until eventually a single, borderless window with no markings of any sort appears. I get a text insert cursor in that window and a normal cursor outside of it. However, typing in that window does absolutely nothing.

This is exactly what happens with me, too.   There's an error box in the upper left corner of the screen, but it only displays as a grey box with an I cursor in the parts where the error message is displayed.

Once it showed its true form (and the background of my desktop appeared - maybe you just have to wait a while?  I'm trying to reproduce right now), and the grey box is an error message saying something about Gnome startup scripts or something.

Failsafe terminal session works...

---

### Post by Endolith on 2007-02-11
I got it to display the error message again.  So first it shows the login screen, then I log in and it says Are you sure you want to log in?  You're already logged in. and you say yes, then it goes to the blank brown screen with the grey rectangle in the upper left hand corner.

However, if you let it sit like that for long enough, something crashes and then it starts to work again, and the grey square turns into an error dialog and a bug report crash thing appears, too.  The system then starts to kind of work the way I would expect.

The error dialog says:
> There was an error starting the GNOME Settings Daemon

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply.  Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.

Is this the same thing you saw?

See attached screenshots.

See also 

[LIST]
[*][http://ubuntuforums.org/showthread.php?p=2141149](http://ubuntuforums.org/showthread.php?p=2141149)
[*][http://ubuntuforums.org/showthread.php?p=2141147](http://ubuntuforums.org/showthread.php?p=2141147)
[/LIST]

---

### Post by jwynia on 2007-02-13
Mine never moved on. I don't remember just how long I let it sit the last time, but I do know that it never changed. 

I ended up using VNC until today, when I got NX working instead, which I like because it's self-contained over SSH, making it easy to connect without a lot of effort.

---

### Post by johnmarshall4 on 2007-02-18
Has anyone figured this out yet? I've spent far too much time trying to get XDMCP login working with Ubuntu 6.10 and XMing. I have been using this setup without problems on my other Linux Distros. What are we missing here?

---

### Post by johnmarshall4 on 2007-02-18
I know you mentioned that your windows firewall was turned off.
Mine was turned on, and I was able to get past this problem by poking some holes for XDMCP in the firewall for local subnet access only:

UDP 177
TCP 6000
TCP 16001

Note: I have not had to do this with other (non ubuntu) distributions running under VmWare.

---

### Post by adam_m on 2007-03-03
It seems to be a XMing problem. Don't use the Clipboard Manager and it works fine.

---

### Post by kemoka on 2007-04-02
Hi!

I am trying to do something similar, without success.
The clipboard tip did not work for me... :(
Maybe there is something slightly different with my setup, I dunno...
So here it is:

1. I use a Windows XP laptop for everyday office work, on this laptop I installed Xming and it works great, I can connect via XDMCP to my (remotely located) Linux application server.

2. In the app server I installed Vmware Player and have some other virtual machines hosted

3. I would like to connect to the Linux app server using Xming (ok, done that!) and then run Vmplayer

4. Problem - the Vmplayer starts, I can see the window resizing like it normally does wile starting a virtual machine, but no outpu at the window... it remains black, and if I drag something over it, it never gets repainted. Just before starting the virtual machine, Vmplayer gives an error about screen/keyboard/mouse mapping.

It seems to me that Vmplayer is unable to hook to the windows laptop display/keyboard/mouse because of Xming... but I have no idea if this is really the problem, or what might be the solution...

Is anyone willing to give it a shot and test this? Ideas anyone=
Thank you for your time! :-)

---

### Post by kemoka on 2007-04-09
Hi!

I found out that this works with VNC.

If I start vncserver on the Linux server, I can connect to it with TightVNC from my Windows laptop and run vmplayer on the Linux server without problems.

I would prefer this working with XDMCP though...

Maybe this is a VMWare problem, not X or Mming?

Thank you!!! :-)

---

### Post by Jahkorp on 2007-04-17
I've been having the same problem using ubuntu edgy, and the latest XMing. I came across this bug-report
[https://launchpad.net/ubuntu/+source/control-center/+bug/61381](https://launchpad.net/ubuntu/+source/control-center/+bug/61381)
and the thing that did the trick for me was disabling ESD under sound preferences. Really odd, but it works :D Hope it works for you too

---

### Post by kemoka on 2007-04-18
Hi,

Thanks for the tip, I'll try it!
I managed to solve the problem another way thanks to a member of the VMWare Forums.
The solution is simple, add the line:
xkeymap.usekeycodeMap = "TRUE"
in the file ~/.vmware/preferences . 
You can even create this directory and file with only this line in /etc/skel/.vmware/preferences in order to automatically add it to new users of the system.

You can see the thread here:
[http://www.vmware.com/community/message.jspa?messageID=617906](http://www.vmware.com/community/message.jspa?messageID=617906)

Best regards!

---

### Post by zenon212 on 2007-06-06
I have been having a similar problem, but I know nothing about VMWare and as far as I know it does not factor into my problem.

In my situation, I have been attempting to use Xming to log into one of two Ubuntu boxes from a laptop running XP or a desktop running Vista.  After the login I, too, get the gray box.  Sadly I have never stuck around long enough to find out if it does anything after that, but I have waited on it a little bit. It was a quite frustrating problem and after much searching around on the Internet and this forum, I finally gave up.  I figured I would take another crack at it after a while.

Well, I eventually installed the Kubuntu aspect of Ubuntu and on a whim decided to try to login to KDE via Xming and lo and behold it let me in.  In fact I am posting from that scenario as I write.  I went back and attempted to go into Gnome again, thinking that maybe I changed something else without knowing it, but to no avail.

So for me, KDE doesn't have the problem, however I need, or rather want, to figure out how to get Gnome fixed.  Either that or abandon Gnome altogether and just use KDE.

---

### Post by zenon212 on 2007-06-12
Oddly enough, I am attempting to install Ubuntu on my laptop now and I am getting the same problem.  So it is apparently not an Xming problem, but rather one with Gnome and my laptop. (Both my laptop and my desktop are made by Dell.)

---

### Post by Legendary Teeth on 2007-07-06
I was having a very similar problem. I got a new computer, and wanted to connect to my old computer running Ubuntu using Xming on XP. I could log in, but I just got the beige background with eventually a blank box in the top left. It woul turn into an error dialog eventually, and if I closed it, some of the desktop loaded, but there were no application bars or anything. Everything was reaaaaallly slow, too.

I thought I had configured the firewall properly on my XP box, and I thought it asked me for permission to let Xming out. But when I turned off the windows firewall, everything ran fine.

So even if you think there's no firewall problem, it might be that.

---

### Post by phryx on 2007-07-08
> **adam_m said:**
> It seems to be a XMing problem. Don't use the Clipboard Manager and it works fine.

Thanks for posting this solution, helped me n getting this to work.

---

### Post by DCToblerone on 2007-08-01
I too had this problem (using Feisty Fawn) and now I have solved it. It no longer freezes when loggin in, the clipboard works, it no longer hangs on logout, and also sounds are working too!

You need to let in port 16001 in your Windows firewall and download and run this esd server:
[http://www.liquid-reality.de/main/projects/esound](http://www.liquid-reality.de/main/projects/esound)

I also made this change in /etc/gdm/gdm.conf-custom. I'm not sure this is necessary but it doesn't seem to hurt.

[daemon]
KillInitClients=0

I also rebooted the machine (probably to get gdm to restart) and now everthing is working.

P.S. some sites suggest opening port 35091 too, but this didn't seem to do anything for me.

Hope this helps.
Dave

---

### Post by RodZap on 2007-08-06
Hello, thanks all for this thread.
I had the blank screen problem and fixed it disabling the clipboard.

I have a different question: is there a way to open a connection with xdmpc and keep it open after closing the xming window? in this way you would be able to turn off the xp box and keep the programs running in the linux box, and come back other time to continue with whatever work is being done in the session. This would be like a VNC functionality.

Thanks!

Rod

---

### Post by Bill_Farrow on 2007-08-14
There should be a way to keep your session running when you disconnect so that you can reconnect at a later date and have everything as you left it.

I haven't tried this yet, but here is a web article describing how to do just this with VNC and XDCMP.

 [HOWTO: Remote Desktop with VNC in Ubuntu Edgy/Feisty]("http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/")

---

### Post by jom2000 on 2007-08-18
I also had the blank screen problem, which was solved by disabling the clipboard.

I would however like to be able to cut and paste between Windows and Ubuntu. Has anyone submitted a bug report for this?

---

### Post by bgturk on 2007-08-27
> **adam_m said:**
> It seems to be a XMing problem. Don't use the Clipboard Manager and it works fine.

That is not true. I have disable the Clipboard Manager and it still does not work fine.

---

### Post by bgturk on 2007-08-27
It is a Windows Firewall issue. Temporarily disabling the firewall on the Windows machine running the Xming resolved the problem for me.

---

### Post by Lee Gray on 2007-09-06
I have been struggling with this too, and having succeeded, would like to add my weight to the "disable ESD Sounds settings within the Gnome desktop" fix.

It works for me, and whats more as a test I disabled the sound locally on the Ubuntu box, then remotely logged in, and re-enabled the sound from the remote session - the remote session instantly hung. 

To disable the sound, you can either used the desktop menus or run "gnome-sound-properties" from a terminal. 

Another point I found is that I needed to individually disable the sound in all profiles - i.e. if I logged in locally with my normal user account, disable the sound, and then logged in remotely with that account, all was OK. If I ran "gedit" from a terminal, up poped the editor, as expected. However, if I ran "sudo gedit", the editor faild to start. To fix this I needed to log back in locally, and run "sudo gnome-sound-properties". Here I found the sound still enabled, and it needed to be turned off here too.

One final point. Without this fix I was able to log in successfully with another session, such as xfce, but Gnome functions such as gedit still failed.

I suspect disabling the sound is not really addressing the underlying problem. It may well be that with ESD Sound settings enabled, Gnome tries to connect out to the machine that is running the remote desktop, but no-matter if this is true or not, disabling the sound fixes the problem (unless you need sound, but that is another matter).

Thanks for all the hints and tips.

Cheers,
         Lee.

---

### Post by garethwatson on 2007-09-24
I had this problem as well.  Damn annoying.

**_History_**
I disabled the clipboard and it started working but I REALLY wanted the clipboard functionality. So...


**_Fix_**

I edited ```
/etc/gdm/gdm.conf
```

In the [daemon] section, I added the line:

```
KillInitClients=false
```

Then I needed to restart gdm by running:

```
sudo /etc/init.d/gdm restart
```

Now I can connect AND use the clipboard from Lin<->Win.  Woohoo.

I hope this helps someone.

Cheers,

Gareth.

---

### Post by apoth on 2007-10-16
> **DCToblerone said:**
> You need to let in port 16001 in your Windows firewall

Thanks, worked for me.

---

### Post by MorsCerta on 2007-12-26
This is definetely a Windows Firewall issue. Very anoying. Disabling ESD in the Ubuntu system sound configuration finally worked for me. Nothing else! Maybe replacing the ESD server would do also.

---

### Post by washeeq on 2008-04-13
Hi,
I have experienced the same issue with Ubuntu and Xming. In my case, disabling the clipboard and little firewall tuning fixed the problem.

Thanks everyone in this thread!

Cheers,
washeeq

---

### Post by sharkey77 on 2008-05-16
> **garethwatson said:**
> I had this problem as well.  Damn annoying.

**_History_**
I disabled the clipboard and it started working but I REALLY wanted the clipboard functionality. So...


**_Fix_**

I edited ```
/etc/gdm/gdm.conf
```

In the [daemon] section, I added the line:

```
KillInitClients=false
```

Then I needed to restart gdm by running:

```
sudo /etc/init.d/gdm restart
```

Now I can connect AND use the clipboard from Lin<->Win.  Woohoo.

I hope this helps someone.

Cheers,

Gareth.

I can't edit this file as it belongs to root.  I don't know how to sudo to edit a text file, I tried and failed.

As far as the ports, firewalls, clipboard, and esd I've tried them all but I get the background picture after logging in.  I'm not using vmware so it's not related to that.  When I log in locally it says I'm already logged in (from the xming on windows) and I get an error message on the local about ISD (not ESD) and port 5800 in use which I think VNC uses.

Any other suggestions to get this working?

Thank you.

P.S. Running 8.04

---

### Post by sharkey77 on 2008-05-16
Figured out how to edit gdm.conf but it didn't help.  The computer refused to go back to graphical until I did a reboot.

```
gksudo gedit /etc/gdm/gdm.conf
```

---

