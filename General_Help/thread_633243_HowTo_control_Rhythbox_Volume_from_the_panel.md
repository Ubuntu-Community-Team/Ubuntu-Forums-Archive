---
title: "HowTo control Rhythbox Volume from the panel"
date: 2007-12-06
forum: General Help
---

### Post by banewman on 2007-12-06
There are many gdesklets for Rhythmbox but unfortunately they aren't working.
So I searched around and come up with this as a solution to let me do stuff and not have to maximize Rhythmbox to turn the volume down or up.
It involves a couple of bash scripts and panel shortcuts.
Save the following code as -  VolUp.sh   -or whatever you want to call it but it must end in .sh

The VolUp.sh

```
#!/bin/sh
echo $(dbus-send --dest=org.gnome.Rhythmbox /org/gnome/Rhythmbox/Player \
org.gnome.Rhythmbox.Player.setVolumeRelative double:0.1)
```

Open a text editor from the application-accessories menu then copy and paste. Then click "file" from the top menu then "save as" -name it -  VolUp.sh - save in your /home/you folder.
Close the file then open your /home/you folder and right click the VolUp.sh file and select properties. Click the "execute" checkbox then close.
Right click the panel where you want the app to be and select "custom application launcher"
Call it "up" or whatever and then select browse to go to the file in your /home/you directory and click the VolUp.sh file and select open.
Click "no icon and browse for a suitable icon.
It is - of course - the same process for VolDown.sh except the names are different.

The VolDown.sh

```
#!/bin/sh
echo $(dbus-send --dest=org.gnome.Rhythmbox /org/gnome/Rhythmbox/Player \
org.gnome.Rhythmbox.Player.setVolumeRelative double:-0.1)
```

I found it useful and hope others do to. :)

---

### Post by rsambuca on 2007-12-06
This is interesting, but what is wrong with the regular volume control icon on the top panel.  You don't even have to click anything, just hover your mouse cursor over top of the icon and turn your mouse scrollwheel.

---

### Post by banewman on 2007-12-06
I have music playing while doing other stuff and found it easier to click on the panel instead of maximizing Rhythmbox then changing the volume then minimizing it again.
Also have shortcuts so I can go to the next or previous songs etc. :)

---

### Post by rsambuca on 2007-12-06
You don't need to open Rhythmbox to do what I was talking about.  Don't you have a volume control knob on your top panel?  It is a default to have one with the Gnome desktop.

---

### Post by banewman on 2007-12-06
Rhythmbox has it's own volume control seperate to alsa.
Yes if you turn alsa right down Rhythmbox will go quiet but change the volume of Rhythmbox while alsa is showing and you'll see the difference. :)
Alsa only sets the max volume.

---

### Post by rsambuca on 2007-12-06
Here is a screenshot of my top right panel.  The volume control is circled in red.

---

### Post by banewman on 2007-12-06
See Above. :)

---

### Post by rsambuca on 2007-12-06
> **banewman said:**
> Rhythmbox has it's own volume control seperate to alsa.
Yes if you turn alsa right down Rhythmbox will go quiet but change the volume of Rhythmbox while alsa is showing and you'll see the difference. :)
Alsa only sets the max volume.

Can you elaborate here?  I am not sure I understand.  On my system, if I use the main volume control while Rhythmbox is playing, I can turn the volume up or down or to whatever level I desire.  Can you not do this?

---

### Post by banewman on 2007-12-06
Of course I can but doing that also changes the volume for system sounds etc.
My post was about only changing the volume of Rhythmbox. :)

---

### Post by rsambuca on 2007-12-06
Ah, gotcha now.

---

### Post by banewman on 2007-12-06
Glad to clear it up for you. :)
As someone that plays music while working on the comp I am so glad I went to the trouble of making this work. Saves several clicks :)

---

### Post by rsambuca on 2007-12-06
No offense, but I think I will stick with the main volume knob.  That way, I don't even need *any* mouse clicks!

---

### Post by banewman on 2007-12-06
Do you have Rhythmbox maximized on a workspace all the time? Then the mouse wheel is the best for you and I wish you luck and good cheer. :)

---

### Post by rsambuca on 2007-12-06
I usually leave it minimized.  I too have it running virtually all day.

---

### Post by banewman on 2007-12-06
I guess you don't get too many interruptions or have songs that you like to hear played louder then? :)

---

### Post by rsambuca on 2007-12-06
I think our systems must not be set up the same.  Even when I have Rhythmbox minimized and playing, I can still use the mouse scrollwheel to change the volume without maximizing Rhythmbox.

I have the PCM set to full blast, but have the main volume control set to the "Front speakers".  This way I can go anywhere from muted up to full blast using the scrollwheel.

---

### Post by banewman on 2007-12-06
Maybe our systems aren't the same.
Are you sure turning the volume down on Rhythmbox doesn't turn the volume down everywhere else?
Unless your working on the gtk action for Rhythmbox's volume any sound controls will be global - or there is dbus...:)

---

### Post by rsambuca on 2007-12-06
Yes, I globally change the volume!

---

### Post by banewman on 2007-12-06
I'm glad you've got your system working for you how you like it.
That's the essence of linux isn't it?
My first post ended with I hope someone can use these scripts too and your not someone that can but I've appreciated our comments. :)

---

### Post by rsambuca on 2007-12-06
Sorry.  Didn't mean to annoy you.

---

### Post by banewman on 2007-12-06
No offence taken at all.
Your exclamation point at the end of your last comment suggested a reconciliatory comment in return.
When I posted this howto I had no idea if anyone else had found themselves in a position where it could be useful.
Your comments - being the only ones - cleared that up and I thank you for your efforts there.
Best of luck and good cheers to you and yours. :)

---

