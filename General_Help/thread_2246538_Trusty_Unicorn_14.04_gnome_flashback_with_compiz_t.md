---
title: "Trusty Unicorn 14.04 gnome flashback with compiz top indicator still does not work?"
date: 2014-10-01
forum: General Help
---

### Post by Cavsfan on 2014-10-01
Just wondering why this LTS is at the 1 point release and the top right logout/restart/shutdown, etc. indicator still does not work

[ATTACH=CONFIG]256865[/ATTACH]

When I click logout or shutdown it does absolutely nothing. Suspend works I believe but why can I not logout/restart/shutdown by clicking on that. 
On Precise you click on shutdown and that brings up a window and on the left is restart and on the right is shutdown. That works. Why doesn't Trusty work?

I tried purging and reinstalling indicator applet complete to no avail.

```
cavsfan@cavsfan-desktop:~$ apt-cache policy indicator-applet-complete
indicator-applet-complete:
  Installed: 12.10.2+14.04.20140403-0ubuntu1
  Candidate: 12.10.2+14.04.20140403-0ubuntu1
  Version table:
 *** 12.10.2+14.04.20140403-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
        100 /var/lib/dpkg/status
```
  
I shouldn't have to rely on Cairo Dock to logout, restart, etc.

---

### Post by mc4man on 2014-10-01
Not sure, works fine here.
As in screen note I have Log Out, Restart & Shutdown options, the Restart & Shutdown open their own specific dialogs unlike an ubuntu session where both open the same 2 option dialog

Also see you don't have a guest option, did you remove it?

---

### Post by Cavsfan on 2014-10-01
> **mc4man said:**
> Not sure, works fine here.
As in screen note I have Log Out, Restart & Shutdown options, the Restart & Shutdown open their own specific dialogs unlike an ubuntu session where both open the same 2 option dialog

Also see you don't have a guest option, did you remove it?

That is odd as I installed Trusty on this partition after final release from the ISO.
I have had restart appear randomly and then disappear. It hasn't been there in quite a while.
I just thought it would eventually be fixed but not on my system.

Yes, I think I disabled the guest account.

---

### Post by mc4man on 2014-10-01
might as well try a new user account to see..

side note:
for ubuntu session (unity) there has been an on going issue with both restart & shutdown opening the same dialog with shutdown highlighted but that shouldn't have any effect on flashback.
(in  some 14.04 install in the unity session the restart option will disappear after 6-10 sec after login, on others it is always there. On one of my 14.04 installs it disappears, on the other it doesn't
[https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/1203355/+attachment/4086148/+files/Apr-17-14-07%3A33.mp4](https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/1203355/+attachment/4086148/+files/Apr-17-14-07%3A33.mp4)

---

### Post by mc4man on 2014-10-01
Does the dialog from this work in your flashback?
```
dbus-send --session --dest=org.gnome.SessionManager --type=method_call --print-reply --reply-timeout=2000 /org/gnome/SessionManager org.gnome.SessionManager.Shutdown
```

---

### Post by Cavsfan on 2014-10-01
> **mc4man said:**
> Does the dialog from this work in your flashback?
```
dbus-send --session --dest=org.gnome.SessionManager --type=method_call --print-reply --reply-timeout=2000 /org/gnome/SessionManager org.gnome.SessionManager.Shutdown
```

Yes that brought a box with suspend, shutdown, cancel and restart.

[ATTACH=CONFIG]256887[/ATTACH]

What does this mean?

On Utopic when I click shutdown, it takes me to a lightdm login screen. I can then click shutdown from the top right and then I see two boxes: the left is restart and the right is shutdown.

But on Trusty I don't even get that.

---

### Post by Cavsfan on 2014-10-01
I created another user and the icon in the top right looks like a fear and functions well when logged in as the new user.

[ATTACH=CONFIG]256893[/ATTACH]

The button on my logon looks like the power off icon you can add to the panel.

So if another user has full functionality of the button and I don't what do I do?

---

### Post by Cavsfan on 2014-10-02
So, I guess I'll just have to change my name to Peter? :p

---

### Post by Cavsfan on 2014-10-04
Would purging indicator-applet-complete and it's config files then rebooting and adding it back help?

---

### Post by Cavsfan on 2014-10-05
Well I purged indicator-applet-complete, rebooted and logged into the other account I created. 

Then I added it back and rebooted into the other account. Restart/Logoff/Shutdown no longer work on either login now.

---

### Post by mc4man on 2014-10-06
Would it be inconvenient to do the 'backup ~/.config/dconf/user file & try a new default  one'  thing?

---

### Post by Cavsfan on 2014-10-07
> **mc4man said:**
> Would it be inconvenient to do the 'backup ~/.config/dconf/user file & try a new default  one'  thing?

Not at all and I thought I looked in that folder and didn't find the user file. But when I checked it was there. :redface:

I booted into Precise, renamed the ~/.config/dconf/user file and booted back into Trusty and it was a Unity session which I changed via CSSM to a gnome flashback session.
However although the icon changed from the orange logout icon to the gear icon, logout and shutdown/restart still did not work.

When I rebooted again the icon was back to the orange one as before.

I cannot believe that didn't solve this problem! Any more ideas?

---

### Post by Cavsfan on 2014-10-07
Does this look right (that which is red):
```
cavsfan@cavsfan-desktop:~$ dbus-send --session --dest=org.gnome.SessionManager --type=method_call --print-reply --reply-timeout=2000 /org/gnome/SessionManager org.gnome.SessionManager.Shutdown
[COLOR=#ff0000]method return sender=:1.15 -> dest=:1.793 reply_serial=2[/COLOR]
```

I could purge flashback but it doesn't appear to take everything it installed when it was initially installed with it:

```
cavsfan@cavsfan-desktop:~$ sudo apt-get purge gnome-session-flashback
[sudo] password for cavsfan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gnome-session-flashback*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 289 kB disk space will be freed.
Do you want to continue? [Y/n] 
```

Or I could even do a clean install but with an LTS I don't understand why or why I have this problem.

I installed it after final release on April 17, 2014:
```
cavsfan@cavsfan-desktop:~$ ls -ld /var/log/installer | awk '{ print $6 " " $7 " " $8 }'
Apr 17 11:30
```

Was I too early? 
According to this [https://lists.ubuntu.com/archives/ubuntu-announce/2014-April/000182.html](https://lists.ubuntu.com/archives/ubuntu-announce/2014-April/000182.html)
It was not released until *Thu Apr 17 17:09:54 UTC 2014*

Shirley not! :p

---

### Post by CantankRus on 2014-10-07
The session menus in indicator-applet-complete have never worked here.
I just add the User menu applet.

P.S. If I fire up gnome-panel in the ubuntu/unity session the menus work.
Also suppressing the confirmation dialogues allows the menus to work in the fallback session.
```
gsettings set com.canonical.indicator.session suppress-logout-restart-shutdown true
```

---

### Post by Cavsfan on 2014-10-08
> **CantankRus said:**
> The session menus in indicator-applet-complete have never worked here.
I just add the User menu applet.

P.S. If I fire up gnome-panel in the ubuntu/unity session the menus work.
Also suppressing the confirmation dialogues allows the menus to work in the fallback session.
```
gsettings set com.canonical.indicator.session suppress-logout-restart-shutdown true
```

Thanks. I'll give that a shot. I just don't understand how they would let an LTS be like this. LTS versions are supposed to be above the rest.
I already deleted the ~/.config/dconf/user file from Utopic again. I think I'll let it stay in Unity for a while before trying Flashback.

---

### Post by Cavsfan on 2014-10-08
When I first logged in to Unity the logout/restart buttons didn't even work at the top right. :o

When I entered 
```
gsettings set com.canonical.indicator.session suppress-logout-restart-shutdown true
```

and clicking restart it worked. I wonder if you can make it give the warning and have it still work? I know the word suppress in that command does just that: does it without any further input.

Tomorrow I'll give flashback a whirl. Thanks  		CantankRus!

---

### Post by Cavsfan on 2014-10-09
Before the only thing that worked on that menu pulldown was suspend; logout, restart and shutdown never worked but now they do! :)
It works now in Flashback (with Comiz) with all of these installed:
```
cavsfan@cavsfan-desktop:~$ dpkg -l | grep indicator
ii  gir1.2-appindicator3-0.1                              12.10.1+13.10.20130920-0ubuntu4                     amd64        Typelib files for libappindicator3-1.
ii  indicator-applet                                      12.10.2+14.04.20140403-0ubuntu1                     amd64        GNOME panel indicator applet
ii  indicator-applet-complete                             12.10.2+14.04.20140403-0ubuntu1                     amd64        Clone of the GNOME panel indicator applet
ii  indicator-applet-session                              12.10.2+14.04.20140403-0ubuntu1                     amd64        Clone of the GNOME panel indicator applet
ii  indicator-application                                 12.10.1+14.04.20140407-0ubuntu1                     amd64        Application Indicators
ii  indicator-appmenu                                     13.01.0+14.04.20140404-0ubuntu1                     amd64        Indicator for application menus.
ii  indicator-bluetooth                                   0.0.6+14.04.20140207-0ubuntu2                       amd64        System bluetooth indicator.
ii  indicator-datetime                                    13.10.0+14.04.20140415.3-0ubuntu1                   amd64        Simple clock
ii  indicator-keyboard                                    0.0.0+14.04.20140410.1-0ubuntu1                     amd64        Keyboard indicator
ii  indicator-messages                                    13.10.1+14.04.20140410-0ubuntu1                     amd64        indicator that collects messages that need a response
ii  indicator-power                                       12.10.6+14.04.20140411-0ubuntu1                     amd64        Indicator showing power state.
ii  indicator-printers                                    0.1.7+14.04.20140527-0ubuntu1                       amd64        indicator showing active print jobs
ii  indicator-session                                     12.10.5+14.04.20140410-0ubuntu1                     amd64        indicator showing session management, status and user switching
ii  indicator-sound                                       12.10.2+14.04.20140401-0ubuntu1                     amd64        System sound indicator.
ii  libappindicator3-1                                    12.10.1+13.10.20130920-0ubuntu4                     amd64        Application Indicators
ii  libindicator3-7                                       12.10.2+14.04.20140402-0ubuntu1                     amd64        panel indicator applet - shared library
ii  sni-qt:amd64                                          0.2.6-0ubuntu1                                      amd64        indicator support for Qt
ii  telepathy-indicator                                   0.3.1+14.04.20140411-0ubuntu1                       amd64        Desktop service to integrate Telepathy with the messaging menu.

```

Not sure I need all of those but they are installed.

I was checking out that command a little and found these possibilities:
```
cavsfan@cavsfan-desktop:~$ gsettings list-keys com.canonical.indicator.session
show-real-name-on-panel
suppress-logout-menuitem
suppress-restart-menuitem
suppress-shutdown-menuitem
suppress-logout-restart-shutdown
user-show-menu
```

I wonder if there is a way to bring back the warning like "Are you sure you want to logoff?".
Just curious but I am happy as is - at least it works. 

Thanks again!

---

### Post by Cavsfan on 2015-03-31
> **CantankRus said:**
> The session menus in indicator-applet-complete have never worked here.
I just add the User menu applet.

P.S. If I fire up gnome-panel in the ubuntu/unity session the menus work.
Also suppressing the confirmation dialogues allows the menus to work in the fallback session.
```
gsettings set com.canonical.indicator.session suppress-logout-restart-shutdown true
```

That also worked like a dream on a fresh install of Mint 17.1 Rebecca. I would click restart and it would just logout. Then I'd have to find where the button at the top was and click restart.
Too much trouble to take 2 separate actions just to restart. Fixed once again. :)

Thanks again CantankRus!

---

### Post by CantankRus on 2015-04-01
Hi Cavsfan,
I suppose you solved your original problem?
Found out it was caused by Plank in my case and probably cairo-dock in yours.
Probably fixed now.
[https://bugs.launchpad.net/cairo-dock-core/+bug/1242112](https://bugs.launchpad.net/cairo-dock-core/+bug/1242112)

---

### Post by Cavsfan on 2015-04-01
> **CantankRus said:**
> Hi Cavsfan,
I suppose you solved your original problem?
Found out it was caused by Plank in my case and probably cairo-dock in yours.
Probably fixed now.
[https://bugs.launchpad.net/cairo-dock-core/+bug/1242112](https://bugs.launchpad.net/cairo-dock-core/+bug/1242112)

Hi CantankRus,
That fix of yours cured my trusty FB session a long time ago.
But I installed Mint 17.1 a week or so ago which is based on Trusty and it's FB had the same problem.
Your fix did fix that problem in Mint as well. I'd like to see a prompt "Do you really want to restart?" but more importantly, I'd rather have a working restart button.
So I'm good. Glad I remembered where to find your command.

It must not be fixed either. I would not have had the problem especially in Mint. So it's probably still in Trusty FB session.
That bug also does not show any fix was released for Trusty cairo dock.
I would think more people would have had this problem.

---

### Post by Cavsfan on 2015-04-18
I just had to apply that to my fresh install (a week or so old) of 14.04.1 to get FB to restart. Once the restart disappeared and when it reappeared it just logged me out with only the option of shutting down.

So, this is indeed the fix for making all the functions - restart, logout and shutdown work in Trusty 14.04 FB.

```
gsettings set com.canonical.indicator.session suppress-logout-restart-shutdown true
```

---

