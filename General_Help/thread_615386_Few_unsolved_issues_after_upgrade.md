---
title: "Few unsolved issues after upgrade"
date: 2007-11-17
forum: General Help
---

### Post by tetrafuran on 2007-11-17
I upgraded from edgy to feisty and then to gutsy. I tried to search for solutions but I couldn't find any that I would have understood.

1) Gnome has only two virtual desktops, workspaces or what ever. In edgy there was a simple GUI tool for changing that. Where is it now? I need four desktops/workspaces. In a help file I found this:

> "1.6.3.&#8195;To Set the Number of Workspaces

To set a mandatory
number of workspaces, use the following command:

gconftool-2 --direct \
  --config-source xml:readwrite:/etc/gconf/gconf.xml.mandatory \
  --type int \
  --set /apps/metacity/general/num_workspaces integer

To set a default number of workspaces, use the following command:

gconftool-2 --direct \
  --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults \
  --type int \
  --set /apps/metacity/general/num_workspaces integer

You can also set other window manager preferences. For information on
the other window manager preferences, see the metacity.schemas
schema definition file."

I don't really understand how to use this.

2) Mostly I use xfce, but now it lost it's keyboard layouts. It has only us, but I need more than just one layout. I read about modifying xorg.conf but apparently gnome and xfce don't obey that file at all any more. Here's what I have in my etc/X11/xorg.conf.
```

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "fi,us"
# Option         "XkbOptions" "lv3:ralt_switch"
# This is the line that used to be there, 
# but most threads and guides didn't mention this line. 
# I added the one you see on the next line.
    Option         "XkbOptions"  "grp:alt_shift_toggle"
EndSection
```

3) Before login screen I'm getting the error "the greeter application appears to be crashing" I read about it, and it says I should un-select the "enable accessible login" in login window preferences - accessibility. The box was empty by default, but I tried ticking it anyway. Nothing happened. That option appears have nothing to do with the error no matter if the feature is on or off..

4) I can't change the login screen's appearance. The graphical tool for doing that exists, but it has no effect.

5) In xfce I used to edit the properties of screen savers. How can I do that now? I just realized that M$ Window$ can edit screen saver properties but gnome can't. In fact now xfce can't either. I wonder if KDE has the same problem.

Generally I'm quite happy with gutsy, but these little problems are hindering the experience. Lots of little things have changed for the better, and others have gone worse.

---

### Post by erginemr on 2007-11-17
Hello,

1 --> When you right click the desktops icon on the bottom-right corner of your screen, you should be able to increase the number of virtual desktops from the preferences or options pop-up menu item.

2 --> No idea, sorry.

3 --> I also had a similar problem in the past. Out of curiosity, I had enabled accessibility under login screen options. Then this problem occurred. It came back to normal after unchecking the accessibility.

4 & 5 --> Maybe this will be a wild guess, but the problem with the unability to change your settings (i.e. login screen and screensavers) may have something with the permissions. Can you please check that you (not root) have got all the permissions in your home folder by issuing the following command from the console:
ls -la

Take Care.

---

### Post by tetrafuran on 2007-11-17
1. Cool it worked. Thanks. This is once again one of the nice features of gutsy. Don't know if it existed before, but I like it.

4&5. There are lots of folders in there and some of them have only -rw----- rights. However most of them are tagged drwx-------.

Acually what I mean is that in edgy gnome the settings for screensavers didn't exist at all. You just select a screensaver and tahats it. In edgy's xfce I could modify various numbers concearning the behaviour of a specific screensaver. Usually I would modify speed and other varialbes. In "attraction" saver I would play around with number of balls, repulsion treshold, repulsion force etc. It was a lot of fun. Unfortunately now in gutsy there is no interface for modifying anything. in fact the options are the same in xfce and gnome. It's not a matter of permission. Perhaps the upgrading process removed those tools or something. You know, it does remove tons of "useless" and obsolete stuff.

Anyway thanks for the help so far.

---

