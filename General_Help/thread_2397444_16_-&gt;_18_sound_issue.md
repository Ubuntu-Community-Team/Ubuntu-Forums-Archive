---
title: "16 -&gt; 18 sound issue"
date: 2018-07-29
forum: General Help
---

### Post by cr25602 on 2018-07-29
My issue is I have no available sound output from ubuntu. But my speaker worked on my previous Ubuntu version and in a windows partition. Also if it helps it is connecting via SPDIF (optical cable)

So I am really not sure whats going on here but here is my alsa info

[http://www.alsa-project.org/db/?f=51756a646fab29ff963715f23b09d383ca8c99d2](http://www.alsa-project.org/db/?f=51756a646fab29ff963715f23b09d383ca8c99d2)

i know that this 
!!Soundcards recognised by ALSA
!!-----------------------------



!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation C600/X79 series chipset High Definition Audio Controller (rev 06)
01:00.1 Audio device: NVIDIA Corporation GP104 High Definition Audio Controller (rev a1)


is the problem but searching for 2 or 3 hours has not yielded any fruitful solutions. Any help is appreciated.

This isnt the first time I have run into this but, usually its a relatively easy fix...maybe I am just missing something.

EDIT: [solved] alsa force-reload

---

### Post by Autodave on 2018-07-29
A little more info will be helpful.  Did you upgrade from 16.04 or did you do a clean install?  What kind of sound issues are you having?

---

### Post by cr25602 on 2018-07-29
I upgraded from 16.04 with dist-upgrade a few weeks ago I normally have no need for sound and I am just now finding it inoperable. My sound settings give me the "Dummy Output" selection.

---

