---
title: "Desktop Won't Appears!?"
date: 2008-02-06
forum: General Help
---

### Post by Suma_Bagher on 2008-02-06
hello
last night i was working on linux normally,,
but this morning when i try to start my pc , the consol command appears like if i pressed ((  alt+ctr+F1  ))
i tried to stop the /etc/init.d/gdm and start it again but still the same problem,, i also tried alt+F7 i see a black screen - no Desktop -
i think the last thing i did before i shutdown linux was
sudo apt-get clean

any answer?
thx

( sorry for my english :) )

---

### Post by aeiah on 2008-02-06
see what your xorg.log files have to say about things. they're located at /var/log/Xorg.log.0 (xorg.log.1, xorg.log.2 etc...)

---

### Post by Suma_Bagher on 2008-02-06
i attached a pgoto of the error :(

---

### Post by Suma_Bagher on 2008-02-06
hello...
i just fixed the problem :lolflag:

i saw a lot of people had the same as i did :mad:

 i just stopped the kdm and reinstalled the nvidea driver
and i started the kdm again and it works now... and i hope it still :KS

thanks anyway for your help :)

---

### Post by 16777216 on 2008-02-06
I installed updates yesterday that broke boot, I had to boot in recovery mode the no VT problem was part of this so I fixed that now I get the tty login screen except mine ( says cannot set console font not enough room on device. )
That is not verbatim but pretty close. BTW I have plenty of HD space.

---

### Post by tbaac on 2008-02-06
Mine wouldn't go into KDE on boot, just to the prompt.  If I typed startx it would start.
The nvidia driver made no difference but I did have kdm-kde4 installed with kdm-kde4 as the default display manager.
I had to remove it and reinstall kdm-kde4 (as I couldn't remember how to reconfigure it otherwise) so I typed
sudo apt-get remove kdm-kde4
sudo apt-get install kdm-kde4

When it asked for the default I chose kdm (rather than kdm-kde4) and after rebooting this worked.

Do we have a bug with kdm-kde4?  (I realise its still new obviously)
Thanks.

---

### Post by Suma_Bagher on 2008-02-06
yeah ,, lot of people had the same problem :(

i think it's something with the reconfiguration of the  xserver & xorg!!?
maybe :confused:

is it a bug or i did delete some files!?

---

