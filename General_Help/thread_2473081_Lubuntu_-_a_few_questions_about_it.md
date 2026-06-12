---
title: "Lubuntu - a few questions about it"
date: 2022-03-22
forum: General Help
---

### Post by jmichaels29 on 2022-03-22
OK, for those that followed my other thread, I installed a 120 GB SSD (and a new battery) on my 81 year old aunt's aging computer - an HP 2000 Notebook PC.  I then installed Lubuntu on it.
The boot up time went from 2 minutes and 40 seconds (Using Ubunt 20.04 LTS with the old HD)  to just 40 seconds (with Lubuntu and the new SDD).  Very good.  Everything else is snappier too.  Perhaps in the future I'll throw some more ram at it, but not for now.  It only has 2GB of factory ram, so later I'll throw more at it.   All she uses it for is facebook anyways.
  
Some Lubuntu questions.

1) Is "System Monitor" on Lubuntu somewhere
2) Where does one go to access the Ubuntu Software Center (might need that to install system monitor)
3) On Ubuntu I had the resolution of the screen set to 800x600 for her eye sight.  Where would I go (to find the settings for) to change the screen resolution to 800x600 now.
4)  I'd like Firefox to startup upon boot - how to?  A "startup items" should be somewhere on Lubuntu, eh?
5) Is there a way to "Search your computer" - like Ubuntu has ?

Thanks much in advance1

Regards,

MJ

---

### Post by guiverc on 2022-03-22
The Lubuntu manual can be found at [https://manual.lubuntu.me/stable/](https://manual.lubuntu.me/stable/)

You didn't mention a release; thus the link I provided was for the latest *stable* release, ie. Lubuntu 21.10.  To read the manual for the latest *lts* release (currently 20.04) change the word "*stable*" in the URL to say "*lts*".  I'll use *stable* links here though (ie. 21.10); as whilst you mentioned Ubuntu was 20.04, you didn't mention Lubuntu release.

To add software, it's covered in Chapter 4 - [https://manual.lubuntu.me/stable/4/Installing_Updating_and_Removing_Software.html](https://manual.lubuntu.me/stable/4/Installing_Updating_and_Removing_Software.html) where you'll note it covers
- [Chapter 4.1 - Discover Software Center]("https://manual.lubuntu.me/stable/4/4.1/discover.html")
- [Chapter 4.2 - Muon Package Manager]("https://manual.lubuntu.me/stable/4/4.2/muon.html")
and more

The *graphical task manager* provided with Lubuntu can be found here in the manual - [https://manual.lubuntu.me/stable/3/3.1/3.1.6/qps.html](https://manual.lubuntu.me/stable/3/3.1/3.1.6/qps.html) , though a terminal based application is provided as well which can be found here in the manual - [https://manual.lubuntu.me/stable/3/3.1/3.1.2/htop.html](https://manual.lubuntu.me/stable/3/3.1/3.1.2/htop.html)

Monitor settings can be found here - [https://manual.lubuntu.me/stable/3/3.2/3.2.10/monitor_settings.html](https://manual.lubuntu.me/stable/3/3.2/3.2.10/monitor_settings.html)  (*which includes resolution changes*)

Session settings can be found here (ie. autostart features) - [https://manual.lubuntu.me/stable/3/3.2/3.2.13/session_settings](https://manual.lubuntu.me/stable/3/3.2/3.2.13/session_settings).

To search for applications there is `lxqt-runner` - [https://manual.lubuntu.me/stable/5/5.3/lxqt-runner.html](https://manual.lubuntu.me/stable/5/5.3/lxqt-runner.html) though it also provides some basic features as can act like a simple calculator too (*example use in the manual is having it calculate 2+2=*) but it doesn't search for files.

---

### Post by jmichaels29 on 2022-03-22
Thanks so much!
& yes it's the latest relese of Lubuntu (version 21.10 sounds like what I clicked to download)....

Thanks again!

ML

---

### Post by jmichaels29 on 2022-03-23
ok, I need a little help with "startup items."

I found Application Autostart in LXQt Session Settings.  I clicked auto start, then it asks for the "name" and the "command" and even has a search box.

I added Firefox by locating it in Applications->Internet->Firefox Web  Browser

However, no Firefox Browser upon startup.

---

### Post by VanillaMozilla on 2022-03-23
The command to start firefox is probably
firefox %u
To find the executable location:  In a terminal type
which firefox
On my computer it is /usr/bin/firefox

---

### Post by guiverc on 2022-03-23
I'd suggest opening a terminal, eg. I'd use Ctrl+Alt+T to do it, but use whatever works for you.

I'd then ask the system where it's located; eg.

```
guiverc@d960-ubu2:~/.config$   whereis firefox
firefox: /usr/bin/firefox /etc/firefox /snap/bin/firefox

```

If I wanted to ensure the command works; I'd just enter it, eg.

```
guiverc@d960-ubu2:~/.config$   firefox
xdg-settings: $BROWSER is set and can't be changed with xdg-settings
Gtk-Message: 15:10:24.377: Failed to load module "appmenu-gtk-module"

```

and I see the messages I copy/pasted ^ and a Mozilla Firefox window has opened on my other screen....

Note:  I'm **not** using Lubuntu 21.10 so my results will almost certainly not match what you'll get, but I've opted to use this box (*my primary jammy box*) in hopes you'll understand what I'm trying to say & hopefully work out the answer for yourself :P


Looking at this box; one autostart option I believe I've created is

Name:        play ubuntu sound on login
Command:  paplay /usr/share/sounds/ubuntu/stereo/desktop-login.ogg

ie. the command `paplay /usr/share/sounds/ubuntu/stereo/desktop-login.ogg` executed at login so I have a sound like Ubuntu of old used to have; the command being `paplay` (or pulse-audio-play) with the path of what sound file I want to play..  I can't recall if that's a default sound for included by default with Lubuntu (*and I'm not going to look*) but it's from the `ubuntu-sounds` package

If you have questions; as always just ask. Myself (*in my round about way*) or someone else will usually give you what you need/want.

*FYI:  if it looks like there are a lot of space between the "$" in the prompt and my command; that's intentional as I don't want commands I execute on my box for paste into support or queries like this (for others) appearing in my command history; the space(s) before the command ensure this :P*

---

### Post by jmichaels29 on 2022-03-23
I got, by clicking serach and scrolling around, I clicked right to it in Applications->Internet->FioreFox Browser
But no go on startup.
I'll try some of your suggestions in about an hour.

Firefox now shows up in the Application Autostartup Window.

Attachment to what I've accomplished thus far:

---

### Post by jmichaels29 on 2022-03-23
And the attachment where Firefox browser is actually showing up in the list, but still not working on startup..

For some reason, I couldn't get the attachment to take - maybe I have too many photos in there....

Anyways, Now, Ima try some of your suggestions

---

### Post by jmichaels29 on 2022-03-23
> **VanillaMozilla said:**
> The command to start firefox is probably
firefox %u
To find the executable location:  In a terminal type
which firefox
On my computer it is /usr/bin/firefox


That worked!

Thank you very much!

---

### Post by guiverc on 2022-03-23
Your picture (*which didn't show the full image*) appeared to be a .desktop file which is **not **executable except to the desktop itself (that reads the file as per [https://specifications.freedesktop.org/desktop-entry-spec/latest/](https://specifications.freedesktop.org/desktop-entry-spec/latest/) rules).

If you wanted the command within it, you should have `cat`, `view` (ie. *commands that show the contents of the file*) or opened the file in a text editor to see what it actually run via the command inside.

In my prior example; as I'm using the `firefox` snap the executable is 
```
/snap/bin/firefox
```

however the script found at

 ```
`/usr/bin/firefox`
```

would have also checked the environment then ran the same executable anyway... as it's final line was the command  

```
exec /snap/bin/firefox "$@"
```

ie. for my *jammy* system the `/snap/bin/firefox` is what I'd execute.

If i'm unsure, I could ask the system what the various options it gave me were, ie.

```

guiverc@d960-ubu2:~/Desktop$   file /usr/bin/firefox
/usr/bin/firefox: POSIX shell script, ASCII text executable
guiverc@d960-ubu2:~/Desktop$   file /snap/bin/firefox
/snap/bin/firefox: symbolic link to /usr/bin/snap
guiverc@d960-ubu2:~/Desktop$   file /etc/firefox
/etc/firefox: directory
```

The `firefox` snap actually runs as snap with `firefox being the name of the snap that executes.

Your system won't contain the *snap* of firefox by default; it was the default only for Ubuntu 21.10 (*not flavors like Lubuntu*). When you upgrade to 22.04 it'll become a *snap* package.

---

### Post by jmichaels29 on 2022-03-23
I would like to thank you all.  I have the system set up perfectly.  I  even splurged and bought 2 GB more ram for it - it actually came with 4  GB (thought it had only 2GB until I installed the Gnome System Monitor).
Well, new battery, an SSD drive, 2 more GB ram (coming), and put Lubuntu on it.  It feels like a new compouter!
Special thanks to guiverc for the most invaluable links to the users manual of Lubuntu !

Regards,

MJ

---

### Post by jmichaels29 on 2022-03-23
> **guiverc said:**
> Your picture (*which didn't show the full image*) appeared to be a .desktop file which is **not **executable except to the desktop itself (that reads the file as per [https://specifications.freedesktop.org/desktop-entry-spec/latest/](https://specifications.freedesktop.org/desktop-entry-spec/latest/) rules).

If you wanted the command within it, you should have `cat`, `view` (ie. *commands that show the contents of the file*) or opened the file in a text editor to see what it actually run via the command inside.

In my prior example; as I'm using the `firefox` snap the executable is 
```
/snap/bin/firefox
```

however the script found at

 ```
`/usr/bin/firefox`
```

would have also checked the environment then ran the same executable anyway... as it's final line was the command  

```
exec /snap/bin/firefox "$@"
```

ie. for my *jammy* system the `/snap/bin/firefox` is what I'd execute.

If i'm unsure, I could ask the system what the various options it gave me were, ie.

```

guiverc@d960-ubu2:~/Desktop$   file /usr/bin/firefox
/usr/bin/firefox: POSIX shell script, ASCII text executable
guiverc@d960-ubu2:~/Desktop$   file /snap/bin/firefox
/snap/bin/firefox: symbolic link to /usr/bin/snap
guiverc@d960-ubu2:~/Desktop$   file /etc/firefox
/etc/firefox: directory
```

The `firefox` snap actually runs as snap with `firefox being the name of the snap that executes.

Your system won't contain the *snap* of firefox by default; it was the default only for Ubuntu 21.10 (*not flavors like Lubuntu*). When you upgrade to 22.04 it'll become a *snap* package.

Is it ok to use the "firefox %u"  in the Startup items since it's working?   Or is advisable to use what you have suggested.   (?)

Regards,

MJ

---

### Post by jmichaels29 on 2022-03-23
One last question if anyone is still following this.

In Lubuntu, how do I change the Wallpaper/background image of screen?

I found how to tinker with the screen saver, but not the wallpaper.

Regards,

ML

---

### Post by guiverc on 2022-03-23
Yep it's 100% fine to use just `firefox` given it works.

Your choice will still work when you *release-upgrade* to Lubuntu 22.04 LTS I'd expect to, where as what I suggested (ie. a full path) may not have (*depending which path you used*).

For changing the wallpaper; look at [https://manual.lubuntu.me/stable/3/3.2/3.2.5/desktop.html](https://manual.lubuntu.me/stable/3/3.2/3.2.5/desktop.html)

There is a *search* function in the manual; I'd suggest trying it, as it'll suggest two different pages which give you more options, ie. [https://manual.lubuntu.me/stable/search.html?q=wallpaper&check_keywords=yes&area=default](https://manual.lubuntu.me/stable/search.html?q=wallpaper&check_keywords=yes&area=default) ie. you can use themes that include a specific/change of wallpaper too.

We also have some more documentation at our discourse site, ie. [https://discourse.lubuntu.me/c/documentation/20](https://discourse.lubuntu.me/c/documentation/20) though in most cases the best documentation is in the manual (*odds & ends end up at the discourse** though for some topics (eg. swap) that's where you need to go*)

---

### Post by ActionParsnip on 2022-03-23
You can get rid of the warning with:
```

sudo apt-get install appmenu-gtk2-module appmenu-gtk3-module

```

Source:
[https://askubuntu.com/questions/1074926/failed-to-load-module-appmenu-gtk-module-canberra-gtk-module](https://askubuntu.com/questions/1074926/failed-to-load-module-appmenu-gtk-module-canberra-gtk-module)

---

### Post by GhX6GZMB on 2022-03-23
> **jmichaels29 said:**
> One last question if anyone is still following this.

In Lubuntu, how do I change the Wallpaper/background image of screen?


Menu: Preferences -> LXQt settings -> Desktop

For best result, find an image that matches your screen resolution.

You can store it anywhere, default is
```
/usr/share/sddm/themes/lubuntu/wall.png
```
Cheers.

---

### Post by jmichaels29 on 2022-03-23
Ok, for kicks, I'm trying to change the wallpaper in Lubuntu.
 
I've selected the 2110-friends-dark.png, by double clicking it, which is one of the wallpaper files that comes with it, and can't get it to work. 

See the attached 4 images to what I've accessed on those screens.  I even shutdown/restarted and no luck.  Well, I tried to attach 4 images, but it would only take 3.

---

### Post by guiverc on 2022-03-24
Are you clicking the APPLY button at the bottom


Note: *I can't see it in your picture; is your screen resolution large enough for LXQt? - which has an [implied]("https://github.com/lxqt/lxqt/issues/1731") minimum size for operation? to prevent dialogs from opening without the OK/CANCEL/APPLY button from appearing off-screen*.  *I do recall you mentioning changing screen resolution and I didn't think to mention minimum resolution sorry.*

---

### Post by jmichaels29 on 2022-03-24
> **guiverc said:**
> Are you clicking the APPLY button at the bottom


Note: *I can't see it in your picture; is your screen resolution large enough for LXQt? - which has an [implied]("https://github.com/lxqt/lxqt/issues/1731") minimum size for operation? to prevent dialogs from opening without the OK/CANCEL/APPLY button from appearing off-screen*.  *I do recall you mentioning changing screen resolution and I didn't think to mention minimum resolution sorry.*

Good question.  I will fire up the laptop and take a look for the "Apply" button.  In the 3 photos I attached above, I don't see an "Apply" button available....

I'll report back...

---

### Post by GhX6GZMB on 2022-03-24
@jmichaels29:
My apologies, I sent you on a wild goose chase. There's a lot of redirection in the wallpaper setup for Lubuntu, I'd forgotten about that.
Default is:
```
/usr/share/sddm/themes/lubuntu/wall.png
``` 
but this redirects to:
```
/usr/share/lubuntu/wallpapers/lubuntu-default-wallpaper.png
```
which again redirects to the actual wallpaper file.
Inspect this file (right-click, Properties) to see where the _real_ xxx.png resides and what it's called.

Either store your own .png renamed to the existing file name, or modify the lubuntu-default-wallpaper.png to point to your graphic file.

All file permisssions should be: root:root  rw-r--r--

---

### Post by guiverc on 2022-03-24
> **jmichaels29 said:**
> Good question.  I will fire up the laptop and take a look for the "Apply" button.  In the 3 photos I attached above, I don't see an "Apply" button available....

I'll report back...

There are buttons partially visible in the first photo of yours at least; if you made the panel disappear (*autohide*) when not in use you would see more of it.. but it's generally not an issue if resolution is 1280x1024 or higher. The buttons appear bottom right of the window.

Sorry I recall doing some QA (*Quality Assurance*) on low resolution displays many cycles ago (*possibly on request of Walter/wxl on the prior to his making the request upstream in the github link i used as I do recall using 19.04** as I had smaller screens on some i386 or 32bit hardware*)* but most my QA is done on 1280x1024 or better *(*I used 1024x768 up to 21.04 I think*)

---

### Post by jmichaels29 on 2022-03-24
> **guiverc said:**
> Are you clicking the APPLY button at the bottom


Note: *I can't see it in your picture; is your screen resolution large enough for LXQt? - which has an [implied]("https://github.com/lxqt/lxqt/issues/1731") minimum size for operation? to prevent dialogs from opening without the OK/CANCEL/APPLY button from appearing off-screen*.  *I do recall you mentioning changing screen resolution and I didn't think to mention minimum resolution sorry.*

ok, you've nailed the problem, which has brought up another problem:  I can't resize the windows so that I can actually see the apply button - I know it's down there, just can't access it.  I've tried using the little logo in top right of window, and also tried to resize the window by grabbing at, and attempting to hold mouse button down and dragging from the top left or top right - again, no luck....   So I need someone to tell me an alternative way to resize a window in Lubuntu...
 
Oh snap, I just thought of something, since I have the resolution set to 800x600, then that's why I can't see/access the apply button down there.   Problem solved..... Big Smiles!

---

### Post by jmichaels29 on 2022-03-24
> **guiverc said:**
> There are buttons partially visible in the first photo of yours at least; if you made the panel disappear (*autohide*) when not in use you would see more of it.. but it's generally not an issue if resolution is 1280x1024 or higher. The buttons appear bottom right of the window.

Sorry I recall doing some QA (*Quality Assurance*) on low resolution displays many cycles ago (*possibly on request of Walter/wxl on the prior to his making the request upstream in the github link i used as I do recall using 19.04** as I had smaller screens on some i386 or 32bit hardware*)* but most my QA is done on 1280x1024 or better *(*I used 1024x768 up to 21.04 I think*)

In my post I just made, I figured out, what you just typed, in the midst of typing it.  I'll just change the screen resolution, set the background/wallpaper, then resize the resolution back to larger for her aging eyes...
Thanks!

---

### Post by guiverc on 2022-03-24
> **jmichaels29 said:**
> ok, you've nailed the problem, which has brought up another problem:  I can't resize the windows so that I can actually see the apply button - I know it's down there, just can't access it.  I've tried using the little logo in top right of window, and also tried to resize the window by grabbing at, and attempting to hold mouse button down and dragging from the top left or top right - again, no luck....   So I need someone to tell me an alternative way to resize a window in Lubuntu...
 
Oh snap, I just thought of something, since I have the resolution set to 800x600, then that's why I can't see/access the apply button down there.   Problem solved..... Big Smiles!

I'll have to read & properly reply later (*if required*),  but you know you can re-size windows using ALT key then right-click+drag with the mouse...  That allows many dialogs to be resized smaller (*so scroll bars show*) & allows often you to drag the window up/down (*up in this case*) so you can get to what you need to.  That is found in the manual too *(sorry no time to go find link currently*).

*FYI:  you'll note the right-click-drag-resize assumes you want want to drag the corner of the window you're pointer is closest too... but it's pretty easy to work out how it works*

It doesn't work with all LXQt dialogs though; the bug reports with small.res are mostly about the ones where it doesn't work.

---

### Post by dragonfly41 on 2022-03-25
I offer this suggestion on accessibility. 
It aims to simplify as many operations for an elderly user by just one key operations.

Install Albert.
Create extensions (bash or python) required such as
- shutdown
- zoom screen
- send email requesting help
- etc.

Assign a hot key to each of these functions. 
For example to the far right of my keyboard I use [Num+Enter] to popup a query box.

Your can (optionally) improve accessibility for elderly user by attaching simple colour stickies to these few hot keys.

e.g. press Red - shutdown.

---

