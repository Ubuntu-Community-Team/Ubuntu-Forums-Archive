---
title: "Putting a webpage as background in Gnome...? [Resolved mostly]"
date: 2006-11-10
forum: General Help
---

### Post by harty83 on 2006-11-10
UPDATE:  We successfully got kwebdesktop to work under gnome but it included making kdesktop your default desktop manager. This caused a number of issues in the end so I decided it was not worth it.  I ended up using kwebdesktop in a script to keep my desktop updated with a webpage.  To keep people from going through all of our experimentation, I'm adding this mini howto here.

1) Install kdesktop 
```
sudo apt-get install kdesktop
```

2) Edit the following script to fit your needs
```
#!/bin/bash

#directory you want the snapshots to be kept
LOCATION="/home/alan/Background/"

#website to make a snapshot of
WEBSITE="http://www.google.com/calendar/"

#check for an internet connection; if not connected, use backup of last successful snapshot
x=`ping -c1 google.com 2>&1`

if [ "$x" = "ping: unknown host google.com" ]; then
	if [ -f $LOCATION/background-2.png ]; then	
		cp $LOCATION/background-2.png $LOCATION/background-1.png
	fi
		
else 
	#use kwebdesktop to get a snapshot of the webpage
	/usr/bin/kwebdesktop 1200 600 $LOCATION/background-1.png "$WEBSITE"

	if [ -f $LOCATION/background-1.png ]; then	
		cp $LOCATION/background-1.png $LOCATION/background-2.png
	fi
fi

#use gconftool to set the updated snapshot
gconftool-2 -t str --set /desktop/gnome/background/picture_filename "$LOCATION/background-2.png"
#change it twice so that it updates to the new snapshot
gconftool-2 -t str --set /desktop/gnome/background/picture_filename "$LOCATION/background-1.png"
gconftool-2 -t str --set /desktop/gnome/background/picture_options "centered"

```

3) Make the script executable
```
chmod a+x *scriptname*
```

4) Add the script to start up (System->Preferences->Sessions->Startup Programs tab) or add it as a cron job.  

Hope this helps!

---

### Post by aysiu on 2006-11-10
Why do you need a script? Can't you just press Alt+Prt Scrn?

That key combination usually invokes the ```
gnome-screenshot --window
``` command.

---

### Post by harty83 on 2006-11-10
> **aysiu said:**
> Why do you need a script? Can't you just press Alt+Prt Scrn?

That key combination usually invokes the ```
gnome-screenshot --window
``` command.

Yup.  I want a script that will auto capture my google calendar so I don't have to manually take a screen shot every time I change it.

---

### Post by aysiu on 2006-11-10
Instead of images of your Google calendar, might it make sense to make some other form of backup of the calendar? This page may help you out:
[How do I export my Google Calendar data?](http://www.google.com/support/calendar/bin/answer.py?answer=37111&topic=8566)

You might find some way of timing the screenshot application to take a screenshot at a particular time or at an interval, but I don't know how you'd have it know you were saving out of Google Calendar and not Ubuntu Forums...

---

### Post by harty83 on 2006-11-10
> **aysiu said:**
> Instead of images of your Google calendar, might it make sense to make some other form of backup of the calendar?

I'm not backing up the data but rather placing the screenshot as my background.

---

### Post by aidanr on 2006-11-10
[screengrab]("https://addons.mozilla.org/firefox/1146/")
[ff 2.0 version]("http://andy.5263.org/screengrab_files/screengrab_v0.8_FF2.xpi")

---

### Post by aysiu on 2006-11-10
> **harty83 said:**
> I'm not backing up the data but rather placing the screenshot as my background.
I realize you're probably using Gnome, but in KDE, you can have a webpage (like [http://calendar.google.com](http://calendar.google.com)) be your background wallpaper.

Just enable kwebdesktop and change [http://www.kde.org](http://www.kde.org) to something else.

Maybe Gnome has something like this, too. I'm not sure.

---

### Post by harty83 on 2006-11-10
> **aysiu said:**
> I realize you're probably using Gnome, but in KDE, you can have a webpage (like [http://calendar.google.com](http://calendar.google.com)) be your background wallpaper.

Just enable kwebdesktop and change [http://www.kde.org](http://www.kde.org) to something else.

Maybe Gnome has something like this, too. I'm not sure.

It would be great if gnome had something like kwebdesktop but unfortunately I've already searched and cannot find anything suitable.

---

### Post by aysiu on 2006-11-10
> **harty83 said:**
> It would be great if gnome had something like kwebdesktop but unfortunately I've already searched and cannot find anything suitable.
This may be more trouble than it's worth, but maybe if you use *kwin* as your window manager in Gnome (instead of Gnome's default window manager, Metacity), you could use *kwebdesktop* on your Gnome background?

[Here's a screenshot of someone's Gnome Kwin desktop](http://ubuntuforums.org/gallery/showphoto.php?photo=1642&cat=11&limit=views)

And [here's a tutorial on using Kwin in Gnome](http://ubuntuforums.org/showthread.php?t=115974).

---

### Post by harty83 on 2006-11-10
> **aysiu said:**
> This may be more trouble than it's worth, but maybe if you use *kwin* as your window manager in Gnome (instead of Gnome's default window manager, Metacity), you could use *kwebdesktop* on your Gnome background?

[Here's a screenshot of someone's Gnome Kwin desktop](http://ubuntuforums.org/gallery/showphoto.php?photo=1642&cat=11&limit=views)

And [here's a tutorial on using Kwin in Gnome](http://ubuntuforums.org/showthread.php?t=115974).

That's like trading a lot of things I like to get one thing I like to work.  I'm not a big fan of kde interface.  If there is nothing really suitable then I'll just have to stick with the old manual way although that firefox extension makes a little less hassle :-).

---

### Post by aysiu on 2006-11-10
> **harty83 said:**
> That's like trading a lot of things I like to get one thing I like to work.  I'm not a big fan of kde interface.  If there is nothing really suitable then I'll just have to stick with the old manual way although that firefox extension makes a little less hassle :-).
You wouldn't exactly be using KDE instead of using Gnome. You'd be using Kwin instead of Metacity. But I can understand your hesitation to do something so involved.

---

### Post by harty83 on 2006-11-10
> **aysiu said:**
> You wouldn't exactly be using KDE instead of using Gnome. You'd be using Kwin instead of Metacity. But I can understand your hesitation to do something so involved.

I don't like the kde look and feel but I decided to give it a shot.  I set things up according to the tutorial you listed.  I notice that somethings have changed but not much.  The one thing I noticed is that Alt-F2 no longer brings up a run command prompt.  Anyway, I went into kcontrol and told it to use kwebdesktop as my background but it does not seem to work.  As a matter of fact it seems to have locked up kcontrol.  :confused:  Any ideas?

In a terminal I get 

```
kwebdesktop: ERROR: : couldn't create slave : Cannot talk to klauncher
```

Thanks!
Alan

---

### Post by aysiu on 2006-11-10
Using *kwebdesktop* disables Alt-F2? That's weird.

As for your error, I found these two threads. Not sure if they solve your problem or not:
[Cannot talk to klauncher](http://www.linuxforums.org/forum/ubuntu-help/70151-cannot-talk-klauncher.html)
[*Fixed* Error: Cannot talk to klauncher](http://kubuntuforums.net/forums/index.php?topic=10129.msg40845)

---

### Post by harty83 on 2006-11-10
> **aysiu said:**
> Using *kwebdesktop* disables Alt-F2? That's weird.

As for your error, I found these two threads. Not sure if they solve your problem or not:
[Cannot talk to klauncher](http://www.linuxforums.org/forum/ubuntu-help/70151-cannot-talk-klauncher.html)
[*Fixed* Error: Cannot talk to klauncher](http://kubuntuforums.net/forums/index.php?topic=10129.msg40845)

I think it is kwin that disables alt-F2.  I restarted my computer and no longer seem to get the klauncher errors.  

Maybe I can use kcontrol to remap alt-f2 but what exactly is the name of the program that alt-f2 is suppose to open?

Any clues where the file that kcontrol uses to store teh desktop settings is located?  It seems to lock up every time I try to click on the desktop background in kcontrol.  I've looked through .kde and do not see anything obvious.

Thanks!
Alan

EDIT: never mind, I found it in /home/alan/.kde/share/apps/kdesktop/programs

---

### Post by harty83 on 2006-11-10
Are you sure that kwebdesktop is suppose to work via kwin under gnome?  I now have everything set up with a website to be the background via kcontrol but I can't get it to actually be my background.

Thanks!
Alan

---

### Post by aysiu on 2006-11-10
I'm not sure *kwebdesktop* is supposed to work via Kwin under Gnome. It was just a guess, actually.

So Kwin is definitely in charge of the background, but *kwebdesktop* isn't working? Is it possible *kwebdesktop* isn't installed?

**Edit**: What's in your /home/alan/.kde/share/config/kdesktoprc file?

---

### Post by harty83 on 2006-11-10
> **aysiu said:**
> I'm not sure *kwebdesktop* is supposed to work via Kwin under Gnome. It was just a guess, actually.

So Kwin is definitely in charge of the background, but *kwebdesktop* isn't working? Is it possible *kwebdesktop* isn't installed?

**Edit**: What's in your /home/alan/.kde/share/config/kdesktoprc file?

```
[Desktop0]
BackgroundMode=Program
BlendBalance=100
BlendMode=NoBlending
ChangeInterval=60
Color1=0,48,130
Color2=192,192,192
CurrentWallpaperName=
LastChange=0
MinOptimizationDepth=1
MultiWallpaperMode=NoMulti
Pattern=
Program=kwebdesktop
ReverseBlending=false
UseSHM=false
Wallpaper=/usr/share/wallpapers/All-Good-People-1.jpg
WallpaperList=
WallpaperMode=NoWallpaper

```

> So Kwin is definitely in charge of the background, but kwebdesktop isn't working? Is it possible kwebdesktop isn't installed?

I don't think kwin is in control of the background.  The only obvious thing I can tell it is control of is window behavior.  Any clue on how to change who is control of what?

kwebdesktop is def installed
```
alan@hartyslaptop:~$ dir /usr/bin/kwe*
/usr/bin/kwebdesktop

```

---

### Post by aysiu on 2006-11-10
Hm. Actually, now that I think about it, Nautilus (not Metacity) is usually in charge of the desktop in Gnome. I wonder what handles the desktop in KDE. I don't think it's Konqueror. I did think it was Kwin, but that appears not to be the case.

I wonder if this might help at all: ```
killall nautilus
nautilus --no-desktop
kwin --replace
```

---

### Post by harty83 on 2006-11-10
> **aysiu said:**
> Hm. Actually, now that I think about it, Nautilus (not Metacity) is usually in charge of the desktop in Gnome. I wonder what handles the desktop in KDE. I don't think it's Konqueror. I did think it was Kwin, but that appears not to be the case.

I wonder if this might help at all: ```
killall nautilus
nautilus --no-desktop
kwin --replace
```

nautilus automatically restarts every time I kill it so I can't add the --no-desktop option.

edit - I added --no-desktop to the nautilus command in .gnome2/session.  No desktop showed up when I logged in but kwin didn't take it over either.  There was NO desktop at all.

---

### Post by aysiu on 2006-11-10
And ```
kwin --replace
``` didn't help?

I think one thing you might want to try is logging into KDE, just to make sure KDE is working properly. Then we can get back to trying to get Kwin to work in Gnome... or *kwebdesktop*.

I'll keep researching the issue if you will. Imagine how exciting it would be to successfully get *kwebdesktop* running in Gnome. I think we'd be the first to do it...

---

### Post by aysiu on 2006-11-10
Okay. It may not be Kwin at all.

I launched up KDE, looked at the Process Table and looked specifically for commands being run by the user (not by root).

One of those commands is ```
kdesktop
``` I'm assuming that is what's controlling the desktop, not ```
kwin
```

So maybe in addition to adding ```
nautilus --no-desktop
``` you can also add ```
kdesktop
``` and forget about ```
kwin
```

---

### Post by harty83 on 2006-11-10
> **aysiu]And
```
kwin --replace
```

didn't help?

I think one thing you might want to try is logging into KDE, just to make sure KDE is working properly. Then we can get back to trying to get Kwin to work in Gnome... or kwebdesktop.

I'll keep researching the issue if you will. Imagine how exciting it would be to successfully get kwebdesktop running in Gnome. I think we'd be the first to do it...[/QUOTE]

Okay, so I logged into kde and everything seems to work (although it took over a minute to load the desktop! maybe kwebdesktop getting an image).

I logged back into gnome and desktop nor panels were working.  I manually restarted nautilus was back as it should.

[QUOTE=aysiu said:**
> Okay. It may not be Kwin at all.

I launched up KDE, looked at the Process Table and looked specifically for commands being run by the user (not by root).

One of those commands is ```
kdesktop
``` I'm assuming that is what's controlling the desktop, not ```
kwin
```

So maybe in addition to adding ```
nautilus --no-desktop
``` you can also add ```
kdesktop
``` and forget about ```
kwin
```

I went back and added --no-desktop to the nautilus command in ./gnome2/session.  I added kdesktop in addition to kwin (needed for window management) in sessions under preferences and no go.  I have no desktop.  kdesktop is running, but I do not have a kde desktop.

---

### Post by aysiu on 2006-11-10
Darn it.

I have a test machine. I'm going to try it out and see if I have any luck with it. I'll post back any findings.

---

### Post by harty83 on 2006-11-10
Got close once.  I logged out and logged in and my background showed the kde blue but I got a message that it couldn't communicate with klauncher.  I ctrl-alt-backspace, logged back in and nothing. 

I've played around quite a bit with ~/.gnome2/session by adding kdesktop as another program to start but the system seems to freeze while processing something when I log in but eventually loads nautilus as the default desktop (even though I have --no-desktop option added in the same file).  

I have to finish up a paper and would like to take my wife out on a date so this will have to wait till later for me.

---

### Post by aysiu on 2006-11-10
Maybe by the time you and your wife get back from your date I'll have figured it out. I'm actually IM-ing my wife on GAIM... trying to figure what we're doing tonight...

---

### Post by harty83 on 2006-11-10
> **aysiu said:**
> Maybe by the time you and your wife get back from your date I'll have figured it out. I'm actually IM-ing my wife on GAIM... trying to figure what we're doing tonight...

Haha, that would be great! ;-).  I'm having an issue now with open office since I've been playing around.  It will not show any toolbar icons but rather just the words.  Attached is a screenshot.  Any clue about this?  Nothing else seems to be affected.

---

### Post by aysiu on 2006-11-10
Geez. I'm really sorry I referred you to that tutorial. It really seems to have screwed up your Gnome--no Alt-F2, no buttons in OpenOffice...

I don't know about that. In the meantime, though, I'll keep looking for a *kwebdesktop* solution in Gnome.

---

### Post by harty83 on 2006-11-10
> **aysiu said:**
> Geez. I'm really sorry I referred you to that tutorial. It really seems to have screwed up your Gnome--no Alt-F2, no buttons in OpenOffice...

I don't know about that. In the meantime, though, I'll keep looking for a *kwebdesktop* solution in Gnome.

No worries, I'll figure it out.  Openoffice was fine even after I followed the tutorial.  OO messed up when I started to play with settings on my own accord to see if I could get this thing to work. Much worse could have happened!  :-)

---

### Post by aysiu on 2006-11-10
Success! Got it to work. Hope the date with your wife went well. 

Forget all that Kwin-Gnome stuff. In fact, undo that entire tutorial.

Don't manually edit ~/.gnome2/session
Undo the tutorial completely so you are where you were before.

Then, go to System > Preferences > Sessions

On the first tab, check to automatically save your sessions at logout.

On the second tab, change the type on Nautilus to not restart but just to be normal. Then remove it and click **Apply**.

On the last tab, remove Nautilus and add in [i]nautilus --no-desktop[/code] and ```
kdesktop
``` to the start menu.

Finally, log out, and log back in again.

The one annoying thing is that since *nautilus --no-desktop* is a startup program, you'll get the file browser opening when you start Gnome.

Then, *kdesktop* should be managing the desktop, so just right-click the desktop and select **Configure Desktop** and set it up to use *kwebdesktop* and point to [http://calendar.google.com](http://calendar.google.com)

I tried it. It definitely works.

---

### Post by harty83 on 2006-11-10
Good news, bad news.

Good news: That's awesome!  It works!  Also, if you add --no-default-window  to nautilus --no-desktop then that annoying window will not open.

Bad news: kdesktop does not like the url gmail produces for calendars because it has a %40 in it.  kwebdesktop accepts it fine but kdesktop does not.  It just locks up ](*,)

---

### Post by aysiu on 2006-11-11
I wonder if something like Tiny URL could help that problem:
[http://www.geocities.com/adilbookz/Utilities/tinyurlcode.html](http://www.geocities.com/adilbookz/Utilities/tinyurlcode.html)

---

### Post by harty83 on 2006-11-11
> **aysiu said:**
> I wonder if something like Tiny URL could help that problem:
[http://www.geocities.com/adilbookz/Utilities/tinyurlcode.html](http://www.geocities.com/adilbookz/Utilities/tinyurlcode.html)

I have a small web server and actually tried creating a redirection using several means last night but kwebdesktop is too fast.  It gets a screen shot of a blank page.  The only thing that came close was creating a webpage that had a frame of the site in it, but again kwebdesktop is too fast and it took a screenshot of a very small box in the upper left corner that had scrollbars.  I guess a frame "expands" as it is loaded so kwebdesktop got it while it was "expanding."  I didn't see that kwebdesktop had any kind of timed feature. :-|

---

### Post by harty83 on 2006-11-11
Another thought: in the verbage of how to use kwebdesktop, it says that if you don't provide a URL, it will use what is in kwebdesktoprc. so I wonder if putting it in there would help at all. But I can't find any documentation on the syntax of what to put in kwebdesktoprc so i can't get it to work.  If I don't put anything, it defaults to KDEs homepage.    But again I cannot find anywhere a config file telling it to do that.  (I wonder if it is hard coded?)  Any thoughts?

---

### Post by aysiu on 2006-11-11
Yup--there's absolutely no documentation whatsoever on *kwebdesktoprc*. My guess, though, is that you'd run into the same problem with that.

Are % signs in URLs just stand-ins for spaces? What happens if you take out the % signs and leave in spaces in the web address?

---

### Post by harty83 on 2006-11-11
> **aysiu said:**
> Yup--there's absolutely no documentation whatsoever on *kwebdesktoprc*. My guess, though, is that you'd run into the same problem with that.

Are % signs in URLs just stand-ins for spaces? What happens if you take out the % signs and leave in spaces in the web address?

%20 is a space.  %40 is the @ symbol. I replaced "%40" with "@" and bam, it works!

This is great!

Thanks for all your work; I really appreciate it!

I really don't like the auto session save thing.  So my next step is to see if I can do all these from ~/.gnome2/session file.

I guess another issue is that it really doesn't like to be logged out and back in. I seem to consistently be getting "cannot talk to klauncher" error when I do.

---

### Post by harty83 on 2006-11-11
Okay, so I've done it without automatically saving sessions.

Here is what I did.

First, I added edited .gnome2/session to be as follows (or create it if it not there)

```
# This is the default session that is launched if the user doesn't
# already have a session.
# The RestartCommand specifies the command to run from the $PATH.
# The Priority determines the order in which the commands are started
# (with Priority = 0 first) and defaults to 50.
# The id provides a name that is unique within this file and passed to the
# app as the client id which it must use to register with gnome-session.
# The clients must be numbered from 0 to the value of num_clients - 1.

[Default]
num_clients=5
0,id=default0
0,Priority=10
0,RestartCommand=gnome-wm --sm-client-id default0
1,id=default1
1,Priority=40
1,RestartCommand=gnome-panel --sm-client-id default1
2,id=default2
2,Priority=40
2,RestartCommand=nautilus --no-default-window --no-desktop --sm-client-id default2
3,id=default3
3,Priority=60
3,RestartCommand=gnome-cups-icon --sm-client-id default3
4,id=default4
4,Priority=40
4,RestartCommand=gnome-volume-manager --sm-client-id default4
```

Then I added kdeinit and kdesktop to startup programs in system/preferences/sessions.

That did it.

Now the last thing to figure out.  It seems that kwebdesktop does not like to startup when you first log in.  When I have kdesktop set to use kwebdesktop and I first log in, kdesktop does not show up.  I click on System/preferences/sessions and under current session can watch kwebdesktop start and stop, start and stop.  I have to manually kill it with a killall kwebdesktop before kdesktop will show up.  Then I can manually kill and restart kdesktop, configure the desktop, set it to use kwebdesktop and it works.  I'm not for sure if this is a kde bug or if it is because I am trying to use it outside of it's native desktop.  

Continuing on...

---

### Post by harty83 on 2006-11-12
Okay so it is really cool that we got this to work.  However, using kdesktop in gnome causes a number of problems to the point where it is just not worth the hassle!  Therefore, I'm going back to plain old ubuntu.

But, I did use kwebdesktop to create a script! :mrgreen: 

```
#!/bin/bash

#check for an internet connection; if not connected, use backup of last successful snapshot
x=`ping -c1 google.com 2>&1`

if [ "$x" = "ping: unknown host google.com" ]; then
	if [ -f /home/alan/Background/background-2.png ]; then	
		cp /home/alan/Background/background-2.png /home/alan/Background/background-1.png
	fi
		
else 
	#work around for cannot talk to klauncher when log out and back in problem - kills other kde start up programs so not using at the moment
	#rm /home/alan/.DCOPserver_*__0

	#use kwebdesktop to get a snapshot of the webpage
	/usr/bin/kwebdesktop 1200 600 /home/alan/Background/background-1.png "http://www.google.com/calendar/"

	if [ -f /home/alan/Background/background-1.png ]; then	
		cp /home/alan/Background/background-1.png /home/alan/Background/background-2.png
	fi
fi

#use gconftool to set the updated snapshot
gconftool-2 -t str --set /desktop/gnome/background/picture_filename "/home/alan/Background/background-2.png"
#change it twice so that it updates to the new snapshot
gconftool-2 -t str --set /desktop/gnome/background/picture_filename "/home/alan/Background/background-1.png"
gconftool-2 -t str --set /desktop/gnome/background/picture_options "centered"

```

Not perfect (my first script) but added it to the start up list and it updates my desktop :-)

---

### Post by aysiu on 2006-11-12
That's awesome. If ever someone asks about webpage wallpaper for Gnome, I'm pointing them to this thread.

I'm also going to retitle this thread appropriately, so I can find it again later.

---

### Post by ildfroe on 2006-11-12
Hm, I tried the script, but I can only get the log-in page. How do you get past that?
When I go to the calendar through firefox, I get straight to the calendar not seeing the log-in page.

---

### Post by ildfroe on 2006-11-12
Oh and I have also lost Alt-F2... :-(

---

### Post by harty83 on 2006-11-12
> **ildfroe said:**
> Oh and I have also lost Alt-F2... :-(

Are you using kwin?  If so, don't do that (unless you really want it).  We probably need to rewrite this so that people don't follow all the beginning stuff.  That was us experimenting.  If  you want to use kwin, then you will have to deal with the loss of alt-f2.  You can get around it by adding the launch application applet on your panel or finding a script (I've seen them but don't know where they are at) to "rewire" alt-f2.  

> Hm, I tried the script, but I can only get the log-in page. How do you get past that?
When I go to the calendar through firefox, I get straight to the calendar not seeing the log-in page.

You need to replace the website "http://www.google.com/calendar" with your personal calendar address that google gives you.  You can find out what that is by logging into google calendar, click on manage calendars at the bottom left of the page, then click on your calendar.  At the bottom you should see Private Calendar.  Click on the html button then use the site given you.

---

### Post by Auslegung on 2008-03-24
I know this is a dated thread but I'd like to revive it.  This is similar but I don't think your workaround solves my problem.  I want the picture at <http://www.die.net/earth/?zoom=1> to be my desktop and update with it as it updates (every three hours).  Anyone know how I do that?

---

### Post by harty83 on 2008-03-24
> **Auslegung said:**
> I know this is a dated thread but I'd like to revive it.  This is similar but I don't think your workaround solves my problem.  I want the picture at <http://www.die.net/earth/?zoom=1> to be my desktop and update with it as it updates (every three hours).  Anyone know how I do that?

Use the instructions in the first post to create the script using the website you want.  Then create a cron job to run every three hours to update the background.

In a terminal
```

crontab -e

```

```

# m h  dom mon dow   command
0 */3 * * * export DISPLAY=:0 && /usr/bin/web-snapshot > /tmp/web-snapshot.txt

```

Ctrl - O to save and Ctrl - X to exit

---

### Post by Auslegung on 2008-03-24
Wow, thanks for the speedy reply, but I thought you said installing kdesktop wasn't ideal.  It was a whole lotta work for not a whole lotta fun, to quote Kevin James.  I'd rather just keep it simple and if 8.04 might make it easier I'll wait until then.  Aren't I going to hit the same problems you did when you installed kdesktop?

---

### Post by ryanhaigh on 2008-07-04
Its likely that the kwebdesktop binary is provided by the kdesktop package. As you can see the script doesn't actually use kdesktop to display the image.

---

### Post by harty83 on 2008-07-04
> **ryanhaigh said:**
> Its likely that the kwebdesktop binary is provided by the kdesktop package. As you can see the script doesn't actually use kdesktop to display the image.

That is correct.

---

