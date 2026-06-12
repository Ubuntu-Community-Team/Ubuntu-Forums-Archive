---
title: "[SOLVED] Very Important pls !!"
date: 2007-07-30
forum: General Help
---

### Post by Sawa4.CoM on 2007-07-30
[B]Hello , 

iam new to linux , also iam useing laptop " Fujitsu Siemens " i run ubuntu

but i need the drivers installs ?!!

i can't run songs or any thing the  the system is soo mute!!!!

how can i get it pls 

thanks [/B]

---

### Post by Sawa4.CoM on 2007-07-30
Hey , 

here is no one who can help me pls ?

---

### Post by forestpixie on 2007-07-30
a little bit of patience would help 

which drivers do you think you need?
if it's multimedia you're after

read this thread - it should sort that out for you

[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

you might be better of posting in the Absolute Beginners in future - there seems to be more people looking in there.

---

### Post by Sawa4.CoM on 2007-07-30
> **forestpixie said:**
> a little bit of patience would help 

which drivers do you think you need?
if it's multimedia you're after

read this thread - it should sort that out for you

[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

you might be better of posting in the Absolute Beginners in future - there seems to be more people looking in there.



der forestpixie 

thanks for your time and trying to help me 

i just need to know how can i let the adiuo work fine 

coz my laptop CD's was all for winXP , but iam now useing Linux , 


HOW TO definition THE  sound

thanks

---

### Post by forestpixie on 2007-07-30
"coz my laptop CD's was all for winXP , but iam now useing Linux "

do you mean that all your music files are wma files?

which player are you using in linux

I'm sorry but i'm having a bit of trouble understanding what you want :(

but that's not your fault :)

---

### Post by Sawa4.CoM on 2007-07-30
no sir 

all what i meant i s 

the audio is not working yet what ever if i trying to run songs , games etc... there is no audio ..

---

### Post by forestpixie on 2007-07-30
ok so follow the thread which I posted above - it should get you the drivers you need to get songs going in your system 

:)

---

### Post by Sawa4.CoM on 2007-07-30
hi , 

sir i just need the driver to install so the audio can be work fine

---

### Post by ugm6hr on 2007-07-30
@sawa4.com:
You probably don't need to install drivers for sound - ubuntu has lots pre-installed.
Do you hear any sounds at all?  Try playing a sound (assuming you have the following sound file - otherwise use another sound file):
```
aplay /usr/share/sounds/gaim/logout.wav
```
If that works - then you are probably looking for multimedia codecs.
If it doesn't, then you probably need to configure alsamixer:
```
alsamixer
```
Use the left/right/up/down arrows to maximise all volumes, and "M" unmute (OO) - where MM is muted.
Then try to play the sound again.

PS: Enter Code entries in Terminal: [http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)

---

### Post by Sawa4.CoM on 2007-07-30
> **ugm6hr said:**
> @sawa4.com:
You probably don't need to install drivers for sound - ubuntu has lots pre-installed.
Do you hear any sounds at all?  Try playing a sound (assuming you have the following sound file - otherwise use another sound file):
```
aplay /usr/share/sounds/gaim/logout.wav
```
If that works - then you are probably looking for multimedia codecs.
If it doesn't, then you probably need to configure alsamixer:
```
alsamixer
```
Use the left/right/up/down arrows to maximise all volumes, and "M" unmute (OO) - where MM is muted.
Then try to play the sound again.

PS: Enter Code entries in Terminal: [http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)



Hello sir 


```
sam@Admin-Sawa4:~$ aplay /usr/share/sounds/gaim/logout.wav
Playing WAVE '/usr/share/sounds/gaim/logout.wav' : Signed 16 bit Little Endian, Rate 22050 Hz, Stereo
sam@Admin-Sawa4:~$ 
```

it didnot work , and the problem is driver  coz i donot hear any sounds yet , games , songes , movice  any thing working fine but you donot her any sounds 

pls advice

---

### Post by ugm6hr on 2007-07-30
```
alsamixer
```

Maximise settings - as described previously.

---

### Post by Sawa4.CoM on 2007-07-30
> **ugm6hr said:**
> @sawa4.com:
You probably don't need to install drivers for sound - ubuntu has lots pre-installed.
Do you hear any sounds at all?  Try playing a sound (assuming you have the following sound file - otherwise use another sound file):
```
aplay /usr/share/sounds/gaim/logout.wav
```
If that works - then you are probably looking for multimedia codecs.
If it doesn't, then you probably need to configure alsamixer:
```
alsamixer
```
Use the left/right/up/down arrows to maximise all volumes, and "M" unmute (OO) - where MM is muted.
Then try to play the sound again.

PS: Enter Code entries in Terminal: [http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)

[PHP]AlsaMixer v1.0.13 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA Intel                                                                                                           &#9474;
&#9474; Chip: Motorola Si3054                                                                                                     &#9474;
&#9474; View: [Playback] Capture  All                                                                                             &#9474;
&#9474; Item: PCM [dB gain=0.00, 0.00]                                                                                            &#9474;
&#9474;                                                        [/PHP]

---

### Post by ugm6hr on 2007-07-30
This shows that the sound card is recognised OK. Now maximise all settings! Then try playing sound again.

---

### Post by Sawa4.CoM on 2007-07-30
[PHP] Card: HDA Intel                                                                                                           &#9474;
&#9474; Chip: Motorola Si3054                                                                                                     &#9474;
&#9474; View: [Playback] Capture  All                                                                                             &#9474;
&#9474; Item: IEC958 [Off] [/PHP]


------------------------------------------------
[PHP]
&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.13 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA Intel                                                                                                           &#9474;
&#9474; Chip: Motorola Si3054                                                                                                     &#9474;
&#9474; View: [Playback] Capture  All                                                                                             &#9474;
&#9474; Item: Caller ID [Off]      [/PHP]


------------------------------------------------------------


[PHP]&#9474; Card: HDA Intel                                                                                                           &#9474;
&#9474; Chip: Motorola Si3054                                                                                                     &#9474;
&#9474; View: [Playback] Capture  All                                                                                             &#9474;
&#9474; Item: Input Source [Mic]                                                                                                  &#9474;
&#9474;                                                                                                                           &#9474;
&#9474;                       [/PHP]




--------------------------------------


[PHP]&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.13 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA Intel                                                                                                           &#9474;
&#9474; Chip: Motorola Si3054                                                                                                     &#9474;
&#9474; View: [Playback] Capture  All                                                                                             &#9474;
&#9474; Item: Input Source 1 [Mic]                                                                                                &#9474;
&#9474;                                                                                                                           &#9474;
&#9474;                         [/PHP]



i also maximise all settings! 

no sounds yet !!

pls advice

---

### Post by El Viejo Lobo on 2007-07-30
Ahlan wa-Sahlan  to Ubuntu:)


First try to use the  link  you got on this thread.
If you are using Ubuntu 7.04 you should have no problem it installs codecs when you try to use music. You just need to follow the small windows that pops up. 

Other option that is good for beginners may be using Automatix to install the codecs.
[http://www.getautomatix.com/](http://www.getautomatix.com/)

Mplayer can play WMA  files.


As a good way of going into Ubuntu - always  look for help by: 1.  Google search  2. Forum search 3.  Forum Thread.

  	

Ma'a Salaama

---

### Post by Sawa4.CoM on 2007-07-30
> **El Viejo Lobo said:**
> Ahlan wa-Sahlan  to Ubuntu:)


First try to use the  link  you got on this thread.
If you are using Ubuntu 7.04 you should have no problem it installs codecs when you try to use music. You just need to follow the small windows that pops up. 

Other option that is good for beginners may be using Automatix to install the codecs.
[http://www.getautomatix.com/](http://www.getautomatix.com/)

Mplayer can play WMA  files.


As a good way of going into Ubuntu - always  look for help by: 1.  Google search  2. Forum search 3.  Forum Thread.

  	

Ma'a Salaama



ahlan beek ya man :D  enta feen ya sede we sayebni layes hena :D

Yes i use Ubuntu 7.04 but i just need the Driver  la2en el sound not work  yet :(

i tryed evry thing and no way iam working for that on Google and here more than 2 days now !  didnot fixed .. thats why iam sure 99%  it needs the driver 

thanks Ma Bro

---

### Post by El Viejo Lobo on 2007-07-30
If you are looking for sound problem in general them you can look at: Terminal: " alsamixer"

you will get the control of sound like the one you can see on the attached screenshot.

---

### Post by Sawa4.CoM on 2007-07-30
i did saw yours 

may you see mine pls for more advice if you see some wrong on mine ?


thanks dear !

---

### Post by El Viejo Lobo on 2007-07-30
So you do not have any sound on your laptop - that a different problem then I understood. 
It took me a few month to make my wireless card to work so take it easy.

---

### Post by Sawa4.CoM on 2007-07-30
> **El Viejo Lobo said:**
> So you do not have any sound on your laptop - that a different problem then I understood. 
It took me a few month to make my wireless card to work so take it easy.

Lol, 

i have evry thing working fine even the wireless , Only the sound Problem :S

Still Donot you think i need the driver for fixeing this?

thanks

---

### Post by El Viejo Lobo on 2007-07-30
Try this  
[http://alsa.opensrc.org/Alsamixer#NAME](http://alsa.opensrc.org/Alsamixer#NAME)

---

### Post by ugm6hr on 2007-07-30
> **Sawa4.CoM said:**
> may you see mine pls for more advice if you see some wrong on mine ?

You have not unmuted all channels (although you have maximised).

See the MM or OO at the bottom of each volume? Press "M" to make them all OO.

Then try again.

---

### Post by Sawa4.CoM on 2007-07-30
> **ugm6hr said:**
> You have not unmuted all channels (although you have maximised).

See the MM or OO at the bottom of each volume? Press "M" to make them all OO.

Then try again.


YESSSSSSSSSSS

it worked now :D

many thanks for you sir :guitar:

---

### Post by ugm6hr on 2007-07-30
:)

It's funny how things are different in Ubuntu to Windows.  When you ask for help - try to explain exactly what the symptoms are, rather than jumping to assumptions about what the cure might be.  That way, forum users will be able to help.

---

### Post by Sawa4.CoM on 2007-07-30
> **ugm6hr said:**
> :)

It's funny how things are different in Ubuntu to Windows.  When you ask for help - try to explain exactly what the symptoms are, rather than jumping to assumptions about what the cure might be.  That way, forum users will be able to help.

you are right , iam sorry , and again : thank you so much

---

### Post by El Viejo Lobo on 2007-07-30
> **Sawa4.CoM said:**
> you are right , iam sorry , and again : thank you so much

I am happy that you made it work - This is  what it means when you say UBUNTU. Take it easy man it takes time to learn to use Ubuntu and I mean not only your box but the community too. For me Ubuntu  is a way of life in what is concerning to PC use.    :guitar:

---

### Post by ugm6hr on 2007-07-30
> **Sawa4.CoM said:**
> you are right , iam sorry , and again : thank you so much

No worries.  You are welcome.

You can now experiment with the various alsamixer controls to see exactly which "volume" corresponds to the speakers.  You will find that the headphone volume will be a different control.  PCM tends to be a common control for both (I think).

Of course, now that it works - you could just leave it alone!

PS: Perhaps you could post the full laptop Make/Model for future forum users with the same problem, with a description of which volume controls control which speakers, so they can search for the laptop model and find how you solved the problem.  And you can also mark this thread as SOLVED (click on Thread tools at top of thread).  Also - try and use helpful Titles for help threads - it helps other people searching (e.g. No sound on Fujitsu.... Laptop)  This helps the rest of the community!

---

### Post by Sawa4.CoM on 2007-07-30
Done sir , 

iam gonna do evry thing u said and i alws will be here to try to help as i find some one like you " very cool "  to help me .


i arked it as sloved 


thanks again!

---

