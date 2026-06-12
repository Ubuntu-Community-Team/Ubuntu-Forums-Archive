---
title: "Sound issues"
date: 2008-05-09
forum: General Help
---

### Post by smkoberg on 2008-05-09
Hey everyone, not sure if this is the best place for this question, but here it goes:

Whenever I'm on my laptop (Dell Inspiron 1501 running 8.04) I usually have music playing through my headphones. Last night at some point the right audio channel stopped working. 

I didn't think much of it as my headphones are a few years old and starting to kick the bucket, but today I tried listening to music on my Windows box through the headphones, and didn't have a problem. Then I tried listening to music/video's through the built in speakers on the laptop, and I'm having the same problem. Nothing coming from the right channel.

Now I don't know what could have caused this problem. It seems to have just happened out of the blue.

Anyone know of a way I can check to see whats going on/fix the problem?

Thanks a bunch

Seth

---

### Post by macaholic on 2008-05-09
Do you have pulse audio installed? I know that it has the ability to mute only one channel, not sure how it would ahve happened by accident though. You can check by running "pulseaudio", clicking on its gnome icon, amp cord, and selecting volume control.

---

### Post by smkoberg on 2008-05-09
I checked Synaptic to see if pulse audio was installed and it tells me that it is. But I'm having trouble finding it on my system. (I've got lots to learn)

---

### Post by fearpi on 2008-05-10
Go to the terminal and run alsamixer.

Then, with the arrow keys, go over to whichever device (probably Master or PCM) has one channel muted. You can tell because at the bottom of the volume bar will be "00", "0M", "M0", or "MM". M signifies muted, 0 signifies unmuted.

The period (.) key will toggle mute for right channel on that device; the comma (,) key will toggle mute for left channel on that device.

I have this issue all the time as well. Usually occurs when I'm changing the volume. This is a ridiculous bug that I'd wish they would fix.

---

### Post by smkoberg on 2008-05-10
Awesome, worked like a charm.
Thank you so much!!

Seth

---

