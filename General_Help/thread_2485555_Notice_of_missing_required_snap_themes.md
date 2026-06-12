---
title: "Notice of missing required snap themes"
date: 2023-04-02
forum: General Help
---

### Post by Dennis N on 2023-04-02
For the past several days, I am getting a popup notice with startups or restarts of the OS (Ubuntu 22.10): "some required theme snaps are missing...Would you like to install them now?"
Clicking on the notification, I then enter my authorization. 
Following that, every time, the following notice pops up: "Installing missing theme snaps: Failed".

Anyone else seen this?

My questions would be:
1) why are they failing to install and/or how to get them installed. (but there is no indication of what exact snaps these might be).
2) Otherwise, how to stop these messages. 

"snap refresh" reports all snaps are up to date.

Besides being annoying, the lack of these 'required' snap themes is having no affect on system operations.

Screenshots of the popups are attached &#8595;

---

### Post by MAFoElffen on 2023-04-02
Saw this answered at AskUbuntu: [https://askubuntu.com/questions/1404650/some-snap-apps-are-not-using-the-default-theme-yaru-in-ubuntu-22-04](https://askubuntu.com/questions/1404650/some-snap-apps-are-not-using-the-default-theme-yaru-in-ubuntu-22-04)

---

### Post by Dennis N on 2023-04-02
> **MAFoElffen said:**
> Saw this answered at AskUbuntu: [https://askubuntu.com/questions/1404650/some-snap-apps-are-not-using-the-default-theme-yaru-in-ubuntu-22-04](https://askubuntu.com/questions/1404650/some-snap-apps-are-not-using-the-default-theme-yaru-in-ubuntu-22-04)

I already had gtk-common-themes installed. 

Another bit of information: I have two Ubuntu 22.10 on different machines. I notice the other install does not get these notifications. You would think there would be some difference, but here are the snap packages on each:

From the affected Ubuntu 22.10 which gets the "missing themes" notice immediately after login:
```

dmn@Kayleigh:~$ snap list
Name                       Version          Rev    Tracking         Publisher   Notes
bare                       1.0              5      latest/stable    canonical&#10003;  base
core20                     20230308         1852   latest/stable    canonical&#10003;  base
core22                     20230316         583    latest/stable    canonical&#10003;  base
gnome-3-38-2004            0+git.6f39565    137    latest/stable/…  canonical&#10003;  -
gnome-42-2204              0+git.e7d97c7    68     latest/stable    canonical&#10003;  -
gtk-common-themes          0.1-81-g442e511  1535   latest/stable/…  canonical&#10003;  -
snapd                      2.58.3           18596  latest/stable    canonical&#10003;  snapd
snapd-desktop-integration  0.1              57     latest/stable/…  canonical&#10003;  -

```

and from the unaffected Ubuntu 22.10:
```
dmn@Tyana-vm:~$ snap list
Name                       Version          Rev    Tracking         Publisher   Notes
bare                       1.0              5      latest/stable    canonical&#10003;  base
core20                     20230308         1852   latest/stable    canonical&#10003;  base
core22                     20230316         583    latest/stable    canonical&#10003;  base
gnome-3-38-2004            0+git.6f39565    137    latest/stable/…  canonical&#10003;  -
gnome-42-2204              0+git.e7d97c7    68     latest/stable    canonical&#10003;  -
gtk-common-themes          0.1-81-g442e511  1535   latest/stable/…  canonical&#10003;  -
snapd                      2.58.3           18596  latest/stable    canonical&#10003;  snapd
snapd-desktop-integration  0.1              57     latest/stable/…  canonical&#10003; 

```
No differences!


And the messages are still appearing.

---

### Post by MAFoElffen on 2023-04-03
And that is the same version I have with 22.04...

---

### Post by Dennis N on 2023-04-05
Update: Today, 3 days after starting this thread, I received the same popup notification about "some required snap themes are missing...", but this time in Ubuntu 22.04 (the thread was about 22.10). In 22.04 clicking on the notification resulted in a successful install rather than a failure. Looks like "icon-theme-papirus" is the required missing snap theme:

```
dmn@Kayleigh:~$ snap changes
ID   Status  Spawn               Ready               Summary
10   Done    today at 10:38 MST  today at 10:39 MST  Install snap ["icon-theme-papirus"]
11   Done    today at 10:38 MST  today at 10:39 MST  Auto-refresh snaps "core22", "gnome-3-38-2004", "gnome-42-2204"

```

Haven't yet checked Ubuntu 22.10 to see if the problem persists there.

Edit: Checked 22.10 - this time, clicking on the notification sucessfully installed/updated the same packages as above. However, I log-out and back in, and the notification pops up again. This time, clicking to install still resulted in the "failed to install" message. Same thing happens after restart.

Edit 2: I spoke too soon about 20.04. After installing the aforementioned theme, and then after a new startup, the "missing theme" message is there again. And this time, choosing to install resulted in the failure to install message. So the problem has spread. It may be time to call the exterminator.

---

### Post by Dennis N on 2023-04-05
Some experimenting shows this has something to do with the icon theme selected in Tweaks. Changing the icon theme from what I was using stops the popups about missing snap themes. Why is not clearly understood.

---

### Post by steveschmechel on 2023-04-08
For me it was solved on Ubuntu Budgie 22.04 by installing the snap: gtk-theme-pocillo
Out of the box, Budgie was using Pocillo for the Widget and Icons settings as seen in Budgie Desktop Settings.
YMMV with different desktops and themes, but search "Software" or snap CLI for "gtk-theme-" and see if some of the offerings are referenced in your system and try installing ones that match.

---

