---
title: "strange sound after headphones are unplugged in suspension"
date: 2018-01-03
forum: General Help
---

### Post by Ivo_Degn on 2018-01-03
Hey all,
I've been having this issue for a while and found my work-around, but I'd like to fix this once and for all. Maybe someone here can help me.
I use a Chromebook 2 with Xubuntu (GalliumOS).

Whenever I put the computer into suspension with headphones plugged in and then unplug the headphones **before** I wake up the computer again, the sound is either off or sounds like an alien talking, until I either play around with Pulseaudio or plug the headphones back in and out.
I imagine that Pulseaudio somehow doesn't realize that the headphones were unplugged while in suspension, so is there a way I can make it confirm every time after suspension or so?

Would appreciate any lead.

---

### Post by DuckHook on 2018-01-03
Are you trying to run a script whenever resuming from suspend? If so, then this strategy might help: [https://blog.christophersmart.com/2016/05/11/running-scripts-before-and-after-suspend-with-systemd/](https://blog.christophersmart.com/2016/05/11/running-scripts-before-and-after-suspend-with-systemd/)
Also this: [https://ubuntuforums.org/showthread.php?t=2344257&p=13605747#post13605747](https://ubuntuforums.org/showthread.php?t=2344257&p=13605747#post13605747)
And this: [https://mariogalan.com/en/content/execute-script-after-suspend-ubuntu-1604](https://mariogalan.com/en/content/execute-script-after-suspend-ubuntu-1604) …which explains the "post" option.

However, because you do not describe your workaround, I have no idea what the contents of said script might be. If your workaround involves resetting pulse audio, then a very simple script might do it.

---

### Post by Ivo_Degn on 2018-01-05
Thanks for the suggestions. Running a post-script should do the trick. My workaround is more manual, plugging the headphones back in and out.
So the trick would be to add an executable script in  /usr/lib/systemd/system-sleep/ with a post-script?
Regarding the code, would this work? (novice)

> [COLOR=#666666][FONT=monospace]*#!/bin/sh*[/FONT][/COLOR]

[COLOR=#666666][FONT=monospace]*# restart pulseaudio*[/FONT][/COLOR]

[COLOR=#000000][FONT=monospace]**case**[/FONT][/COLOR][FONT=monospace] [/FONT][COLOR=#FF0000][FONT=monospace]"$1"[/FONT][/COLOR][FONT=monospace] [/FONT][COLOR=#000000][FONT=monospace]**in**[/FONT][/COLOR]
[FONT=monospace]        post[/FONT][COLOR=#7A0874][FONT=monospace]**)**[/FONT][/COLOR]
[FONT=monospace]          [/FONT][COLOR=#000000][FONT=monospace]**/**[/FONT][/COLOR][FONT=monospace]usr[/FONT][COLOR=#000000][FONT=monospace]**/**[/FONT][/COLOR][FONT=monospace]sbin[/FONT][COLOR=#000000][FONT=monospace]**/**[/FONT][/COLOR][FONT=monospace]service [/FONT][COLOR=#000000][FONT=&quot]pulseaudio -k && [/FONT][/COLOR][COLOR=#000000][FONT=&quot]pulseaudio -v[/FONT][/COLOR][FONT=monospace] [/FONT][COLOR=#000000][FONT=&quot]
[/FONT][/COLOR][FONT=monospace]                [/FONT][COLOR=#000000][FONT=monospace]**;;**[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]**esac**[/FONT][/COLOR]

---

### Post by DuckHook on 2018-01-08
Sorry for the delayed response. For some strange reason, I didn't get a notice of your reply. :confused:

Since my last post, I've done some experimenting and discovered the following: Pulseaudio is a user service and not a system service. Therefore, if it is killed and restarted with systemd, it will be running as a system service under root. This is awkward and inadvisable for security reasons, if nothing else. A better solution is to create a shortcut key to a simple user script. By invoking the user script, you cycle a kill and restart of pulseaudio.

[list=1]
[*]Create a directory under /home/<your-username>/ called /home/<your-username>/.bin as a container for your own scripts:```
mkdir -P -m 755 ~/.bin
```
[*]Check to make sure that ~/.profile contains the following:```
# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/.bin" ] ; then
    PATH="$HOME/.bin:$PATH"
fi
```
[*]Create a file in this directory called pulse-reset.sh:```
nano ~/.bin/pulse-reset.sh
```
[*]Type something like the following:```
#!/bin/bash
# Kill and restart pulseaudio
pulseaudio -k
sleep 5
pulseaudio

```
[*]Make the script executable:```
chmod -c 775 ~/.bin/pulse-reset.sh
```
[*]Create a keyboard shortcut for this script.
If using Ubuntu Artful: [https://help.ubuntu.com/stable/ubuntu-help/keyboard-shortcuts-set.html](https://help.ubuntu.com/stable/ubuntu-help/keyboard-shortcuts-set.html)
If using Ubuntu Xenial: [https://help.ubuntu.com/lts/ubuntu-help/keyboard-shortcuts-set.html](https://help.ubuntu.com/lts/ubuntu-help/keyboard-shortcuts-set.html)
You will have to experiment with different key combos to avoid those already in use.
[/list]
It bears noting that the best solution is to remember to unplug your headphones before you suspend. Consider: when suspending, you are asking your system to take a complete snapshot of its system state before going into deep sleep. When you disconnect your headphones while suspended, this is like sawing off an appendage while it is frozen in its state of deep sleep. Asking it to elegantly recover from such a brutal assault is a big ask. It's no wonder it complains with wonky sounds.

---

