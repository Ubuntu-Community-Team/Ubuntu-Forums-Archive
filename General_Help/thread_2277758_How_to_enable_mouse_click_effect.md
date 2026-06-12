---
title: "How to enable mouse click effect"
date: 2015-05-11
forum: General Help
---

### Post by danbuz on 2015-05-11
Hi guys,

I'm about to do a make a presentation in the university with projector, and I would like to achieve an effect like this watch?v=K0ytU668vzg.

Tried KeyMon, but it is not even close.. Searched about an hour over the net and compiz seems to be the only option but again not like this..

Any idea?

Thanks in advance!

---

### Post by dino99 on 2015-05-11
you can change the mouse settings via dconf (dconf-editor needs to be installed): click on its menu to search 'mouse', then click 'next to get the next occurence, till you find the right setting entry

---

### Post by danbuz on 2015-05-11
> **dino99 said:**
> you can change the mouse settings via dconf (dconf-editor needs to be installed): click on its menu to search 'mouse', then click 'next to get the next occurence, till you find the right setting entry

Thank you for the reply.  I'm not a technical guy. Although I managed to install dconf-editor I can't find how to achieve such effect. 
Any further help will be much appreciated since there is nothing on internet ..

Thanks

---

### Post by danbuz on 2015-05-13
Anyone please?

I believe it will be helpful for a lot other guys?

---

### Post by coffeecat on 2015-05-13
Was that meant to be a link to a video or image in your first post? If it was, you've left out most of the URL. So that others can help you by being able to see the effect you are seeking, you might want to re-post the link.

---

### Post by danbuz on 2015-05-13
> **coffeecat said:**
> Was that meant to be a link to a video or image in your first post? If it was, you've left out most of the URL. So that others can help you by being able to see the effect you are seeking, you might want to re-post the link.


Sorry I do not post direct links by default :)
[https://www.youtube.com/watch?v=K0ytU668vzg](https://www.youtube.com/watch?v=K0ytU668vzg) watch after 2 minute of the video..

---

### Post by dragonfly41 on 2015-05-13
Explain the "mouse click effect" in one sentence.

---

### Post by Holger_Gehrke on 2015-05-13
I think danbuz is talking about the visual cue around the mouse pointer in the video every time the mouse is clicked (a blue circle spreading around the pointer and then vanishing again).

 Something like that can actually be achieved using key-mon by going into it's settings (ctrl-s), switching of all the indicators it shows in it's window except for "highly visibly mouse-click", leaving key-mon settings and then key-mon (ctrl-q) and starting it from the shell with a scaling option to make the window into a single pixel ('key-mon --visible_click --scale=0.05', might need to play with the scaling factor; too large and the windows stays visible as a small square, to small and key-mon won't run). This will give you a red circle around the pointer on mouse click which - provided you have a compositor running - should then fade out quickly (without a compositor it won't fade out; it will stay visible a moment longer and then just vanish). If you want a different colour or shape, you can just replace or edit the svg file '/usr/share/pyshared/keymon/themes/classic/mouse-indicator.svg' (put the name of whichever theme you're using instead of 'classic') using inkscape. If you absolutely, positively need (or want) an animation effect, feel free to change '/usr/shared/pyshared/keymon/shaped_window.py'. You'd need to load the phases of the animation in __init__ and change fade_away to show the various phases instead of just setting a timer for the fade out.

I think the video was recorded using a virtual machine since the recording continues through a reboot, probably on a windows host using a screen-recorder that added the effect (camtasia can do things like that, I believe ...)

---

### Post by danbuz on 2015-05-13
> **Holger_Gehrke said:**
> I think danbuz is talking about the visual cue around the mouse pointer in the video every time the mouse is clicked (a blue circle spreading around the pointer and then vanishing again).

 Something like that can actually be achieved using key-mon by going into it's settings (ctrl-s), switching of all the indicators it shows in it's window except for "highly visibly mouse-click", leaving key-mon settings and then key-mon (ctrl-q) and starting it from the shell with a scaling option to make the window into a single pixel ('key-mon --visible_click --scale=0.05', might need to play with the scaling factor; too large and the windows stays visible as a small square, to small and key-mon won't run). This will give you a red circle around the pointer on mouse click which - provided you have a compositor running - should then fade out quickly (without a compositor it won't fade out; it will stay visible a moment longer and then just vanish). If you want a different colour or shape, you can just replace or edit the svg file '/usr/share/pyshared/keymon/themes/classic/mouse-indicator.svg' (put the name of whichever theme you're using instead of 'classic') using inkscape. If you absolutely, positively need (or want) an animation effect, feel free to change '/usr/shared/pyshared/keymon/shaped_window.py'. You'd need to load the phases of the animation in __init__ and change fade_away to show the various phases instead of just setting a timer for the fade out.

I think the video was recorded using a virtual machine since the recording continues through a reboot, probably on a windows host using a screen-recorder that added the effect (camtasia can do things like that, I believe ...)


That's what I was talking about.. Thanks for the reply but it's to complicated for me I'm not able to do it myself. May be I will try all this when I have the time for the future. I hoped it is stand alone app with ready settings. 

Thanks!!

---

### Post by dragonfly41 on 2015-05-13
Like here ... [http://askubuntu.com/questions/169426/how-to-get-cursor-click-effect](http://askubuntu.com/questions/169426/how-to-get-cursor-click-effect) ... ?

---

