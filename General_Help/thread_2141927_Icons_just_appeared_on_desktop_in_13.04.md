---
title: "Icons just appeared on desktop in 13.04"
date: 2013-05-04
forum: General Help
---

### Post by barnowl13 on 2013-05-04
I switched on my computer this morning and on the desktop 3 icons have appeared computer, home and trash.

I can not move them or delete them I can open them and get to all my files in the home folder.

If go into properties of this home folder I get Basic/permissions and in permissions it says "The permissions of **** can not be determined"

The three icons still appear on the launcher and work, again if I go in to properties on the Home folder I get Basic/Permissions/Share. 

Have been using Ubuntu for some years now and never really had many problems with it and when I have had a problem managed to sort it out.

Maybe it some thing so simple and I am just being thick but I am stuck on how to get rid of them, so hope some one can put me right?:confused:

---

### Post by 3rdalbum on 2013-05-04
Install Gnome Tweak Tool (Advanced Settings) and use it to hide the Computer, Hone and Trash icons.

Or if you are handy with Gconf-editor, you can change this setting in Gconf Editor. It is actually a Nautilus setting.

---

### Post by barnowl13 on 2013-05-04
Have gone into Gconf Editor and into Nautilus but can the only thing I could find that may relate to these 3 icons was in Nautilus " NM-APPLET STAMP 3?" I use Tweak Tool but could not find how to hide icons. Maybe I am having a bad day it been one of those weeks!! :confused:

---

### Post by grahammechanical on 2013-05-04
Is Unity the user interface? I am asking because some people install alternative user interfaces. Also, 13.04 have dconf editor not gconf editor. Just so that you know.

How have you tried to delete them? You may need administrator privileges. In 13.04 gksudo nautilus will not work unless you install gksu. I find it strange that you have a folder on the desktop called Computer. That is just another way of saying File System. I have just tried to copy my home folder on to the desktop. I get this error message:

> Error while Copying. The folder "dconf" cannot be handled because you do not have permission to read it I am working as a standard user. Can you think of anything that you may have done to cause this? Re-trace your steps, sort of thing?

Regards.

---

### Post by barnowl13 on 2013-05-04
Yes I am using Unity as my interface. Yes I have tried to delete them but delete is shaded as is move, cut copy and move. Oh as regards the icon for Computer is a computer and Trash is a trash bin The home folder is a folder sorry if I have missed lead you on this point? 

Yes I would class myself a standard user and have try to think of anything I have done to cause this but all I did was close down which it did with no problem and open the next day again with now problem but now with these 3 icons on desktop?

I have been using Ubuntu for 7 years now and normal can sort out any problems but this has got me flummoxed?

---

### Post by Frogs Hair on 2013-05-04
See the desktop setting in the Gnome Tweak Tool . In the Unity Tweak Tool it is under desktop Icons.

---

### Post by barnowl13 on 2013-05-04
> **Frogs Hair said:**
> See the desktop setting in the Gnome Tweak Tool . In the Unity Tweak Tool it is under desktop Icons.

Have done this but they are still there!!

It they are there but at the same time not?

---

### Post by barnowl13 on 2013-05-05
Well I have tried everything I could think and tried what had been suggested but to no avail. So bit the bullet and did a reinstall.

So now all is back to normal, it would have been nice to work out why and how but it was doing my head in!! :mad::)

---

### Post by desgua on 2013-05-19
I got the very same problem. Turn out that somehow "Nemo"  was putting these icons on my Desktop. So I opened dconf-editor, then gone to org.nemo.desktop and unset home-icon-visible trash-icon-visible computer-icon-visible. The question now is: how these configuration have changed by themselves?

---

