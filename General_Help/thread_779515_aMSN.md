---
title: "aMSN"
date: 2008-05-02
forum: General Help
---

### Post by Springy2 on 2008-05-02
Since I upgraded from 7.10 to the latest version the sound and visual notifications stopped working
any help please?

---

### Post by ajmorris on 2008-05-03
hi there,
could you please start amsn from a terminal, and post any errors when sounds should play, but dont, or even if you use the test sound function in properties.

Aj

---

### Post by X-626 on 2008-05-03
I was having the same problem.  More than likely, you have it set to use the 'play' command to play the audio file.  After running the command manually, I got the same thing that I had from the terminal:
```
play soxio: Failed reading `type.wav': unknown file type `auto'
```You can change it under the Preferences.  It's under the "Others" tab.  Where it says "Sound server:" you will need to check "Use the Snack library (Tcl internal)".  Afterward, click the Save button, and it should work.

As for the visual notifications, I am not sure about that.  They aren't working for me, either.

---

### Post by Springy2 on 2008-05-04
ajmorris: I don't get any errors, the sound works fine in any other application 

I did what X-626 suggested and the sound is now sometimes working and sometimes not,I still want to get the blinking chat window to work again too when a new message is recieved
(And again, both stopped working just like that after the upgrade finished)

Thanks for the answers :)

---

### Post by profediego on 2008-05-08
Me have the same problem,... any solutions yet???

---

