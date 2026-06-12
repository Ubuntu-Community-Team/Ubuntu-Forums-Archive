---
title: "feisty fawn locks up semi-randomly"
date: 2007-05-24
forum: General Help
---

### Post by pixeltarian on 2007-05-24
motherboard - DFI ultra infinity Nforce2
CPU - athlon xp 2800
ram - 1GB (corsair)
video - nvidia FX


I'm pretty new to ubuntu adn linux in general. when I leave my computer for a while (usually overnight) it freezes and all I get is my caps and scroll lock lights blinking. It happened today when I was in the middle of using it though. I poked around the system log, but wasn't sure/didn't see anything suspicious. 

I know this isn't enough info probably, but I thought someone may have seen this kind of thing before or knows what the blinking caps and scroll lights mean. 

let me know of any additional info needed and how to access it. 

thank you so much for your help in advance,

- pixeltarian

---

### Post by pixeltarian on 2007-05-25
oh please help. someone? I can't really use ubuntu until I figure this out... it gets worse every time I have to illegally shut down. 

I might get rid of windows all together if I can fix this. granted I get my audio interface up and running.

---

### Post by borris.morris on 2007-05-25
this was happening to me when i restarted my networking. just seems kind of random to me as well.

---

### Post by kolanos on 2007-05-25
If you're using the nvidia drivers, Ubuntu just recently updated the nvidia-glx and restricted-drivers-common packages with the latest drivers. Apparently there were known freezing issues with the previous version of the Nvidia drivers. So do a "sudo update && sudo upgrade" and hopefully that will help.

also, here's a long thread on the subject with numerous potential solutions (assuming a driver update doesn't work or is not an option):
[http://ubuntuforums.org/showthread.php?t=412125](http://ubuntuforums.org/showthread.php?t=412125)

---

### Post by pixeltarian on 2007-05-25
thanks a lot man, I'll give that link a try...

---

