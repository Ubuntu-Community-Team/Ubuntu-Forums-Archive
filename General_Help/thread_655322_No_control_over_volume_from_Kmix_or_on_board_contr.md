---
title: "No control over volume from Kmix or on board controls"
date: 2008-01-01
forum: General Help
---

### Post by nirpius on 2008-01-01
I've just loaded Kubuntu Gutsy onto a new laptop and I can't stop the volume being at full. If I'm playing something in Amarok or Kaffeine I can use the volume contorl in that program to change the volum of that item but nothing else works.

I can press function and f3 and I get a thing pop up on the screen saying mute on or mute off but it doesn't actually d anything. I can press function and f5 for increase and f6 for decrease but it only goes between 0% and 11% in one jump (no scaling) and this doens't actually affect output either. I fI use Kmix, no matter which of the volumes (input or output) I set to whatever level, nothing changes in the actual output.

Oh, and another thing, I imstalled audacity nad it won't recognise anything being said when I record so I don't think my on board mic is working either.

Does anyone know any noob friendly guides that should be able to help me or does anyone have experience with a similar problem?

Many thanks

---

### Post by nirpius on 2008-01-01
I don't mean to bump but please if anyone has any ideas what to do...

---

### Post by disturbedite on 2008-01-01
some apps (i.e. audacious) have options to "Use Software Volume Control" which means you can adjust the volume in the program separate from the system volume.

try deselecting/turning that off.

---

### Post by nirpius on 2008-01-01
I don't have audacious on here. What is that?

---

### Post by nirpius on 2008-01-01
I input this into a terminal:

```

aplay -l
```

And got

```

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC861 Analog [ALC861 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC861 Digital [ALC861 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I don't know if this will help but I thought ti might give someone some leads.

---

### Post by lord aragorn on 2008-01-02
> **nirpius said:**
> I can press function and f5 for increase and f6 for decrease but it only goes between 0% and 11% in one jump (no scaling) and this doens't actually affect output either. s

I have the exact same issue with SB450 HDA Audio (rev 01) card, any ideas how to fix it?

---

### Post by nirpius on 2008-01-02
No ideas how yet. I googled it and it seems that hundreds of people have had this same issue in Gutsy and there is a bug report filed but in the current Hardy developement release this isn't fixed yet :(

---

### Post by disturbedite on 2008-01-05
> **nirpius said:**
> I don't have audacious on here. What is that?
audacious is an audio player.  (a dang good one if i can get in a cheap plug here ;)).  i was simply using audacious as an example of a program with that type of option.

---

