---
title: "Computer suspends when rhythmbox is playing"
date: 2014-06-12
forum: General Help
---

### Post by Qd64erK on 2014-06-12
Hi

First, I'm using Xubuntu Trusty :). I have configured power management to suspend my computer after 15 minutes if inactive, but it also suspends if rhythmbox is playing. So if I'm listening to music but away from my computer, it will stop playing and suspend after 15 minutes.

 I think that Xubuntu shouldn't "be" inactive when pulseaudio or a media player is running. It should only be inactive after the playlist is over and nothing else happens.

How can I prevent this from happening? Is there something wrong with my pulseaudio/rhythmbox install or config?

Thank you for your help,
Cheers
**ASENSIO**

---

### Post by tgalati4 on 2014-06-13
Inactive is generally defined as no user input (keyboard or mouse).  So change your system not to suspend.

You would have to write a script to specifically prevent suspend under certain conditions as in this thread:  [http://ubuntuforums.org/showthread.php?t=1423030&highlight=awake+playing+video](http://ubuntuforums.org/showthread.php?t=1423030&highlight=awake+playing+video)

---

### Post by bug67 on 2014-06-13
An app called [Caffeine]("https://launchpad.net/caffeine") used to, ahem, suspend suspend (Thanks!  I'll be here all day! :lolflag: ) but, the developer has butchered the app to the point of being beyond useless.  I'm looking into alternatives, like tgalati4 mentioned, such as scripting myself.

---

### Post by tgalati4 on 2014-06-13
I did not mention *caffeine* because it seems to cause more issues than it solves, but if it works for you then great.  Otherwise, you will need to spend some time scripting to get your computer to do what you want.

If you just want the screen to turn off, then check the monitor's settings or your computer's BIOS and check the DPMS settings.

---

### Post by Qd64erK on 2014-06-13
thanks for your replies, 
Ok, there's nothing wrong with my xubuntu, good. So caffeine is useless and I can't code... :(

Well, I thought something like this: monitor rhythmbox, if it's running then I need a keystroke to keep my computer active. Did some searching and found this:
[How to continuously monitor rhythmbox for track change using bash]("http://unix.stackexchange.com/questions/46301/a-list-of-available-dbus-services")
[How to inject keystrokes via a shell script?]("http://unix.stackexchange.com/questions/14879/how-to-inject-keystrokes-via-a-shell-script")

I think I'm way over my head here, but... is this usable? (remember I can't code :))
```
#!/bin/bash

interface=org.gnome.Rhythmbox.Player
member=playingUriChanged
dbus-monitor --profile "interface='$interface',member='$member'" |
while read -r line; do
xdotool key space
done
```

Again, thank you for your help
Cheers
**ASENSIO**

P.S. - "suspend suspend" ahahahah

---

### Post by tgalati4 on 2014-06-14
Yes, that's one way to do it.  Let us know if it works.  The script looks OK and *xdotool* seems to be installed on my 12.10 system as part of the base system.

Some players (not rhythmbox) allow a preplay script to run before a track is played.  That allows you to use *xdotool* or some other script to keep awake during playback.

There are some dbus plug-ins for rhythmbox and perhaps you can use a direct dbus command to keep the system awake.

---

### Post by Qd64erK on 2014-06-15
it didn't work. i tried it with the <super> key that opens my wisker menu and, even if rhythmox is off, the script opened de menu. so I think that the "monitor dbus" part has something wrong. I tried it with rhythmbox on and my computer suspended after 15 minutes.
there should be a RB plugin to do this :(

---

