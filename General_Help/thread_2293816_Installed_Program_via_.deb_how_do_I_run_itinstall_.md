---
title: "Installed Program via .deb how do I run it/install shortcut in Start Menu?"
date: 2015-09-07
forum: General Help
---

### Post by roler2 on 2015-09-07
I installed a MP3 Player via .deb-now how do I run it? Do I type the name of the Player in the terminal? Do I have to move the contents of the installed Player folder to a different location?

I also separately installed a Plugin Pack which contains codecs for the Player. Will the contents of the Plugin Pack automatically install with the Player? Or do I have to run that separately?

Is there a way to place a shortcut for the Player in the Sound & Video Section of the Start Menu?

Thank you in advance for any assistance.

---

### Post by ian-weisser on 2015-09-07
What is the application called?
Where, exactly, did you obtain it?
What flavor and version of Ubuntu are you running?

How to easily start your application depends on the desktop environment you are running, and how well the application developers integrated it into that environment.

---

### Post by roler2 on 2015-09-07
The Program is QMMP. I got the file from the QMMP download section and converted it to a .deb file. Unfortunately, I found out too late that I have to utilize quake to install and make it run. I don't know how to do that and it doesn't seem to be worth the hassle. All I am used to installing are .deb files. The QMMP Developer came out with a new version 9 that doesn't run very well. Lots of bugs. My playlists are a mess. Freezes constantly. So I am trying to go back to the older version 8.

I am currently utilizing Audacious but the sound is horrible and I cannot get the audio to clear up. Very distorted. Utilizing the equalizer actually helped. The audio with QMMP was excellent. . .well. . .with version 8 that is. 

The Ubuntu Repository has version 7. Can I utilize the files in version 8 to override the version 7 files? If so, how do I do that so I don't mess up the installation?

Is there an alternative to Audacious that utilizes a WinAmp interface that has good audio? Or is there a way to clear up the distorted audio?

Lubuntu 14.04

Any assistance would be greatly appreciated. Thank you!

---

### Post by Dennis N on 2015-09-08
With Lubuntu, you could try using pulse audio with Audacious: ( install 2 packages: pulseaudio and pavucontrol). In Audacious preferences, you can set Audio > Output Settings to: PulseAudio output (but it may not be necessary - try it and see).

---

### Post by roler2 on 2015-09-08
Thank you for the suggestion. I do have PulseAudio already installed. The pavucontrol didn't do much to help. I still get distorted audio when I utilize Audacious. The audio was terrific with QMMP. Too bad the Developer changed some of the functions of QMMP. It was working great until Version 9. The Playlists don't even organize correctly, nor can you change them to the lists that were present in Version 8.

---

### Post by Bucky Ball on 2015-09-08
QMMP is in the repositories and that is the one you should be using as that is the version tested, passed, and known to work on your currently installed OS release. Install stuff from outside the repos at your own risk. There are no guarantees it will work or that it will work with your release. It may screw your system soundly or work great. Who knows? We generally don't unless we've bothered to try.  

Have you tried the version in the repos???

---

### Post by roler2 on 2015-09-09
I was able to manually make changes to the QMMP config file. That has helped the Playlist issue. The audio is still vastly superior to Audacious. The current version, 0.9, does have some bugs.

---

