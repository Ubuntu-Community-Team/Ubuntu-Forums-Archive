---
title: "[SOLVED] T60 System Beep Problem"
date: 2008-01-22
forum: General Help
---

### Post by prince_niceguy on 2008-01-22
I am having T60 laptop. Sound is working perfreclty fine and I have the alarm disabled in bios.

I have unchecked the system beep in the sound preferences. Still the annoying pc beep sounds. It is driving me crazy especialy when I am listening to audio. Not sure how to fix it. Please help!!!

---

### Post by mikelito on 2008-01-22
I remember having a similar problem. I don't remember how I fixed it, but I did, so don't lose hope.
you could try appending to the end of your .bashrc file (from a terminal, gedit ~/.bashrc) the line

if [ $TERM = xterm ]; then xset b 0; fi 

I also vaguely remember that the beep can be disabled from the bios, so give it a try.

let me know if either of these fix it, otherwise I'll look harder :)

cheers 
m

---

### Post by Whiffle on 2008-01-22
do 

sudo modprobe -r pcspkr

and add 
blacklist pcspkr 

to 

/etc/modprobe.d/blacklist

---

### Post by prince_niceguy on 2008-01-22
thank you whiffle and mikleto... solution from whiffle worked... and it removed the annoying beep sound... 

also checked my speaker and mic are working... i can hear through amarok and record through sound recorder.

thanks again...

---

### Post by Ohwii on 2008-04-06
Thank you! 

I had the same problem 1 min ago. thanks to you, I could solve it. :popcorn:

but now the sound is not working :(

Cheers 


Oh wii

---

