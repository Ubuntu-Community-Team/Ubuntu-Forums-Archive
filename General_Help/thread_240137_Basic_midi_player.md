---
title: "Basic midi player"
date: 2006-08-20
forum: General Help
---

### Post by robin_reala on 2006-08-20
This is beginning to annoy me - I'm sure there's something simple available but I've no idea how to do it.

I moved my mum over the Ubuntu a month ago and generally it's been fine. The only major problem I've got left is playing .mid files. Now in windows this is simple - WMP will just load them and play without any problem. I'm having nightmares in Ubuntu though. So far I've installed Timidity and (afaicr) modplugger, and this combination will play them (sans GUI) in Firefox. Ideally though I'd just like Rhythmbox to request the WAV stream that Timidity produces when a .mid is double-clicked on, but I've no idea how to get that working. Fwiw I tried kmid and the command-line playmidi but they both complain about a lack of /dev/sequencer - fair enough, it is missing (along with /dev/midi).

So, any ideas would be happily received. Thanks!

---

### Post by cptjaben on 2006-08-20
if i recall correctly, [EasyUbuntu]("http://easyubuntu.freecontrib.org/") lets one graphically install codecs for midi files, could be wrong though. hope this helps.

---

### Post by robin_reala on 2006-08-20
Ah, forgot to mention that I'd tried that already. It's not the synth that's the issue I think, as I can drag .mid files onto Firefox to get them to play. It's more the lack of a dedicated player that's the issue. Ideally there'd be a plugin for Rhythmbox or something...

---

### Post by viciouslime on 2006-08-20
I've just installed timidity and timidity-interfaces-extra and then set all midis to open with the command:

timidity -ig

The -ig opens it with a GTK gui.

In my opinion this is one of the last major flaws in ubuntu, it should ship with midi support preconfigured and working in such a way that all applications can handle midis.

---

### Post by robin_reala on 2006-08-20
Hey, weird. timidity -ig was producing 'PANIC' messages in the console earlier but it appears to be working now. I'll set that up for default load, thanks :)

---

### Post by viciouslime on 2006-08-20
> **robin_reala said:**
> Hey, weird. timidity -ig was producing 'PANIC' messages in the console earlier but it appears to be working now. I'll set that up for default load, thanks :)
You're welcome! :D

---

### Post by christhemonkey on 2006-08-20
If Kmid was complaining about a lack of /dev/sequencer, maybe you should load the module for it to be there?:
```
sudo modprobe snd-seq
```

And if that works fine, then add it to the end of /etc/modules:
```
gksudo gedit /etc/modules 
```
And add the line ```
snd-seq
``` to the end.

---

### Post by mssever on 2006-09-05
> **christhemonkey said:**
> If Kmid was complaining about a lack of /dev/sequencer, maybe you should load the module for it to be there?:
```
sudo modprobe snd-seq
``` 
And if that works fine, then add it to the end of /etc/modules:
```
gksudo gedit /etc/modules 
``` And add the line ```
snd-seq
``` to the end.
Anyone know how to make playmidi work? It complains about /dev/sequencer not existing. lsmod shows snd_seq to be there, but I tried modprobe on it anyway. No dice. Timidity works, but how come the playmidi .deb doesn't take care of /dev/sequencer (or depend on a package that does)?

---

### Post by Ramaddan on 2006-09-05
Hi,

Just for future reference.
This is a site with some nice How-Tos,
one of them being how to properly set up Timidity with Soundfont files:

[http://www.cs.cornell.edu/~djm/ubuntu/]("http://www.cs.cornell.edu/~djm/ubuntu/")

---

