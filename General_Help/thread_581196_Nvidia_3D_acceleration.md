---
title: "Nvidia 3D acceleration"
date: 2007-10-19
forum: General Help
---

### Post by trackrat on 2007-10-19
I have just installed Gusty Gibbon and then I enabled Nvidia 3D acceleration and it said I had to reboot, on rebooting it came up with the splash screen,  then I had a message( monitor input out of range), so I rebooted and the same happened again.
As I did not now how to disable the 3D acceleration from the command line, I did another install and just to test it out enabled those drivers again and the same happened.
Is this a known bug?, has anyone else had this problem.

---

### Post by technoidiot on 2007-10-19
This happened to me about a week ago with 7.04. Somehow my setting for Nvidia and the flat panel got all messed up. go thru ALL of your settings, and reset to your system. As I remember this fixed my problem

---

### Post by bryston on 2007-10-24
Trackrat
how did you enable the 3D acceleration for nvidia?  I have  an Acer aspire 9304 with nvidia geforece go7600 and cant get any 3D acceleration.  I have searched the forums but cant find anything on how to do it.
Can you advise?
thanks in advance.

---

### Post by Nunu on 2007-10-24
Going to sound a bit technical but you might need to configure XORG.CONF and limit the perimeters for the display to 70Hz and which ever resolution you need.

---

### Post by Nunu on 2007-10-24
When it boots it goes into command line right?

Try this
 dpkg-reconfigure -phigh xserver-xorg

---

### Post by bryston on 2007-10-24
thnks for reply nunu
i should explain a bit more,
feisty boots up fine and works great.  I am trying to get google earth to work but it freezes on the  splash screen.  All the research i have done points towards my 3D acceleration not enabled. 
i may be wrong though
cheers for the fast response

---

### Post by Qwerty_ on 2007-10-24
Bryston, installing the restricted drivers should get you up and running.

System>Administration>Restricted Drivers Manager.

---

### Post by bryston on 2007-10-24
Qwerty, thanks for that
i have tried that, upon clicking on the restricted drivers manager i get a dialogue box saying my hardware doesn't need any restricted drivers

---

