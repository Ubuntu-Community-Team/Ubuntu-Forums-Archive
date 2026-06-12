---
title: "Was tricked into upgrading kernel: Lost sound"
date: 2007-10-07
forum: General Help
---

### Post by farmfield on 2007-10-07
*So when I activated nvidia-glx-new it installed the new kernel as a dependency -and nvidia-glw-new won't start anyway so I'm on the "Nv" driver now -Grrrrrrrrrr!!! But I got another post about that...*

But I also lost sound... Just got an "x" by the speakersymbol and Gutsy say's I got no sound installed... I have an onboard card which worked flawlessly with 7.04 and in Gutsy until now...

Anyone?

---

### Post by DagMan on 2007-10-07
Can you unmute it if you double click it or slide the volume meter up?
If you type alsamixer at a terminal, is there anything there that looks muted that should not be, m toggles mute  and up and down arrows for volume leverl, esc to quit.  In alsamixer sometimes if something that is enabled that conflicts or isn't there it can actually screw sound up so disable what you know you don't need for now.  
First, I forgot, if you right click on the volume mixer applet in gnome, try out to see if alsa is there or if something else works and set it to something like PCM or whatever... make sure it isn't on mic though I don't know if that makes a differance.
Finally, there's settings in preferances->sound

---

### Post by farmfield on 2007-10-07
Clicking on it gets me;

```
The volume control did not find any elements and/or devices to control.
This means either that you don't have the right GStreamer plugins installed, or
that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker
icon on the panel and selecting "Remove From Panel" from the menu.
```

And Alamixer in terminal says:


```
alsamixer: function snd_ctl_open failed for default: No such device.
```

---

### Post by mpgarate on 2007-10-07
i had a problem like this, and the only thing I could do was choose he generic kernel from the grub menu. since then, I have gotten automatic upgrades for the kernel, and generic is default again (at the top of the list)

heres my thread about my similar problemo

[http://ubuntuforums.org/showthread.php?t=559922](http://ubuntuforums.org/showthread.php?t=559922)

---

