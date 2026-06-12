---
title: "Touch events do not work in Chromium on Ubuntu 14.04"
date: 2014-04-27
forum: General Help
---

### Post by lesilvestre on 2014-04-27
I've just upgraded to Ubuntu 14.04 on my Thinkpad X201T, which has a touch screen. I noticed that the touch screen behavior has changed. Now the system treats touches and mouse clicks differently, which sounds like a good idea at first.

The difference is most noticeable in Chromium. Now we can drag the page with one finger, which is great. This looks more like Safari on the iOS or Chrome on Android. However, there is a major flaw in the implementation: touching the page does not generate touch events.

In practice, this means that any modern HTML application made with HTML5 and javascript will not work with the touchscreen. If anyone has any clue how to fix this, please let me know. I'm a bit surprised because I thought Canonical was making this one of its priorities.

I would be willing to go back to the previous behavior where the touch screen worked just like another mouse. It is not optimal but at least the web apps work.

I like playing a scrabble-like game on the touchscreen with my wife. I wrote this game myself ( [http://math.uchicago.edu/~luis/words/](http://math.uchicago.edu/~luis/words/) ). I used standard HTML5 & javascript. It works on the iPad, iPhone, Android, and probably Windows (although I haven't tried), but not on Ubuntu 14.04. Luckily I have another Thinkpad with a touch screen which will not get updated until this is fixed.

---

### Post by lesilvestre on 2014-05-02
I think the problem may be related to this bug

[https://code.google.com/p/chromium/issues/detail?id=133735#c3](https://code.google.com/p/chromium/issues/detail?id=133735#c3)

From what they say, Chrome/Chromium will not support touch for as long as it uses GTK. I have no idea what is the stage of the transition of Chromium to Aura.

---

### Post by lesilvestre on 2014-05-02
I found a very easy fix. Touch events work if we start chromium with the command line

chromium-browser --touch-events=enabled

I have no idea why touch events are not enabled by default.

---

