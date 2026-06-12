---
title: "xmms-shn plugin"
date: 2005-05-18
forum: General Help
---

### Post by fluideye on 2005-05-18
Didn't see much discussion or how to play shn files so here is what I did to install xmms-shn. 

# sudo gedit /etc/apt/sources.list

Append follwing line to end of list:  

deb [http://www.rarewares.org/debian/packages/unstable](http://www.rarewares.org/debian/packages/unstable) ./

Hope it helps.  Anybody else have a better solution?

---

### Post by torstenprahl on 2005-10-07
You Rock!

I spent all day trying to figure this out.

Thanks,
T

---

### Post by fluideye on 2005-10-08
Glad it helped!

---

### Post by graabein on 2005-11-18
Does this work with beep-media-player as well?

---

### Post by AndrewB on 2007-04-24
the missing key

---

### Post by mikeize on 2007-05-04
I can't seem to get this to work in Feisty Fawn.  Can anyone tell me how to enable shn playback in ubuntu?  I tried this, and I tried installing xmms-shn from source... nothing is working.  Linux is giving me a big headache :confused: 

-mike

*edit*  [http://ubuntuforums.org/showthread.php?t=25201&highlight=shn]("http://ubuntuforums.org/showthread.php?t=25201&highlight=shn")

found the answer here.

---

### Post by Kamesennin on 2007-08-11
Hi!
I had the problem that when I try to install the .deb for xmms-shn from [http://www.rarewares.org/debian/packages/unstable](http://www.rarewares.org/debian/packages/unstable) I saw an error in Feisty. And I couldn't install the plug-in...
Then I tried to install the shorten plugin since source from xmms.org. I downloaded the tarball and when I configured [./configure] I received a lot of errors. many of them said that I hadn't installed xmms >=1.0.0; glib, gtk, etc. I knew I had installed these but only the binary packages not the devs, I installed each dev package of the errors that I see.. And voilà... The plugin was configured, compiled and installed without problems and now I can hear my Shorten \\:D/

---

