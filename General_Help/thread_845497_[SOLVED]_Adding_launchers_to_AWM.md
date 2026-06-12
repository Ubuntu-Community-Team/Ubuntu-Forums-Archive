---
title: "[SOLVED] Adding launchers to AWM"
date: 2008-06-30
forum: General Help
---

### Post by Foster Grant on 2008-06-30
The AWN manager's "Launcher Preferences" does not actually work and from what I've seen, that's well known. I found a tip online to add launchers directly via drag-and-drop from /usr/share/applications and was able to do that successfully for a short period of time, but that stopped working without warning and I haven't been able to add any more via drag-and-drop.

So how else may I add launcher icons to AWM? Hacking a prefs file ... working in terminal ... anything?

Bueller?

Bueller?

---

### Post by eryksun on 2008-07-01
> **Foster Grant said:**
> The AWN manager's "Launcher Preferences" does not actually work and from what I've seen, that's well known. 
....

I had no serious issues adding launchers with 'Launcher Preferences' on AWN 0.3.1, though it is a bit buggy. I use only two launchers, though: Firefox and Nautilus. I noticed when I added them that they initially came up twice in the list and did not immediately show up on the bar. However, everything started ok after I closed the bar and re-launched it, either from Gnome's 'Accessories' or with the command 'avant-window-navigator'.

---

### Post by magicmanfk on 2008-07-01
you might want to check which awn you're running... there's a bunch of different ones from the repos, and I think the one you install through add/remove programs isn't the best. I downloaded the necessary avant packages with the versions that ended in -bzr (such as avant-window-navigator-bzr), and I'm at the same point as the above user, where it's a little buggy but still works overall (I also have to manually add the icon for firefox and thunderbird). This was also the only way I could get the applets, if I remember correctly.

---

### Post by eryksun on 2008-07-01
> **magicmanfk said:**
> you might want to check which awn you're running... there's a bunch of different ones from the repos, and I think the one you install through add/remove programs isn't the best.... This was also the only way I could get the applets, if I remember correctly.

Yes, the official Ubuntu package was on my system just long enough for me to find another repository. The developer that packaged awn for Ubuntu wasn't able to work out some QA issues with the applets before Canonical's package freeze, so we only got the navigator. I like living on the bleeding edge, and wasting time with constant updates and bugs, so I'm using [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu).

---

### Post by Foster Grant on 2008-07-07
Update ...

As I've planned for months, when Hardy was bumped up to 8.04.1 last week I upgraded from Gutsy to Hardy. At the same time, I upgraded AWM to version 0.3.1 via the PPA at the AWN web site.

I still can't add launchers via drag-and-drop, awn-manager's dialog box or anything else.

Where does AWN hide its prefs file? (It's apparently not in a hidden directory in my /home folder.) Is it something that I can adjust by hand?

---

### Post by eryksun on 2008-07-08
> **Foster Grant said:**
> Where does AWN hide its prefs file? (It's apparently not in a hidden directory in my /home folder.) Is it something that I can adjust by hand?

The preferences are stored in the GNOME configuration system, GConf. There's a decent GUI, gconf-editor, that you can use to manually modify AWN's settings. Navigate to 

```
/apps/avant-window-navigator/window_manager
```

and update the key called 'launchers'. It's a list of .desktop files that define the parameters and icons. Just extend the list with however many new entries you need using the following scheme (replace '~' with your '/home/user'):

```
~/.config/awn/launchers/awn_launcher-1.desktop
~/.config/awn/launchers/awn_launcher-2.desktop
~/.config/awn/launchers/awn_launcher-3.desktop
etc...
```

Then edit/copy the existing .desktop files in ~/.config/awn/launchers/ to suit your needs.

---

### Post by Foster Grant on 2008-07-08
> **eryksun said:**
> The preferences are stored in the GNOME configuration system, GConf. There's a decent GUI, gconf-editor, that you can use to manually modify AWN's settings. Navigate to 

```
/apps/avant-window-navigator/window_manager
```

and update the key called 'launchers'. It's a list of .desktop files that define the parameters and icons. Just extend the list with however many new entries you need using the following scheme (replace '~' with your '/home/user'):

```
~/.config/awn/launchers/awn_launcher-1.desktop
~/.config/awn/launchers/awn_launcher-2.desktop
~/.config/awn/launchers/awn_launcher-3.desktop
etc...
```

This works with one caveat: the launchers listed in the GNOME Configuration Editor's AWN keys are of this format:

```
/usr/share/applications/APPLICATION_NAME.desktop
```

And once that's done, AWN has to be restarted.

> Then edit/copy the existing .desktop files in ~/.config/awn/launchers/ to suit your needs.

Empty directory. Don't seem to need to do that, though.

Thanks! :grin:

---

### Post by eryksun on 2008-07-08
My own setup probably uses local .desktop files because I used Awn to configure the launchers rather than dragging and dropping launchers from the desktop. I didn't want to suggest using the DE's .desktop files and possibly break your Awn installation. Anyway, it's cool to know that there's no special order to the file names. I'll probably change my setup to point to the .desktop files in /usr/share/applications. Thanks.

> **Foster Grant said:**
> This works with one caveat: the launchers listed in the GNOME Configuration Editor's AWN keys are of this format:

```
/usr/share/applications/APPLICATION_NAME.desktop
```

And once that's done, AWN has to be restarted.



Empty directory. Don't seem to need to do that, though.

Thanks! :grin:

---

