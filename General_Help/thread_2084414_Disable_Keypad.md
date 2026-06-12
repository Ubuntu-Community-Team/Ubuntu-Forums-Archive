---
title: "Disable Keypad"
date: 2012-11-15
forum: General Help
---

### Post by borgward on 2012-11-15
How do I disable the keypad?

Ubuntu 10.04. Dell Inspiron 1520.

I did:

System -> Preferences -> Keyboard -> Mouse Keys -> Unchecked "Pointer can be controlled using the Keypad"

Keypad still functions.

I decided to use wireless mouse, as I am always loosing the cursor by unintentionally touching the keypad.

---

### Post by Paddy Landau on 2012-11-22
What do you mean by the keypad? I presume you do not mean the keyboard. Do you perhaps mean the built-in mousepad on a laptop?

---

### Post by borgward on 2012-11-22
Yes, the built-in mousepad, aka touchpad, keypad. keypad is the Dell terminology for it.

Actually, System -> Preferences -> Keyboard -> Mouse Keys -> Unchecked "Pointer can be controlled using the Keypad" Kind of works, say if you can type 60 wpm.

The trouble is that the pad becomes active again after any short pause. I found I can boot to setup and disable the pad, but I do not want to reboot to setup everytime I want to disable the pad.

---

### Post by Paddy Landau on 2012-11-22
The laptops that I have seen over the past few years come with a button to disable or enable the mousepad. It is usually some kind of Fn (function) key; for example, my son's laptop uses Fn+F9 to toggle the status. In my experience, this key combination works with Ubuntu.

I'm sorry I am not of more help. There must be a way to disable the driver, but I don't know it.

---

### Post by chapra on 2012-12-01
"pointer can be controlled using the keypad" refers to controlling the mouse pointer using the numeric keypad on a desktop keyboard.  

If you have a desktop, pressing numlock while holding the shift key down causes the pointer to move in up/down/left/right/diagonal directions, if this option is checked. Pressing numlock and shift again resumes the normal keypad function.

That option shouldn't do anything to the mousepad.  There is a way to completely deactivate the mousepad, as well as to disable it temporarily while typing. I could use both options when I had an HP laptop. 

Unfortunately, neither seem to work on my Dell. In Ubuntu 10.04, you can try: 
system settings ->mouse and touchpad->disable touchpad while typing. That will deactivate the mouse pad for two full seconds after you've hit a key, making it impossible for you to accidentally brush the mousepad.

This worked for me with an HP, it may work for you.  I don't recall how I originally deactivated the entire touchpad with the HP, before I found this solution.

If all else fails, the solution I found for my piece-of-crap Dell is to just take a piece of cardboard and tape it over the mousepad. It's got to be a firm piece of cardboard. The backing of a legal pad won't work. you need something from a box.

Chopra

---

