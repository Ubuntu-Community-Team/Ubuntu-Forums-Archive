---
title: "Atlantis issues since upgrade? Plus other questions."
date: 2008-06-04
forum: General Help
---

### Post by vapotrini on 2008-06-04
Have a few questions that hopefully someone can help me with... Firstly, since I did a update of Linux today (auto updater) whenever I have Atlantis enabled my cube colors distort. It's like one side changes to a dark blue, then when that side reaches to the front while rotating it returns to normal, and the next window in line of the cube will change to the blue. And so and so on. I'm guessing it's the update that did this. Anyone else having this problem?

The next thing I'd like to find is, my grub now has 3 versions of Linux to choose from. I'd like it so that it only displays 2. How can I edit grub to display only 2? And how do I go about removing the older kernels? I tried synaptic>status>installed local or obsolete but all I see there is kiba bar and awn. Nothing else? :confused:

Lastly, I have quite a few things loading up on my computer at start up. A lot of Screenlets, AWN and Kiba-dock. When Ubuntu is loading up, they ALL distort and it stays that way for about 30-40 seconds. Now I know I have a lot loading up so I don't mind the time, however is there a way I can have Ubuntu load up. Then once it's FULLY loaded, have the screenlets load, then awn, then kiba? I tried going into sessions and changing the order but no joy, they all seem to load at the same time.

Any help to any of my questions would be greatly appreciated.

---

### Post by Forlong on 2008-06-05
> **vapotrini said:**
> Have a few questions that hopefully someone can help me with... Firstly, since I did a update of Linux today (auto updater) whenever I have Atlantis enabled my cube colors distort. It's like one side changes to a dark blue, then when that side reaches to the front while rotating it returns to normal, and the next window in line of the cube will change to the blue. And so and so on. I'm guessing it's the update that did this. Anyone else having this problem?
It seems like Atlantis has been pulled from Ubuntu's packages.
> **vapotrini said:**
> The next thing I'd like to find is, my grub now has 3 versions of Linux to choose from. I'd like it so that it only displays 2. How can I edit grub to display only 2? And how do I go about removing the older kernels? I tried synaptic>status>installed local or obsolete but all I see there is kiba bar and awn. Nothing else? :confused:
In Synaptic, search for **linux** and the last number of the kernel you want to remove -- but only by Name -- e.g. **linux 16**
Then remove all the packages you find. It will update GRUB automatically then.
> **vapotrini said:**
> Lastly, I have quite a few things loading up on my computer at start up. A lot of Screenlets, AWN and Kiba-dock. When Ubuntu is loading up, they ALL distort and it stays that way for about 30-40 seconds. Now I know I have a lot loading up so I don't mind the time, however is there a way I can have Ubuntu load up. Then once it's FULLY loaded, have the screenlets load, then awn, then kiba? I tried going into sessions and changing the order but no joy, they all seem to load at the same time.
You have to write a small script for that.
Open a terminal and type
```
gedit $HOME/start-screenlets-awn-kiba
```
and paste this in there:
```
#!/bin/bash

sleep 20
screenlets &
avant-window-navigator &
kiba-dock &
```
Save an close gedit.

Then you have to make it executable:
```
chown +x $HOME/start-screenlets-awn-kiba
```

Finally, go to *System &#8594; Preferences &#8594; Sessions &#8594; Startup Programs* and add **start-screenlets-awn-kiba** (it's a file in your home directory).


P.S. please use separate threads for unrelated topics next time.

---

### Post by vapotrini on 2008-06-05
Thank you VERY much Forlong! And fantastic setup guide by the way, really good work.

---

