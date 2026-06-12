---
title: "Text to speech impossible to turn off 14.04 LTS"
date: 2014-04-22
forum: General Help
---

### Post by lennart3 on 2014-04-22
Hi, I am very pleased with the new LTS release of Ubuntu-it works great on an old Toshiba Satellite Laptop !
But there is one very annoying "feature" that seems impossible to get rid of....
When started there is a text to speech thing that is speaking in a strange language (chinese???).
I browsed forums and found that there is indeed a text to speach program package included.
When looking in /etc.I found that package entries both in the local and main etc folders.
I commented out all entrances found in the files both in  the local and main etc directories (as sudo) and checked
that there were no entries that would cause the program to work.
But it continues to work any way. I rebooted a few times but without luck.

So - how to get rid of this thing ?
Otherwise I am very pleased with this Ubuntu release - it is a strong competitor to Windows !

---

### Post by Christmas on 2014-04-22
I'm not sure which one is included in Ubuntu, but it may be Orca. You can try to do **ps aux|grep orca** and then kill all instances of Orca. If your program appears to start up automatically, one way to disable it could be to remove the execute permissions after killing it **sudo chmod a-x /usr/bin/orca**.

---

### Post by grahammechanical on 2014-04-22
In System Settings>Universal Access we can turn off the screen reader. Or we can use Alt+Super+S. You might want to check at the login screen that screen reader is not activated there. I think that it is the human icon in the top panel. I do not think that this is activated by default. But we never know. Features that are annoying to you would be very useful to a blind person.

Regards.

---

### Post by lennart3 on 2014-04-22
Thanks to both of you !
Yes it was Orca that caused the trouble - what I did was a bit more drastic than suggested...
What I did was to uninstall Orca from the installation menu. I do not need it.
Now everything works fine, thanks a lot for your feedback !

---

