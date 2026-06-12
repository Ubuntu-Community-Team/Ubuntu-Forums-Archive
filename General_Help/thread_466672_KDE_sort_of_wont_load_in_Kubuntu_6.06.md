---
title: "KDE sort of wont load in Kubuntu 6.06"
date: 2007-06-07
forum: General Help
---

### Post by BradNeuman on 2007-06-07
I've been using Kubuntu 6.06 64 bit version for 7 or 8 months now with only a few problems, but today it suddenly locked up, not accepting any input, but it seemed to still be running all of my applications fine (I was using gaim and I could actually see IMs i was getting). I did a hard reset and everything seemed to load up fine but I couldn't log in through KDE. Sometimes it would flash the screen and bring me right back to the KDE login (as if the X server were reseting), and other times it flashes the screen and then just sits there. Sometimes I can switch to terminal 1 and log in, but other times it does the same flash and then sit there thing.

I'm pretty sure I didn't change anything and the really weird part is that I can still get in by logging into the console as root (using the system restore boot option in GRUB) and then start the x server and run a session as root and everything works.

I really don't know where to begin with this and I haven't been able to find any similar cases on the forums.

thanks,
Brad

---

### Post by pbw on 2007-06-07
Try moving your kde settings and logging in fresh. Could be some saved setting or startup application from the crash. Sounds like a config problem to me, if root session works fine.

mv ~/.kde ~/.kde.bak

See if things work after trying that, if they do and you really need some of your old settings, then you can bring some configs back after and leave out the suspect ones.

-- pbw

---

