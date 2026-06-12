---
title: "skype installation issues."
date: 2005-06-17
forum: General Help
---

### Post by byen on 2005-06-17
hey guys.
I tried installing skype using 

sudo apt-get install libqt3c102-mt
wget -c [http://frankandjacq.com/ubuntuguide/skype_1.1.0.13-1_i386.deb](http://frankandjacq.com/ubuntuguide/skype_1.1.0.13-1_i386.deb)
sudo dpkg -i skype_1.1.0.13-1_i386.deb

skype installs but is not working properly...the main log-in window takes over 2 minutes and then hangs for a while and after giving my user name and psswd it fails to connect. is there anything Im doing wrong in this installation?

please suggest. I use skype a lot to talk to my family so it wud mean a lot if someone can help me out here,...
thanx.

---

### Post by Chen_Zhen on 2005-06-17
I also have problems with skype. The istallation went smoothly but for some reason my microphone seems dead and other people cannot hear me. Does anyone have any clues? Thanx in advance

---

### Post by byen on 2005-06-21
wow... no one? well..just incase someone pops in, here is what is happenning.after installing skype i try logging in but the window gets smudgy and after i type my username and password it fails to connect... says invalid username and password...i know 4 sure they are right!! so I checked the active connections on my firewall and i dont see skype...so is it the firewall...? anyone...anything?

---

### Post by WiXP on 2005-06-21
I took the the tar ball from Skype's website and it works fine here. If you have problems with your microphone I suggest to "contact" the Skype user "echo123". Calling this user gives you an echo of your voice after a few seconds - maybe this helps ...
Ciao
Wolfgang
-- 
Linux pinguin 2.6.10-5-k7

---

### Post by byen on 2005-06-21
[QUOTE=WiXP]I took the the tar ball from Skype's website and it works fine here. If you have problems with your microphone I suggest to "contact" the Skype user "echo123". Calling this user gives you an echo of your voice after a few seconds - maybe this helps ...
Ciao
Wolfgang
-- 
Linux pinguin 2.6.10-5-k7[/QUOTE]
 thank you Wixp...will check it out and let you guys know if there is a prob. thanx :-)

---

### Post by allenmaher on 2005-06-25
I too am having trouble trying to get the microphone to work in skype.

I have the Intel HD Audio on board scratchy sound... and configured it from the how to... so now the machine whizzzes bangs and pops.... but no microphone.

Using the volume control to mute un mute turn up, etc... still no joy.  Switching between ALSA/ESD/OSS does not improve things.  All the permissions look good in /dev/ and the users are members of audio.

Any other hints.

---

### Post by byen on 2005-06-25
yeah... during my 1st install it somehow seemed towork very well... but after re-installing ubuntu.. it does not work at all! i tried looking around and it seems to me that this is not an issue with many... damn! i so need this software to work.but i cant get it done!

---

### Post by gratefulfrog on 2005-06-25
I'm trying to install the 1.1 skype, but this just won't go on AMD 64, Hoary, etc.

There is an outstanding bug in HOARY, the front panel mic connector will not work!
Workaround: use the rear panel!

As to the mic issues themselves, i suggest trying to record sound on the mic first. To do that:
1. reboot,
2. do not start any sound using application, in particular DO NO START SKYPE:
3. be sure you have followed the instructions at: [http://www.ubuntuguide.org/#configuresoundproperly](http://www.ubuntuguide.org/#configuresoundproperly)
4. in a terminal window, record some sound from the mic:
```
$ rec toto.wav
``` 
5. playback the sound:
```
$ play toto.wav
``` 
6. if this works, then skype has to work, too.
7. if not, without starting any other apps, use the alsamixer to set up the mic as capture device, if you don't mute you should hear yourself through your speakers. 

8. that should do it! 

good luck,
GF

---

### Post by allenmaher on 2005-06-26
Ok I have configured it all according to the link... 

Where do you get rec and play, what package?

The alsa mixer tells me that the microphone is on and working, and I can here my voice through the speakers, but programs will still not record anything... although the y don't send up error messages, only small ripples are visible when recording in audacity, sound recorder still does not work.

No joy using echo123 either.

---

