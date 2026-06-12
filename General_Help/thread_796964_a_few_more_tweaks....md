---
title: "a few more tweaks..."
date: 2008-05-16
forum: General Help
---

### Post by Wangberg on 2008-05-16
1. how do i prevent all icons in the notification area of my panel from launching with a single click. I want double click to open items, not single.

2. where can i install fonts for GIMP ? 

3. how do i prevent gnome from reopening all programs after i "sudo reboot"?  The option is unchecked in the sessions manager, but it keeps happening.  

4. how do i prevent evolution from resetting itself and forcing me to have to reset the view panes every time it launches....I am sick of ctrl+m 

5. how do i disable the most annoying autoupdate notifier in the tray?  

6. how do i get nm-applet (biggest piece of crap) out of my task bar?  

7. how do i get the icons on my desktop to actually "keep aligned" ?  they never conform to a grid or matrix unless i uncheck "keep aligned" and recheck it...

any help will go much appreciated!!! Thanks!

---

### Post by chewearn on 2008-05-17
I will try to give some answers, but they might not be to your satisfaction (you sounds like an easily frustrated person :mrgreen:).


[B][I]1. how do i prevent all icons in the notification area of my panel from launching with a single click. I want double click to open items, not single.
[/I][/B] 
I'm not sure what you mean.  If you single click on a notification-area icon, the menu pops up.  Right-click and left-click usually give you different menus.  Do you want to double-left-click and double-right-click instead?  Not sure if this is possible, really.  I'm not aware any other OS does it this way.


[B][I]2. where can i install fonts for GIMP ? 
[/I][/B] 
I'm not sure if this work for Gimp (I assumed it will be).  The usual way to install fonts are to simply copy them into /usr/share/fonts directory.


[I][B]5. how do i disable the most annoying autoupdate notifier in the tray?  
[/B][/I] 
You can set the auto-update to be automatic without user intervention, or reduce the frequency of checks.  But this could be risky; it's best to know what you are updating before doing it.  The said setting is under:
System > Administration > Software Sources
Go to the "Updates" tab.


[B][I]6. how do i get nm-applet (biggest piece of crap) out of my task bar?  
[/I][/B] 
Removing the icon only is not possible without some shenanigan.  It currently put under ubuntu wishlist:
[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/115031](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/115031)

You might be able to uninstall it; I have no experience in this and will not suggest a method.  If you break something, it's won't be by my prompting. :mrgreen:


I skipped those questions to which (in my humble opinion) I don't have a good answers.  I do have some bad answers, but I will keep it to myself :mrgreen:

.

---

### Post by warjowuch on 2008-05-17
the nm-applet you can uninstall by searching in synaptic for network-manager. This should give 2 networkmanager, one with -gnome on the end.
Do NOT uninstall the other one, only the -gnome-variant. The other one breaks your networking-capability and since there is no network, it's very hard to reïnstall the package again :-)

---

### Post by steveneddy on 2008-05-17
1. how do i prevent all icons in the notification area of my panel from launching with a single click. I want double click to open items, not single.

**I think that's a "feature"**

2. where can i install fonts for GIMP ? 

**~./fonts - this is in your /home folder and is a hidden file denoted by the "."before the / **

3. how do i prevent gnome from reopening all programs after i "sudo reboot"?  The option is unchecked in the sessions manager, but it keeps happening.  

**What happens when you hit the "start button" and reboot from there?**

4. how do i prevent evolution from resetting itself and forcing me to have to reset the view panes every time it launches....I am sick of ctrl+m 
[B]
I don't use Evolution, I can't help you there.[/B]

5. how do i disable the most annoying autoupdate notifier in the tray?  
[B]
open gconf-editor in terminal and go to

[COLOR="Red"]apps --> update notifier[/COLOR]

and check no_show_notifications[/B]

6. how do i get nm-applet (biggest piece of crap) out of my task bar? 

[B]Go to [COLOR="Red"]System --> Preferences --> Sessions[/COLOR] and in the Startup Programs tab, [COLOR="RoyalBlue"]uncheck Network Manager[/COLOR] and re-boot.

_[COLOR="Red"]Do not uninstall Network Manager![/COLOR]_ Just stop it from starting up at start up is sufficient.

how will you connect to the internet?

I use [COLOR="Red"]network-config[/COLOR] [/B]

7. how do i get the icons on my desktop to actually "keep aligned" ?  they never conform to a grid or matrix unless i uncheck "keep aligned" and recheck it...

[B]I wonder why they are moving? Are you changing your resolution all the time or something?

I don't know.[/B]

You might try digging around in gonf-editor to see if you can change what you want to change there.

Good luck.

---

### Post by Wangberg on 2008-05-17
> **AstalaVista said:**
> I will try to give some answers, but they might not be to your satisfaction (you sounds like an easily frustrated person :mrgreen:).


naw, just picky the way my desktop runs.  Most of these tweaks i'm asking for, like no single click in panel, are the way fedora defaults, or the way i prefer an OS to function.  

> 
[B][I]1. how do i prevent all icons in the notification area of my panel from launching with a single click. I want double click to open items, not single.
[/I][/B] 
I'm not sure what you mean.  If you single click on a notification-area icon, the menu pops up.  Right-click and left-click usually give you different menus.  Do you want to double-left-click and double-right-click instead?  Not sure if this is possible, really.  I'm not aware any other OS does it this way.


Fedora does it this way.  All the icons in the notification area of the panel in addition to some others which do not reside in the notification area (volume applet), all launch with a single click.  By the same token, icons for applications like terminal, calc, amarok, are in my panel and SHOULD be launched with a single click....at the very least, nothing in the notification area should launch with a single click.  


Thanks for everything thus far!!!

---

### Post by Wangberg on 2008-05-17
> **steveneddy said:**
> 1. how do i prevent all icons in the notification area of my panel from launching with a single click. I want double click to open items, not single.

**I think that's a "feature"**


no...

> 
2. where can i install fonts for GIMP ? 

**~./fonts - this is in your /home folder and is a hidden file denoted by the "."before the / **


Thank You!

> 
3. how do i prevent gnome from reopening all programs after i "sudo reboot"?  The option is unchecked in the sessions manager, but it keeps happening.  

**What happens when you hit the "start button" and reboot from there?**


the same thing...everything is saved, and relaunches upon boot.  This is ridiculously annoying....

> 
5. how do i disable the most annoying autoupdate notifier in the tray?  
[B]
open gconf-editor in terminal and go to

[COLOR="Red"]apps --> update notifier[/COLOR]

and check no_show_notifications[/B]


THANK YOU!

> 
7. how do i get the icons on my desktop to actually "keep aligned" ?  they never conform to a grid or matrix unless i uncheck "keep aligned" and recheck it...

[B]I wonder why they are moving? Are you changing your resolution all the time or something?

I don't know.[/B]

You might try digging around in gonf-editor to see if you can change what you want to change there.

Good luck.

nah, i'm not changing resolution or anything.  If i move an icon it goes where it put it, which is nice, but would prefer if it stayed aligned in a matrix format.

---

### Post by potatan on 2008-05-17
> **Wangberg said:**
> nah, i'm not changing resolution or anything. If i move an icon it goes where it put it, which is nice, but would prefer if it stayed aligned in a matrix format.

Right-click a blank part of the desktop, make sure that "Keep aligned" is ticked.

---

### Post by steveneddy on 2008-05-25
> **potatan said:**
> Right-click a blank part of the desktop, make sure that "Keep aligned" is ticked.

I just came back to this thread today and i was gonna say that same thing.

Thank you.

---

