---
title: "Disabling joystick button events"
date: 2008-02-15
forum: General Help
---

### Post by Prefader on 2008-02-15
I've got a Saitek X-52 Joystick/Throttle that I bought to use with Vendetta Online - for the most part, it works very nicely.  There are a few hang-ups:  1)I can't seem to figure out how to set up deadzones on the stick and throttle, and 2) the mode switch on the stick registers as a button press, and one of them is always pressed.  I'm most concerned with #2.  (BTW, this is in Kubuntu Gutsy).

The problem rears it's head whenever I try to set up my button mappings in Vendetta - whenever I double click on an action to map a button to it, it gets assigned to whichever "mode" button is currently selected, and so I have to set up my button configs manually in a text editor - very annoying if I want to make a quick change to something.

So, what I'd like to do is tell the entire system to just flat out throw away any events from the joystick for buttons 23, 24, and 25 - these mode buttons aren't supported by anything in linux that I know of, anyway.  Is there a way to do this?

---

### Post by Prefader on 2008-02-18
Bump -

Manually editing the config file isn't working for me . . . either there is something wrong with the way VO is mapping buttons (some buttons don't appear to have the same mapping as what I see in kcontrol - JOYBUTTON0 in VO is Button 1 in kcontrol, stuff like that.  The -1 offset doesn't work for all of the buttons, though - and without disabling the always-on buttons, I can't figure out what buttons VO thinks I'm pressing), or it just doesn't like the controller.

Any ideas?

---

### Post by Prefader on 2008-02-19
OK, manually editing the config is working - I had overlooked an extra section in the config file.  I had originally tried copying my config from a windows install, which didn't work for me.  Turns out that the reason was, windows called the joystick "Saitek X52 Flight Control System" and kubuntu called it "Saitek Saitek X52 Flight Control System".  I also noticed that the game client won't allow me to leave the configs for buttons 1, 2, or 3 empty.  So, although I haven't figured out how to block the button presses from the mode switch, I have a working config for the game.

Hope this can help someone else!

---

