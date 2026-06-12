---
title: "absolute beginnner, webcam"
date: 2007-02-24
forum: General Help
---

### Post by nonewmsgs on 2007-02-24
im sorry but i wasnt quite certain as to the correct forum to place this, so i chose general help.  it seemed a very appropriate place being general help and this being a general question.

now i have been using ubuntu for 8 days, and i LOVE it.  i never want to go back to windows.  i have not yet recieved the couple books on ubuntu i bought on amazon, but im starting to get a real feel for it (thanks to all those wonderfully patient people in absolute beginner's), but now im uncertain as to where i should post my dumb questions.  perhaps the questions arent dumb, but the background is, for example:

well my webcam (magicvision usb sightcam) was sort of working woth ubuntu.  camorma webcam viewer would let me see but i always looked a blue, which would be fine and dandy but im more of a pale white person.  the colors and hue arent actually adjusting it.  yache shows it as a few red bars and blank for the webcam viewer.

so i downloaded bunches of stuff.  anything related to webcams especially drivers.  im not even sure what i did download but i know i got some universe and multiverse stuff, but nothing seemed to really help.  (in fact for a brief period of time i just got an error everytime i tried to access it, but im not sure what caused/ended that).

so i have the following questions:
what do i have to do to stop being so blue?
what do i have to do to have my cam viewable in gyache
should i start threads in absolute beginners or should i use the more typical forums for my questions?

---

### Post by cronholio on 2007-02-25
That webcam doesn't seem very common. Can you tell us the output of "lsusb"?

---

### Post by nonewmsgs on 2007-02-25
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 002: ID 0af9:0011 Hama, Inc. Micro Innovations IC50C WebCam
Bus 005 Device 003: ID 124b:4d01 Nyko (Honey Bee) Airflo EX Joystick
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

---

### Post by cronholio on 2007-02-25
[See here.]("http://mxhaard.free.fr/spca5xx.html") This is the driver used by Ubuntu for your webcam and it says on the list your camera is supported but the quality is bad. This is probably due to the problem you described. The only way to get decent image quality is buying one of the cameras on the list with better support.

---

### Post by nonewmsgs on 2007-02-25
thank you very much for the help and the link.  i do have penguinitis and micro$ofthate so im willing to put a few bucks towards linux.  i have already replaced my videocard from ati to nvidia so now i can spend a couple bucks on ebay and get a webcam that can show me off and then i wont be so blue.

(webcam problem solved, tv tunercard, and pcmcia wireless card to go)

---

### Post by theJagger on 2007-02-27
I just installed camorama from the universe repository.

it has color correction available as an effect.
so I right clicked in the box that says "effects" and clicked "add" "color correction"

Does that work for you?

---

