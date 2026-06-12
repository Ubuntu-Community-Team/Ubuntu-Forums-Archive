---
title: "Skype Issues."
date: 2006-11-04
forum: General Help
---

### Post by lodravah on 2006-11-04
I am in a pickle.. 

Had Skype newest version installed, worked fine. Am using Dapper with Xfce/GNOME. Today I suddenly started having serious sound problems while talking. I can hear the other person loud and clear, but when I speak i hear myself with a lag of about half a second, and in addition there are weird loud "wooobly wooobly" - sounds in the background and also other noise that makes communication impossible. I have no idea what happened. I have not touched the settings lately. Using ALSA with Skype. So, I decided to do a reinstall after checking all soundsettings. The mike works after trying it with "sound recorder" and "Skype Test Call Service.." 

However, after reinstall and "sudo apt-get update" I get an error msg saying "database problems.." So now I not only have sound problems, but also a non - working skype. The errormsg is attached as a *.jpg. I was thiking I maybe need to purge skype - files?

Anyone?

lodravah:confused:

---

### Post by lodravah on 2006-11-04
Problem update..

Seems that the "database" - problem was caused by light crash of my desktop. Skype was still running but no windows or other means of telling was visible. Had to shut down the process and reboot. So now I can start it again, but the sound problems continue..

I can start and log in and all, but when I talk to people; firstly I can hear myself with about a half-second delay, secondly the sound is completly twisted, thirdly I can hear loud "wooobly wooobly" - sounds in the background everytime I try to talk and fourth the mike seems to have become severly sensitive. If I just run my finger over it, SKYPE makes screeching and other loud sounds in my ears. Even if I just tap my mike. Now the fun part is that everything works fine when calling the "test-number" (echo123, skype call test service). But when I'm talking to people, the sound problems show up.. All my ALSA settings and hardware are okay. They work perfectly with other apps, and mic/capture settings are all in place. I did nothing to change the settings beforehand. Skype just decided to bug me.. 

Anyone have an idea? Appreciate any help..

lodravah

---

### Post by lodravah on 2006-11-04
Hm, seems there might be a kernel - problem, according to this:
[http://forum.skype.com/index.php?showtopic=67860&st=0&gopid=315762&#entry315762](http://forum.skype.com/index.php?showtopic=67860&st=0&gopid=315762&#entry315762)

Does it help?

---

