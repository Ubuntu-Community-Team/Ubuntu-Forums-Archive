---
title: "Dropbox icon missing in top panel (Xubuntu 14.04)"
date: 2014-12-15
forum: General Help
---

### Post by Bill Tetzeli on 2014-12-15
I apologize first off for posting on a topic I've already seen covered, but so far nothing I've read has helped.

I recently lost the Dropbox icon in the indicator portion of my top panel.  I know Dropbox is still running in the background because when I type "dropbox stop" in a terminal window I get back "Dropbox is already running!"  Still, without the Dropbox icon, I can't configure it, check on sync progress, adjust bandwidth, or anything else of importance.  This icon is gone on all four computers running Xubuntu 14.04 - the only one it's still on is one running Zorin 9.

Here's what I've done so far:

- Tried to install libappindicator1 - turns out I already have it.
- Turned off the indicator application in Session and Startup (in the Settings Manager).  Worked for a few logins, now zip.
- Uninstalled Dropbox using the method recommended on their website ("[COLOR=#3D464D]sudo apt-get remove dropbox; rm -rvf ~/.dropbox ~/.dropbox-dist"), then downloaded and installed the 64-bit .deb from the Dropbox website.  No go.

Has anyone with this problem managed to find a permanent fix?  I'm going nuts with this, and definitely don't want to go through the hell of installing different distros until I find one that works with it.  Get it together, Dropbox!

Thanks in advance,

Bill[/COLOR]

---

### Post by vasa1 on 2014-12-15
> **Bill Tetzeli said:**
> ...
Has anyone with this problem managed to find a permanent fix?  I'm going nuts with this, and definitely don't want to go through the hell of installing different distros until I find one that works with it.  ...
What's your Dropbox version? There are reports of icons looking ugly in Dropbox 3.0.3 and otherwise "misbehaving". Maybe an update will fix things.

---

### Post by Bill Tetzeli on 2014-12-15
Well, this is weird.  The .deb package I downloaded is named dropbox_1.6.2_amd64.deb, but when I go into Preferences it says 3.0.3, so I guess that's what it is.  In any case, I split the difference and downloaded the LXDE environment.  So far Dropbox is showing up fine in the bottom panel, and other than a few minor differences I have no real quibbles with it.  I guess I can continue using LXDE until a fix shows up, but I really prefer the Xubuntu XFCE environment.

<rant>What burns me is that this isn't one of those "Do you want a refund on your free OS/free software" kind of things.  I pay $99 a year to Dropbox for their Pro package (granted, it's a full 1 TB and change, but even so).  My money's as good as a Windows or Mac user's, and when they spend it no one asks what OS the customer who paid it was using, so I have every right to expect just as good service as if I was using Windows or Mac.  The only part of supply and demand I want to know is if I supply the $$$$$, then I demand the service.</rant>

---

### Post by vasa1 on 2014-12-15
No point ranting here in a support forum ;)

If you're a pro user, there should be Dropbox-run support. I'm grateful that Dropbox provides a Linux desktop solution unlike Google and I'm sure they'll fix things down the road.

---

### Post by Kurt_Alan on 2014-12-19
Hi Bill,

I'm tearing my hair out on same problem. I pay almost $500.00 per year to dropbox.com  I have emailed them re: same and I'm still waiting for a response. Meanwhile, I've done a lot of obvious stuff to no avail: e.g. uninstalled and reinstalled two versions: either via synaptic or the .deb via command line -- and more.

Dropbox is the center of my work. I, too, do not what to change my OS flavor just because of one damn but critical indicator.  Without this indicator Dropbox is dead in the water.  You cannot access Selective Sync or any of its powerful features.  Sure Dropbox itself is running . . . Now the indicator WAS working on 14.10 Xubuntu (new install) which suggests that it CAN work and that it must be broken.  I'm still researching this problem and looking for a solution.

Do you have a solution yet? We are in the same predicament.

---

### Post by markodd on 2014-12-20
I'm also having this problem. If anyone manages to fix it, please let me know!

---

### Post by bapoumba on 2014-12-20
Have you tried to run it from the terminal and see if there is any message ?
```
dropbox-dist/dropboxd
```

---

### Post by markodd on 2014-12-20
@bapoumba

I get the following error message:

```
bash: dropbox-dist/dropboxd: No such file or directory
```

In what folder am I supposed to run that command?

---

### Post by bapoumba on 2014-12-20
Sorry, my copy/paste from my cheat sheet got truncated :)
```
bapoumba@bapoumba-utopic:~$ ~/.dropbox-dist/dropboxd
Another instance of Dropbox (2123) is running!
```
Here is the command again, with my own output.

---

### Post by markodd on 2014-12-20
@bapoumba:

Same output:

```
bash: /home/markodd/.dropbox-dist/dropboxd: No such file or directory
```

---

### Post by bapoumba on 2014-12-20
Hmm.. How did you install dropbox ? I installed nautilus-dropbox.

---

### Post by el_garicimo on 2014-12-20
[COLOR=#000000]I've been hammering on this all day...not solved but made some interesting discoveries... i'm using 64 bit xubuntu 14.04 on a dell xps 12 9q33[/COLOR]

[COLOR=#000000]I don't know if it's related, but there was also an indicator issue with Copy, which this post from webupd8 addresses: [/COLOR][http://www.webupd8.org/2014/06/fix-c...or-ubuntu.html]("http://www.webupd8.org/2014/06/fix-copycom-indicator-menu-for-ubuntu.html")
[COLOR=#000000]I've been trying to figure out if I could apply this solution analogously to my dropbox installation, but it's not been obvious / haven't been able to figure it out.[/COLOR]

[COLOR=#000000]in this article, the link to this bug report: [/COLOR][https://bugs.launchpad.net/libdbusmenu/+bug/1086563](https://bugs.launchpad.net/libdbusmenu/+bug/1086563)

[COLOR=#000000]and in that bug report, there is a test case python script:[/COLOR]
[http://pastebin.ubuntu.com/7604811/](http://pastebin.ubuntu.com/7604811/)

[COLOR=#000000]downloading that python script as python_test.py and running that python script in my terminal:[/COLOR]
[COLOR=#000000]$ python python_test.py[/COLOR]

[COLOR=#000000]I get a firefox indicator popping up...however, if I change the "firefox" in line 18 of the python script to "dropbox" , a dropbox indicator shows up![/COLOR]

[COLOR=#000000]ctrl- z stops the python script, and closing that terminal windows makes the icons disappear again.[/COLOR]

[COLOR=#000000]Perhaps this info will help people who actually know what they're doing get a fix![/COLOR]

---

### Post by el_garicimo on 2014-12-20
Wow, I think I inadvertantly figured it out! For me at least :-p

I have a netbook that I'm running a 32 bit installation of lubuntu on, and the dropbox icon works fine there...I figured I'd try to install another desktop environment to see if that would help. Apparently it's pretty easy, and this article does a good job of explaining it:

[http://www.howtogeek.com/193129/how-to-install-and-use-another-desktop-environment-on-linux/](http://www.howtogeek.com/193129/how-to-install-and-use-another-desktop-environment-on-linux/)

Basically, it's super easy to install another desktop environment and switch which one you want to load upon login. I decided i'd try lubuntu here's what I did

1.) install the desktop environment via terminal (you could use the software center too though)

$ sudo apt-get install lubuntu-desktop

2.) after it was done, shut down the computer

3.) boot into xubuntu. At the login screen, in the upper right next to the batter icon, there's a little xubuntu icon...click that, and it gives you a choice of what session to log in as. I didn't even know this, but apparently there's an 'xfce session' option and a 'xubuntu' session option....being curious, i clicked on the 'xfce session' option, and logged in....and voila! dropbox icon was back.

4.) Now that the icon was back, I tried it for the regular 'xubuntu' login session and it works for that too. And of course it woks for the lubuntu sessions as well.

So that seemed to do it! hopefully it works for you guys too!

---

### Post by markodd on 2014-12-21
@el_garicimo 

I'm glad you found something that works for you.. I don't want to install a whole desktop environment to have dropbox working though! It would be cool if someone found out what exactly makes it work, so I can install that something only.

---

### Post by markodd on 2014-12-21
Actually, there's no need to install a diferent desktop environment. All you need to do is change to XFCE and then when going back to Xubuntu, the icon is there. However, how do I make Xubuntu my default environment?! It always boots me to xfce and it's pissing me off!


EDIT: Apparently I'm on Xubuntu, but everything looks different. For example, my "docky" doesn't let me choose "Intellihide" now. A warning pops-up saying that docky requires compositing and because of that docky will not function properly and the windows will look different. So ya, does anyone know how to fix this or will I have to format my PC again?

God damn it algaricimo, I hate you! 

Though really, why does switching to XFCE and then going back to Xubuntu break things up?!

---

### Post by markodd on 2014-12-22
@bapoumba

After removing and installing dropbox and trying several stuff I found online, the command you suggested gave me the following output:

```
 Another instance of Dropbox (1933) is running!
```

---

### Post by bapoumba on 2014-12-22
@markodd, OK, so now it is working. Is the panel notification working too ?

---

### Post by markodd on 2014-12-22
> **bapoumba said:**
> @markodd, OK, so now it is working. Is the panel notification working too ?

Sadly, no. It works if I disable compositing and then do a restart. But I need compositing, so that's not really a solution for me.

---

### Post by bapoumba on 2014-12-22
There is this other current thread : [http://ubuntuforums.org/showthread.php?t=2257571](http://ubuntuforums.org/showthread.php?t=2257571)

---

### Post by bapoumba on 2014-12-22
Update, with today's updates :
```
bapoumba@bapoumba-utopic:~$  dropbox status
Dropbox isn't running!
bapoumba@bapoumba-utopic:~$ ~/.dropbox-dist/dropboxd &
[1] 3079
bapoumba@bapoumba-utopic:~$ dropbox status
Up to date

```
~/.dropbox-dist/dropboxd & brings the notification icon up in the panel. Will manually add dropbox to the startup applications and see if it sticks.

---

### Post by markodd on 2014-12-22
```
markodd@markodd:~$ dropbox stop
Dropbox daemon stopped.
markodd@markodd:~$ dropbox status
Dropbox isn't running!
markodd@markodd:~$ ~/.dropbox-dist/dropboxd &
[1] 5415
markodd@markodd:~$ dropbox status
Up to date



```

No icon whatsoever.

---

### Post by bapoumba on 2014-12-22
Just one thought, are you using a standard theme ? If not, could you please try with one ?

---

### Post by nicola13 on 2014-12-23
Yesterday i tried a live version of kxstudio, just to see it. After i rebooted to Xubuntu the dropbox icon reappeared, then it disappeared again. For what it can help.

---

### Post by Andr_Lus_Matte on 2015-01-03
I spent two days searching for a fix to the same problem and I found a solution that seems so surprising as annoying. I am using Xubuntu 14.04 and I was logged on a Xubuntu session. I just logged off and logged on again but in a Xfce session. Surprisingly the missing Dropbox applet icon appeared on the systray! Then I logged off and logged on again in a Xubuntu session and the icon was there again! So annoying discover so simple after spending two long days searching a solution!

---

### Post by gdtrfb1968 on 2015-01-05
Thanks Andr_Lus_Matte!  Although logging on to a Xfce did not work at first, logging back on to a Xubuntu session did!  Dropbox version 3.03.

---

### Post by markodd on 2015-01-06
> **Andr_Lus_Matte said:**
> I spent two days searching for a fix to the same problem and I found a solution that seems so surprising as annoying. I am using Xubuntu 14.04 and I was logged on a Xubuntu session. I just logged off and logged on again but in a Xfce session. Surprisingly the missing Dropbox applet icon appeared on the systray! Then I logged off and logged on again in a Xubuntu session and the icon was there again! So annoying discover so simple after spending two long days searching a solution!

You spent two days searching for a fix that "everyone" already knows? That "fix" is well documented in this very same thread! Did you even read the thread in which you're posting? Look at post [13]("http://ubuntuforums.org/showthread.php?t=2256902&page=2&p=13191247#post13191247").

The reason why that works is mentioned in [this]("http://askubuntu.com/questions/561448/dropbox-3-0-4-ignoring-local-themes-missing-notification-icon/564297#564297") askubuntu thread. 

<snip>

---

### Post by adiesner on 2015-01-07
What worked for me is to disable compositing:

[LIST]
[*]Go to "All settings" and click on "Window manager tweaks": 
[*]Go to the tab "Compositor" 
[*]Uncheck the "Enable display compositing" option 
[/LIST]

enter in a terminal:
```
dropbox stop
dropbox start
```

The icon disappears again, as soon as I enable compositing again :-(

See also: [http://askubuntu.com/questions/561448/dropbox-3-0-4-ignoring-local-themes-missing-notification-icon](http://askubuntu.com/questions/561448/dropbox-3-0-4-ignoring-local-themes-missing-notification-icon)

---

### Post by James_Doc on 2015-01-19
> **adiesner said:**
> What worked for me is to disable compositing:

[LIST]
[*]Go to "All settings" and click on "Window manager tweaks":
[*]Go to the tab "Compositor"
[*]Uncheck the "Enable display compositing" option
[/LIST]


This has worked for me.

---

### Post by ckrles on 2015-01-28
In my case it has disappeared as well. I thought it had to something with Chrome, since it asked me to uninstall it along with some libraries (can't remenber). So I proceeded with the installation of dropbox and chrome was uninstalled. Then I installed Chrome again and it was fine, BBBBBBBBBUUUUUUUUUUTTTTTTTTTT, then for other reasons I reinstalled Xubuntu 14.04, Chrome was removed, Dropbox icon appeared and then it disappeared (but it still syncs) and hasn't been back.

The curious thing is that I have two session (2 users). And in my secondary user the dropbox application starts and asks me to introduce an account and password. I don't need the sync in that user account, so I don't need to input my detals.

And what's even more curious is that for one bootup at my main session the dropbox icon appeared. I thought it was fixed, but on the next reboot it was gone again.

I've read the whole thread and there seem to be many causes, which leads me to think that it's not something specific, but quite random. Just a newbie's opinion.

Am I right or has anybody discovered the specific reason for this bug?

Thank you.

---

### Post by idobrinescu on 2015-04-09
Apparently someone finally figured this out here:
[http://www.srw2d.com/getting-dropbox-notification-working-in-elementary-os-freya/](http://www.srw2d.com/getting-dropbox-notification-working-in-elementary-os-freya/)


1. Start dropbox with this command
dropbox stop && env XDG_CURRENT_DESKTOP=Unity dropbox start


2. Go to settings and turn off "Start Dropbox on system startup" 


3. Go to system settings -> Applications , from the tab up top select "Startup" and add a command from the + button at the bottom left and there will be an input where you can enter in a command below and press enter to save.
env XDG_CURRENT_DESKTOP=Unity dropbox start

[COLOR=#333333][FONT=monospace]Worked for me on Elementary OS Freya. I finally have the dropbox indicator working. :))[/FONT][/COLOR]

---

### Post by milegrin2 on 2015-05-29
Confirmed in Vivid 15.04 too running Gnome Flashback.  

This worked for me:

Change the "Exec" line in the dropbox.desktop files to :
```

Exec=env XDG_CURRENT_DESKTOP=Unity dropbox start -i

```
Make the change in /usr/share/applications/dropbox.desktop file:
  ```

sudo gedit /usr/share/applications/dropbox.desktop

```Make the change in ~/.config/autostart/dropbox.desktop file:
```

gedit ~/.config/autostart/dropbox.desktop

```

Then restart dropbox
```
 dropbox stop && dropbox start -i
```


Source : 
[http://askubuntu.com/questions/618410/icons-missing-and-misbehaving-in-gnome-panel-since-15-04-upgrade](http://askubuntu.com/questions/618410/icons-missing-and-misbehaving-in-gnome-panel-since-15-04-upgrade)
[http://www.srw2d.com/getting-dropbox-notification-working-in-elementary-os-freya/](http://www.srw2d.com/getting-dropbox-notification-working-in-elementary-os-freya/)

---

### Post by Mike_Lim on 2016-02-14
I'm using Xubuntu 14.04.3 with Dropbox v3.14.5 and below command works for me, but it's using unity icon. 

> dropbox stop && env XDG_CURRENT_DESKTOP=Unity dropbox start

---

### Post by dez93_2000 on 2016-02-17
This resulted in the following for me:

> Dropbox daemon stopped.
Starting Dropbox...Dropbox isn't running!
Done!
(dropbox:3507): GLib-GObject-WARNING **: cannot register existing type 'GdkDisplayManager'
(dropbox:3507): GLib-CRITICAL **: g_once_init_leave: assertion 'result != 0' failed
(dropbox:3507): GLib-GObject-CRITICAL **: g_object_new: assertion 'G_TYPE_IS_OBJECT (object_type)' failed

Trying
> xfce4-panel --quit
then starting dropbox through the menu, then
> xfce4-panel
results in
> upstart: indicator-power main process ended, respawning
upstart: indicator-messages main process ended, respawning
upstart: indicator-sound main process ended, respawning
upstart: indicator-messages main process ended, respawning
upstart: indicator-power main process ended, respawning
upstart: indicator-application main process ended, respawning
upstart: indicator-messages respawning too fast, stopped
upstart: indicator-power respawning too fast, stopped
upstart: indicator-sound main process ended, respawning
upstart: indicator-application main process ended, respawning
upstart: indicator-sound respawning too fast, stopped
upstart: indicator-application respawning too fast, stopped

Where it sits for minutes. I then tried dropbox again from the menu and got:

> (xfce4-panel:3867): Gtk-CRITICAL **: IA__gtk_widget_show: assertion 'GTK_IS_WIDGET (widget)' failed
Dropbox is already running!

I don't know if this has already been discovered, but it feels like the root of the problem.
Potential help [here]("https://askubuntu.com/questions/561448/dropbox-3-2-9-ignoring-local-themes-missing-notification-icon") but I'm still trying to make sense of it.
Potentially of interest: dropbox & icon work fine on my laptop (xubuntu 15.10, db version 3.14.7, 2015.02.12 in software centre), but has this problem on my desktop (xubuntu same, db v 2012.10.28). So conceptually something was changed between those versions which affects the GTK_IS_WIDGET spawn code. [This]("http://www.gtkforums.com/viewtopic.php?p=6516") is info about that line. The note about window & window1 got me thinking: another difference between my setups, other than the dropbox version, is that my main pc has 2 workspaces & my laptop only has 1. Will experiment with 1 workspace on main pc & report back.
Edit: nope, no change. Next experiment: try to find the deb for v2015.02.12 [[https://www.dropbox.com/download?dl=packages/ubuntu/dropbox_2015.02.12_amd64.deb]](https://www.dropbox.com/download?dl=packages/ubuntu/dropbox_2015.02.12_amd64.deb]) uninstall current version reboot and install older version.
Edit2: no improvement. Installs, I launch from menu, and the broken icon pops up. xfce panel is 4.12.0 on both machines. The only difference I can think of, which is clutching at straws, is that probably-irrelevant GTK_IS_WIDGET window/window1 error, since my main pc has 2 workspaces. Both machines only have 1 display. I haven't tried installing either db version with only 1 workspace on my main machine.
Out of ideas. Compositing trick didn't work for me.

---

### Post by raphael k on 2016-02-18
I have the same problem with xubuntu 14.04 :
I tried many of the suggested solutions, [ postet on askubuntu]("http://askubuntu.com/questions/358913/no-dropbox-icon-in-the-indicator-panel?answertab=oldest#tab-top"). But with all of the preferred solutions the problem still remains: Instead of the dropbox symbol there is a squared "no image" place holder; and when I click on it, I see only the upper shadow of the popup menue. 

This problem did not exist in the current version of Linux Mint xfce (Rosa), that I had installed previously.

---

### Post by scottbomb on 2016-03-08
I just got help for this from Dropbox support. Here is what worked for me:
> We're currently investigating this issue. While we do this, we'd like to offer you a workaround as a temporary solution.

If you would like to use this workaround, you can do so by opening a Terminal session and running the following command:

dropbox stop && DBUS_SESSION_BUS_ADDRESS="" dropbox start

Several users have reported that this workaround is successful and have documented more information in the following Ubuntu forum:

[http://askubuntu.com/questions/732967/dropbox-icon-is-not-working-xubuntu-14-04-lts-64/736205#736205](http://askubuntu.com/questions/732967/dropbox-icon-is-not-working-xubuntu-14-04-lts-64/736205#736205)

Please note that it is possible that you will need to run this workaround every time you restart your computer.

Finally, please take into account that this is a workaround intended for Xubuntu and XFCE based Linux distributions; however, you can also try these steps if you're running KDE or any other desktop environment, but since these others would not be within the list of requirements to run Dropbox on Linux, we may not be able to provide further support.

This worked for me on Kubuntu 14.04.2 on AMD and Intel machines.

---

### Post by dez93_2000 on 2016-03-08
That's awesome, cheers Scott

---

### Post by QNEPFmr on 2016-04-20
This is working here as well, I get a nice DB icon instead of an icon with a question mark in it...
This should be a XFCE issue, but I don't have a problem on my Arch box with a xfce DE.

---

### Post by Elvis_de_Freitas_S on 2016-05-26
Thanks guy, it worked on lubuntu 16.04, I had the same issue 

[COLOR=#000000] env XDG_CURRENT_DESKTOP=Unity dropbox start[/COLOR]

> **idobrinescu said:**
> Apparently someone finally figured this out here:
[http://www.srw2d.com/getting-dropbox-notification-working-in-elementary-os-freya/](http://www.srw2d.com/getting-dropbox-notification-working-in-elementary-os-freya/)


1. Start dropbox with this command
dropbox stop && env XDG_CURRENT_DESKTOP=Unity dropbox start


2. Go to settings and turn off "Start Dropbox on system startup" 


3. Go to system settings -> Applications , from the tab up top select "Startup" and add a command from the + button at the bottom left and there will be an input where you can enter in a command below and press enter to save.
env XDG_CURRENT_DESKTOP=Unity dropbox start

[COLOR=#333333][FONT=monospace]Worked for me on Elementary OS Freya. I finally have the dropbox indicator working. :))[/FONT][/COLOR]

---

