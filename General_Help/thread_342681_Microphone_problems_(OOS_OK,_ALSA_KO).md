---
title: "Microphone problems (OOS OK, ALSA KO)"
date: 2007-01-20
forum: General Help
---

### Post by alberto666 on 2007-01-20
Hi.

I have been trying to use the microphone with ALSA mixer in Linux (Ubuntu 6.10) but it is impossible for me.

I have installed Kphone and Skype and they work properly when I use OSS, but when I try to use ALSA, it doesn't work at all.

I have used the alsamixer (command line) to setup the microphone and switch on, also with the Volume Control, but nothing. I can't, it doesn't work.

And when I try to open the application Sound Recorder I have this error:

```
Your audio capture settings are invalid. Please correct them in the Multimedia settings.
```

The microphone is included in the laptop (VAIO Laptop) and it works in Linux since with the OSS driver I have no problem.

Any ideas?

Thank you!

---

### Post by teaker1s on 2007-01-20
just a guess my headphone and mic socket won't work correctly unless I compile and install latest alsa

---

### Post by alberto666 on 2007-01-20
The sound works fine with ALSA, but if I want to use the microphone I have to use OSS, so I need to close all the audio opened applications :(

I have tried in System -> Preferences -> Sound to check ALSA in sound capture, and when I press test, this appears:

```
gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open resource for writing.
```

---

### Post by alberto666 on 2007-01-22
So no info how to do in ALSA?

:(

---

### Post by stami on 2007-02-07
I have experiecied exactly the same problem with ALSA on Ubuntu Edgy 6.10, and this is how I solved the problem:

First of all I restored my default esd.conf:
```
sudo cp -rp /etc/esound/esd.conf /etc/esound/esd.conf.old
sudo gedit /etc/esound/esd.conf
```
replace all the content of the file with these lines:
```
[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 1
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=
```
Then rename /etc/asound.conf if exists:
```
sudo mv /etc/asound.conf /etc/asound.conf.old
```

Now go on System -> Prefereces -> Sound
On the tab Devices select
Autodetect
Autodetect
Autodetect
Alsa - Advanced Linux Sound Architecture

On the Sounds tab enable the two checkbox (I don't remember exactly their names cause my Ubuntu is in Italian)

Restart alsa:
```
sudo /etc/init.d/alsa-utils restart
```

Close and reopen your application (Skype...)

This worked for me, I hope the same for you!

Happy Ubuntu :) :) :) :)

---

### Post by alberto666 on 2007-02-07
It does really works and really fine ;-)

This was the error:
spawn_options=-terminate -nobeeps -as 1

I had -as 2... (this shouldn't be) and -d default (so default device, should that be a problem? weird...).

But now it works!!!

Mille Grazie!!

---

### Post by stami on 2007-02-07
Great, I'm happy that it works for you too.

Prego.):P ):P ):P ):P ):P

---

### Post by aliennet on 2007-02-19
Great solution!
Now, the microphone works perfectly.
The problem starts with the upgradig of ubuntu from dapper to edgy in my laptop.
I had also an error every time I use "gedit". 
I put my old error just could be useful for someone looking for a solution:
ALSA 2146 (snd_pcm_open_noupdate)

Thanks!

---

### Post by gavintlgold on 2007-02-21
Works for me too! I had edited my sound from a howto in order to get audacity to work, but that messed it up.  Now it works again. Audacity didn't until I changed the audacity command to "aoss audacity"

Now it works perfectly! Thanks.

---

### Post by eggdeng on 2007-02-25
Another satisfied customer. Kudos, stami!

---

### Post by vratnica on 2007-04-30
well, I ve followed the instructions but didnt have to change anything, i.e. all the settings I have allready had.


but still my mic doesnt function :( 

yea, I forgot to say that when I try to test Alsa  I cannot hear anything, while the other tests are ok

anything to do?:frown:

---

### Post by morpheus01 on 2007-05-11
This 1 minute solution worked for me just using the GUI:

[http://ubuntuforums.org/showthread.php?p=2635174#post2635174](http://ubuntuforums.org/showthread.php?p=2635174#post2635174)

---

### Post by strangedata on 2007-05-11
Hi,

I have the same problems here too. It's with my HDA VIA VT82xx on Feisty Fawn. I get the sound, and I can hear the mic on the speaker, but applications cannot use it.

Actually, Sound Recorder even records from the microphone, but applications like Gizmo cannot use it (and does not report any error) :confused: 

I think this is pretty bad for Ubuntu. I've been reading tons of similar problems on sound input, all the way back to August 2006, and we still don't have a definitive fix.

I've tried every fix I could find on the web, but the problem is always there. Tried modifying /etc/modprobe.d/alsa-base to add "option snd-hda-intel model=A/B/C/ETC", tried using the command line alsamixer, tried using the gnome-mixer... all to no avail!

How do I test if OSS works?

---

### Post by Gouz on 2007-09-08
I doesn't work for me :(

---

### Post by Genotrius on 2008-01-07
For reference, this is no good on 7.10, at least not with a VT82xx [HDA VIA VT82xx] onboard sound device.

---

### Post by CaTTiusha on 2008-01-22
It worked for me, too. Weeee :D After the change I had some noises but changing the Audio system in Skype preferences to Alsa help and work now perfectly. 

alberto666 Thanks for posting the problem
Stami, a hundred kisses from Ubuntu girl :*

---

### Post by restless on 2008-02-24
i've been reading on this topic pretty much everywhere, and still i can't find the solution for it..

i have a toshiba tecra 8, with the soundcard:
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)


i tried what u guys said, but i get an error message when i try to test the sound capture device..
>>Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat

it is only the microphone that is giving me troubles...all the rest works properly...
any idea on how to solve this problem? i also tried all the inputs in skype, while having a conversation, but none of the 6 worked...
please...tell me that you know how to fix this :)

thanx
Lor

---

### Post by rlmorrisonwy@hotmail.com on 2008-05-24
Many thanks st stami!

I also had this problem (with a fresh installation of Ubuntu 8.04).
Stami's solution solved my problem.:)

---

### Post by rlmorrisonwy@hotmail.com on 2008-05-25
Great help Stami!  This solved my microphone problem too (on a fresh install of Ubuntu 8.04)

---

