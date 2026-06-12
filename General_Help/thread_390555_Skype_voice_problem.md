---
title: "Skype voice problem"
date: 2007-03-22
forum: General Help
---

### Post by rockymaxsource on 2007-03-22
Hey,

I installed latest ubuntu succesffuly on my Dell Inspiron 1300. Since I could not apt-get install skype. I downloaded skype 1.3.0  debian source from skype.com and use dpkg installed the skype. Everthing works fine the only problem is dial to echo123 I can not record any audio to there although I can hear the ringing tone and the audio hints for testing. I tried to skype to my friends to test but I can not hear from him and he can not hear from me. Can any of you help me out please?

Blessings,
Rocky

---

### Post by PurplePenguin on 2007-03-22
Hi Rocky!  You'll need to open up alsamixer or alsamixergui and make sure that you've got the correct settings (to take sound from your microphone).  You're not the only one - this question gets asked at least two or three times a week, it seems!   Here's a link to [HOWTO: Get your microphone to work.]("http://ubuntuforums.org/showthread.php?t=386832")

It might need a bit of playing with, but it will work!

---

### Post by giuseppe.dem on 2007-03-22
I have another problem
I installed Edgy. 
1) Skype gives bad audio (slow)
2) Other applications (game) give slow and intermmittend audio

Anyone has some suggestions?
G

---

### Post by mahy on 2007-03-22
> **rockymaxsource said:**
> Hey,

I installed latest ubuntu succesffuly on my Dell Inspiron 1300. Since I could not apt-get install skype. I downloaded skype 1.3.0  debian source from skype.com and use dpkg installed the skype. Everthing works fine the only problem is dial to echo123 I can not record any audio to there although I can hear the ringing tone and the audio hints for testing. I tried to skype to my friends to test but I can not hear from him and he can not hear from me. Can any of you help me out please?

Blessings,
Rocky

I'd recommed gnome-alsamixer. It has far more capabilities than generic alsamixer. Just enable everything regarding capture, recording and microphone.

---

### Post by mahy on 2007-03-22
> **giuseppe.dem said:**
> I have another problem
I installed Edgy. 
1) Skype gives bad audio (slow)
2) Other applications (game) give slow and intermmittend audio

Anyone has some suggestions?
G

You can install the newest ALSA drivers (1.0.13) from [http://www.alsa-project.org](http://www.alsa-project.org)

Steps (in Terminal):

1.) sudo apt-get update
2.) sudo apt-get install linux-headers-generic build-essential
3.) Download the ALSA drivers. Unpack them like this: tar xjvf [filename].tar.bz2
4.) Go into the newly created directory: cd [filename]
5.) ./configure
6.) make
7.) sudo make install
8.) sudo reboot

That's it. Feel free to ask more questions.

---

### Post by tlacuache on 2007-03-22
> **giuseppe.dem said:**
> 
...
1) Skype gives bad audio (slow)
...
Anyone has some suggestions?
G

I had that same problem with recent versions Skype in Edgy on my laptop (but not on my home pc, for some reason).

What I finally ended up doing was downloading an older release (1.2.0.18) and running it instead. I didn't have the problems with slow, stuttery audio with the older version.

I believe this is the link I used:

[http://download.skype.com/linux/skype_staticQT-1.2.0.18.tar.bz2](http://download.skype.com/linux/skype_staticQT-1.2.0.18.tar.bz2) 

-SG

---

### Post by rockymaxsource on 2007-03-22
> **PurplePenguin said:**
> Hi Rocky!  You'll need to open up alsamixer or alsamixergui and make sure that you've got the correct settings (to take sound from your microphone).  You're not the only one - this question gets asked at least two or three times a week, it seems!   Here's a link to [HOWTO: Get your microphone to work.]("http://ubuntuforums.org/showthread.php?t=386832")

It might need a bit of playing with, but it will work!


Hey,

Thank you very much for your reply!

I did follow the instruction you offered and > vumeter -r  gives me there are voice get recorder when I tap on the microphone. 

The problem is calling to echo123 in skype still not be able to listen to my voice though I can hear the Skype system testing voice. On my another PC which installed Debian stable has the same problem I changed sound device in Skypes option to OSS and it works but on my Ubuntu Inspiron1300 the problem is still there. Can any of you give me further assistance please?

Someone mentioned gnome-alsamixer how can I do the configuration please I input that in terminal nothing happens.

Thanks a lot in advance!
Rocky

---

### Post by drpaul on 2007-03-23
If you are running Edgy Synaptic has it as alsamixer-gui. I just installed it and it does nothing more than alsamixer. I think it's a waste of space. YMMV

Paul

---

### Post by alzoubi on 2007-03-27
i installed the skype but it's not supported with sound recording> **rockymaxsource said:**
> Hey,

I installed latest ubuntu succesffuly on my Dell Inspiron 1300. Since I could not apt-get install skype. I downloaded skype 1.3.0  debian source from skype.com and use dpkg installed the skype. Everthing works fine the only problem is dial to echo123 I can not record any audio to there although I can hear the ringing tone and the audio hints for testing. I tried to skype to my friends to test but I can not hear from him and he can not hear from me. Can any of you help me out please?

Blessings,
Rocky

---

