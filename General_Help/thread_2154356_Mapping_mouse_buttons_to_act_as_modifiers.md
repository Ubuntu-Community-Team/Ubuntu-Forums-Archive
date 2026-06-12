---
title: "Mapping mouse buttons to act as modifiers"
date: 2013-06-14
forum: General Help
---

### Post by stuartr on 2013-06-14
Inkscape (as an example) moves the canvas when the mouse is scrolled and zooms in and out if this is modified with the ctrl key ie ctrl + mouse scroll wheel = zoom in/out. I would like to map 2 spare buttons on my mouse to 'shift' and 'ctrl' so I could hold a modified mouse button (ctrl) and then use the scroll wheel to zoom. There are various threads which show how to map mouse buttons to one-off commands but I've had no luck with finding a mapping to a modifier.  I've used xev to find the button names and had various attempts with xbindkeys and imwheel which have come close (toggle behaviour) but I haven't reached the nirvana of button = ctrl.  Has anyone managed to do this?

Thanks

Stu
(Ubuntu 13.04)

---

### Post by carboi82 on 2013-06-14
Have you tried using the imwheel configurator from sourceforge? [http://imwheel.sourceforge.net/](http://imwheel.sourceforge.net/)

---

### Post by stuartr on 2013-06-14
I've tried imwheel (which shows that my buttons now work - one of today's success stories) but like [here]("http://ubuntuforums.org/archive/index.php/t-833835.html") the effect is like tapping the newly mapped 'ctrl' button once rather than acting like a modifier which is being held down (of course I may not understand imwheel well enough). I've also tried, amongst many other things, [this]("http://www.linuxforums.org/forum/hardware-peripherals/169773-solved-map-mouse-button-modifier-key.html") which looks more promising, but when I added my own button / modifier settings it didn't work at all (again don't assume I have any ability - I don't fully understand the syntax used here).

---

### Post by carboi82 on 2013-06-14
Assuming I understand correctly you mean that right now it has the effect of hitting ctrl, not holding ctrl (which is what you want).  The closest imwheel can come to this is simulating holding ctrl for a specified length of time in ms, using the delay before keyup event option. 

Theres also (or at least used to be) a bindbutton script that may work better for you for it to emulate the control key being held when the mouse button is held [http://ubuntuforums.org/archive/index.php/t-455656-p-5.html](http://ubuntuforums.org/archive/index.php/t-455656-p-5.html)   The commands to install and map it are about 60% down on that page, and it uses the same naming as imwheel Control_L, Shift_R, etc

---

### Post by stuartr on 2013-06-14
Thanks carboi82, potentially SOLVED (It's a bit flakey so I'm going to give it a few more days). The answer for me came a little further down the thread you highlighted (good memory!). I've used Easystroke to get the right effect - although I didn't find it very intuitive. For those following later: ubuntu 13.04, Easystroke 0.5.99.2-0ubuntu1:

1. Preferences tab: Under additional buttons; add; select radio button 'Instant Gestures', click the mouse button of choice in the grey are (so for me a 'back, thumb button' became '(Instantly) Button 8'
2. Preferences tab: Select Autostart Easystroke
3. Actions tab: Add Action, type in your own name eg 'Back button becomes ctrl', with that whole line selected/highlighted - Record Stroke, just press the button you're wanting to use again, this came up with '8 -> 8' in the Stroke column for me. Under the 'type' it'll probably have 'Command' selected, click on this and change it to 'Ignore', under details another 'Ignore' will appear, click that second ignore to make it read 'Key Combination ...', leave the mouse hovering now press Ctrl + a (or 'Shift + a' if you want the mouse button to be bound to Shft) the 'a' doesn't matter it's ignored, a 'Ctrl' will have replaced the 'Key Combination'.
4. Restart. Not sure if this is necessary but I got some odd behaviour (might have been something else I'd tried)
5. Now pressing and holding my mouse button brings up a dinky 'Ctrl' on the screen and acts like the button is being held for as long as the mouse button is.

Thanks again to carboi82 and ubuntu forums.

---

### Post by W_Z on 2014-05-10
Hello.
I just made the same using Easystroke in a different way.
My mouse has two side buttons mapped for Firefox to "open new tab in background" and "close tab":

Additional buttons:
(instant) Button 9
(instant) Button 8

Gestures are simple clicks:
gesture: 9 -> 9	type: Button	argument: Button 2
gesture: 8 -> 8	type: Key	argument: Ctrl+W


I have added button 9 + mouse scroll clicks gestures:
gesture: 9 -> 4	type: Key	argument: Ctrl++
gesture: 9 -> 5	type: Key	argument: Ctrl+-

---

