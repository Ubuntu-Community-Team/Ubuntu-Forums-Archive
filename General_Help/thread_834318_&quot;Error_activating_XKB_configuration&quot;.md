---
title: "&quot;Error activating XKB configuration&quot;"
date: 2008-06-19
forum: General Help
---

### Post by serhalp on 2008-06-19
Greetings.

I'm running Ubuntu 8.04 (Hardy Heron). I just installed a bunch of recommended updates plus the closed-source ATI accelerated graphics driver. I ran into some problems (namely, my alt key stopped working for certain shortcuts and I couldn't access other workspaces), so I uninstalled it and reverted to the open source driver. To make a long story short, I now have a problem with my keyboard layout. From what I understand, I seem to have "dead keys" enabled (to get an apostrophe, I must type ', then space; same for double-quotes). I'm using the 'USA' layout with the 'Default' variant. Any time I log in or change anything in the 'Layouts' tab of the Keyboard preferences, I get the following error:

> Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10400090

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

**xprop -root | grep XKB**
> _XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "us", "", "lv3:ralt_switch"
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "us", "", "lv3:ralt_switch"

**gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd**
>  layouts = [us]
 model = pc105
 overrideSettings = false
 options = [lv3 lv3:ralt_switch]



I've tried several keyboard model settings, layouts and variants. I get the same error and the same 'dead keys' behavior with all combinations. I've also rebooted at several points.

I've followed the "successful" solutions of several users on these forums and others. I've unset the keys in /desktop/gnome/peripherals/keyboard/kbd from gconf-editor to reinitalize those settings and rebooted. I've tried it the other way around by commenting lines in /etc/X11/xorg.config and rebooting. I've removed the "scim" package as someone proposed. I've tried countless other proposed solutions as outlined in various forums, but to no avail.

Also, they often seem to suggest that 'dead keys' are part of the 'USA International' layout, which I am not using. There are also no 'dead keys' options under 'Layout Options' with which to work.

I'm stumped here. Does anyone have any idea what I could try next? I appreciate any help you could provide. Thank you!

---

### Post by Motorhead Kaze on 2008-06-27
Man!  Just no help huh?  I just posted a "Yeah me too!" on another very similar post.

I installed an ATI graphics card yesterday and did a lot of toying with the xorg.conf to get my dual monitors going together. At the SAME TIME I had an issue with Compiz just randomly turning itself on (I have desktop effect OFF) and turning my screen white! So, I did a lot of fixing...somewhere in there, my keyboard got switched from Japanese to an American one, and that is not good for me at all.

So yeah, I would really like to hear from somebody about how we fix this XKB thing!  (My error message was identical to yours)

---

### Post by Motorhead Kaze on 2008-06-27
This is what I just did:

Type this into a terminal
```
 gksudo gedit /etc/X11/xorg.conf

``` to access your xorg.conf and go to the section called, 
```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	
EndSection

```
I had all these options right after "driver 'kbd'" and deleted all of those options. Then I went to system/preferences/keyboard and reset my keyboard to the way I want it (Japanese keyboard, 106keys).  Now my keyboard is back to normal.

---

### Post by serhalp on 2008-07-02
Didn't do anything at all. I still get the same error every time I change the layout or any layout option and I still have dead keys enabled when they shouldn't be.

This problem is on my work computer - and I am a programmer. I've been dealing with it for nearly two weeks, and it's kind of a hassle... If anyone has any possible solution in mind, please let me know!

Thanks

---

### Post by serhalp on 2008-07-18
If anyone else still has this problem, let it be known that the latest updates to XKB have fixed my problem! After re-adding the default USA layout and removing the old one, everything was fixed! Huzzah.

---

### Post by vmisha on 2008-07-23
what exactly did you do...?

---

### Post by kaitenbushi on 2008-08-06
I went to System->Preferences->Keyboard->Layouts
Here I added pressed "Add...", and chose the layout I use, in my case, Japan, although I already had a Japan entry in my Selected layout list. Then I deleted the existing Japan entry. (If you had more than one existing entry, perhaps you might need to delete them as well.) Don't worry about error messages that pops up. Reboot. Everything OK.

If you later press "Reset to Defaults", you might get the same error again. If that is a source of frustration, you can play around with your /etc/X11/xorg.conf file, as Motorhead Kaze suggests.

Caveat: This is advise from a non-expert!

Let me know how it goes :)

---

### Post by elmicz on 2008-08-07
For me the trick was, to reinstall xkb-data

```
sudo aptitude reinstall xkb-data
```

Everything works fine again now :)

---

### Post by Dorian17xD on 2008-10-09
Hey elmicz!! THX A LOT!!

I worked around of it for hours!! I just did the same and my keyboard is working properly!! :D THX A LOT!!

---

### Post by BalancedOne on 2011-01-03
Hi people, I'm new here and new to Ubuntu too, I'm afraid. I'm having a  hard time switching from Windows to this as it is, and now  having to  deal with installation problems...But I decided to stick with Ubuntu,  rather than have a pirate Windows copy installed ( I have had a legit  copy that came with my laptop, but lost the CD's and can't get it  reinstalled).

OK, my problem is this: I bought a new HD for my  Toshiba, as the old one died. So I decided to go with Ubuntu on the new  HD. After following the steps to get Ubuntu installed from CD, at  [http://www.ehow.com/how_4963838_install-blank-laptop-hard-drive.html](http://www.ehow.com/how_4963838_install-blank-laptop-hard-drive.html), I  got as far as the page where I am asked to enter user name and password,  etc. There, the 'folow' button is no longer highlighted and I only have  the option to go 'back'. Which ofc I don't need :). Then, I suspended  the session, as it was my only option. After powering back on, i get the  following message: 

Error activating XKB configuration
X server version data: the x.org foundation 10900000

If you report this situation as a bug, please include:
-the result of xprop-root/grep XKB
-the result of gfconftool-2-r/desktop/gnome/peripherals/keyboard/kbd

This didn't help me much, so I suspended again and at restart I got this on a dark screen:

(process:300):glib-warning**:getpwuid_r():failed due to unknown user id(0)

Anyone can help with this? Thanks in advance guys.

---

