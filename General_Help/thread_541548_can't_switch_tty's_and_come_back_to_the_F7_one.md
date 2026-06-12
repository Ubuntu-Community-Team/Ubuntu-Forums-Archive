---
title: "can't switch tty's and come back to the F7 one"
date: 2007-09-02
forum: General Help
---

### Post by shane2peru on 2007-09-02
I don't do this often, but it is annoying when I want to be able to do this.  When I want to switch to another tty screen (alt + ctrl + F3 (or any F1-6)  and then try and go back to the F7 one, it gives me some weird blue flashing screen.  I can't recover my running session, at least I don't know how to.  I end up having to run a 'sudo reboot' command to get back into my running session.  Any ideas?  This is really annoying.

Shane

---

### Post by shane2peru on 2007-09-06
Does anyone have any clue about this?

Shane

---

### Post by peromalosutra on 2007-09-07
I have the oposite problem. When I press ctrl+alt+f1 (or any f 1-6) the screan becoms black and I don't see the tty login prompt. Then, when I press ctrl+alt+f7 it swiches back to my X session without any problems.. 

Maby it's problem related to graphic card drivers? I installed binarys downloaded from nVidia oficial site (they weren't awilable through synaptic / apt-get)

---

### Post by mcduck on 2007-09-07
> **peromalosutra said:**
> I have the oposite problem. When I press ctrl+alt+f1 (or any f 1-6) the screan becoms black and I don't see the tty login prompt. Then, when I press ctrl+alt+f7 it swiches back to my X session without any problems.. 

Maby it's problem related to graphic card drivers? I installed binarys downloaded from nVidia oficial site (they weren't awilable through synaptic / apt-get)

I had the same problem on my laptop (with Ati card) and I solved it by making Ubuntu use framebuffer at 1024x768 resolution in VTTs (I simply added vga=792 to the end of the kernel line in /boot/grub/menu.lst).

---

### Post by shane2peru on 2007-09-07
That is funny because I use neither Nvidia or ATI, I have inteli810 or something like that.  It is integrated with the motherboard.  So in theory I should have this problem because of video cards. :)  Glad to know I'm not the only one with these problems though.  :lolflag:

Shane

---

