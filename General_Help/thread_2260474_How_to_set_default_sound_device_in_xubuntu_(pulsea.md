---
title: "How to set default sound device in xubuntu? (pulseaudio)"
date: 2015-01-12
forum: General Help
---

### Post by fkervin on 2015-01-12
Hi all,

It can be a dumb question, but after a time trying I don't know how to set the default audio device in xubuntu.

In pulseaudio control I can set the device I can choose for every sound card (I've one for the HDMI output and another one for spdif/analog), but I can't set the default one between those 2 groups.

In this moment the default card is the one of the second group (stereo analog now) and I want to change it to HDMI, but I don't find an option to this. The most similar I can do is, once the application opened and appearing in "playback" tab, selecting here for THIS application.

I want to set the default card for all programs, how can I do this?

Many thanks in advance

---

### Post by slickymaster on 2015-01-12
[s]Why don't you install [pavucontrol]("http://freedesktop.org/software/pulseaudio/pavucontrol/#download") which is a volume control for pulseaudio, but also allows you to choose the fallback or default.[/s]

---

### Post by pqwoerituytrueiwoq on 2015-01-12
@slickymaster pavucontrol is default in xubuntu , or is that different in 14.10 or 15.04?

@OP look to the left of my mouse in this screenshot, that is what you are looking for, if you don't see what you want go to the configuration tab
[[img]http://www.zimagez.com/miniature/screenshot-01122015-080423am.php[/img]](http://www.zimagez.com/zimage/screenshot-01122015-080423am.php)

---

### Post by fkervin on 2015-01-12
Many thanks to both!!

> **pqwoerituytrueiwoq said:**
> @slickymaster pavucontrol is default in xubuntu , or is that different in 14.10 or 15.04?

@OP look to the left of my mouse in this screenshot, that is what you are looking for, if you don't see what you want go to the configuration tab
[[IMG]http://www.zimagez.com/miniature/screenshot-01122015-080423am.php[/IMG]]("http://www.zimagez.com/zimage/screenshot-01122015-080423am.php")

pqwoerituytrueiwoq, I firstly have to admit that I've had to copy paste your nick :P

Of course I saw this option, but it's tooltip is "Poner como plan B", that in english is something like "set as secondary option", so in every moment I thought that the device I wanted to be the first shouldn't be marked in this way, hehe

Many thanks for your help and regards :)

---

### Post by slickymaster on 2015-01-12
> **pqwoerituytrueiwoq said:**
> @slickymaster pavucontrol is default in xubuntu , or is that different in 14.10 or 15.04?
<---snip--->

No, it's not different. pavucontrol is still default.

This post wasn't intended here. That's what you get when you have several tabs with multiple threads open. :oops:

---

