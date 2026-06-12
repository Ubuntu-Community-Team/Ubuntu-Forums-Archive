---
title: "random pasting"
date: 2008-06-15
forum: General Help
---

### Post by dracule on 2008-06-15
This is starting to get annoying and get in the way of coding. 

Sometimes i am just typing away and all of the sudden it pastes something i copied earlier. My fingers are no where near my ctrl button, and i would have defiantly noticed if i accidentally right clicked and somehow magically hit the paste command. 

When i write emails, it randomly pastes.


when i am coding it randomly pastes (this is a BIG pain in the *** since i have to find where my cursor was when it decided to do it)

or when i am on forums, or IRC, it will paste without me doing anything.

I am getting mad..

---

### Post by Joeb454 on 2008-06-15
It's probably something to do with the Middle Click button on your mouse. I believe you can change it, though I can't remember where :( I'll have a look around, but I'm almost certain thats what's causing it :)

---

### Post by dracule on 2008-06-15
o dang! you are right! 

i am using a laptop, so sometimes it clicks the left and right and that simulates the middle click.

so... now i just need to find out how to fix it..

---

### Post by Joeb454 on 2008-06-15
This is why whenever possible I use an actual desktop mouse whenever possible ;)

It happens less that way. Though I'm not 100% sure how you can fix this, I'd be interested to know myself, as I've just put up with it so far :p

---

### Post by kevmitch on 2008-06-15
I believe that you want to add the line

[CODE]
        Option          "Emulate3Buttons"       "false"
[\CODE]

to any "InputDevice" of your /etc/X11/xorg.conf file.

---

