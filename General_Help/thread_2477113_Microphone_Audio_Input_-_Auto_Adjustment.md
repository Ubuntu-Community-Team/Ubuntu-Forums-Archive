---
title: "Microphone Audio Input - Auto Adjustment"
date: 2022-07-14
forum: General Help
---

### Post by mpbaker82 on 2022-07-14
Hello

I was wondering if there is any settings in the Ubuntu OS (20.04.4) that i could disable the auto microphone adjustment for a external USB microphone. I have a Yeti nano and this thing can pick up a mouse fart from the other side of the room. 
I noticed that if i adjust the mic input volume in volume settings down to about 40-50% and then talk, it's easier on the person on the other side of the line. 

I was looking in the /usr/share/pulseaudio/alsa-mixer/paths/ folder to see if there was anything in there that would help my issue but to be honest there is so many configurations files, i got lost and didn't want to mess with anything.

Thank you

---

### Post by de Bacon on 2022-07-18
I don't know a lot, yet I may know how to assist you.  

I use Ubuntu Studio and there are differences between flavors.  Go to your main ubuntu interface menu, and open "PulseAudio Volume Control."  PulseAudio Volume Control has its graphical user interface.  If you are inexperienced, just make note of what you change, so if changing something doesn't work, change it back to what it was to avoid confusion and or problems.  When your external usb sound card is on, and running, it will be listed separately from other sound devices of your system. 

Good luck,

---

### Post by mpbaker82 on 2022-07-18
thank you de Bacon
I am currently running 20.04 Ubuntu. I was thinking about reimaging to Ubuntu Studio but i dont do alot of studio like task. I may end up trying this but i might look at swapping out my yeti nano with the normal yeti which also includes a gain knob. Im not sure why yeti would push a mic with no ability to control gain. 

thank you again

---

### Post by de Bacon on 2022-07-19
I hope that helped.  If not, we can try to figure it out.

---

### Post by TheFu on 2022-07-19
pavucontrol

---

