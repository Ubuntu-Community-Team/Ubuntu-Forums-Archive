---
title: "Volume Control doesnt effect firefox?"
date: 2006-12-06
forum: General Help
---

### Post by raveneffct on 2006-12-06
So..why doesn't the volume control (in upper right) effect the volume of videos that I play in FireFox, like say YouTube. I would really appreciate the help. Thanks in advance.

I mean, I knew it wasn't going to be easy configuring everything in Linux..but god damn, for something that is supposed to be easier and more user friendly than windows xp...I have had way more problems with Ubuntu then I ever had with Windows..

---

### Post by raveneffct on 2006-12-06
Anyone? I really want to get this working properly.](*,)

---

### Post by DougieFresh4U on 2006-12-06
That **'Volume Control'** in the **upper right corner** has been **useless** to me and I have posted many many times and have got no helpful replies. Good luck, wish I could help! :evil:

---

### Post by raveneffct on 2006-12-06
> **DougieFresh4U said:**
> That **'Volume Control'** in the **upper right corner** has been **useless** to me and I have posted many many times and have got no helpful replies. Good luck, wish I could help! :evil:

I know?! This is ridiculous. I love Linux..but god damn, all these little issues REALLY annoy me. Please someone...anyone:confused:

---

### Post by frogfusious on 2006-12-06
Try right clicking the volume control icon, hitting preferences and setting it to 'PCM', instead of 'Master'.

---

### Post by raveneffct on 2006-12-06
> **frogfusious said:**
> Try right clicking the volume control icon, hitting preferences and setting it to 'PCM', instead of 'Master'.

When I right click the volume control icon it brings me to a drop down menu which consists of the following

SigmaTel STAC9221 Ai (OSS Mixer) - Which mine is set
HDA Intel (alsa Mixer)
USB Device (alsa mixer)

I don't see anything with PCM

---

### Post by DougieFresh4U on 2006-12-07
When you right click on Master Volume Control in the upper right corner, your supposed to get a drop down that consist of: Mute>Open Volume Control>Preferences>Help>About>Remove From Panel>Move & Lock To Panel.  Now I clicked open 'Open Volume Control' then when that opened I clicked: Edit>Preferences , then I put a check mark in PCM & Headphone as those are the only 2 that work. you should see 'sliders' for thocse 2 that you checked, and that is how I control volume as a 'Master'. I know it' a pain to keep opening to get to 'sliders' but I deal with it. It' worth a shot, hope it helps :cool: Dougie!

---

### Post by raveneffct on 2006-12-07
> **DougieFresh4U said:**
> When you right click on Master Volume Control in the upper right corner, your supposed to get a drop down that consist of: Mute>Open Volume Control>Preferences>Help>About>Remove From Panel>Move & Lock To Panel.  Now I clicked open 'Open Volume Control' then when that opened I clicked: Edit>Preferences , then I put a check mark in PCM & Headphone as those are the only 2 that work. you should see 'sliders' for thocse 2 that you checked, and that is how I control volume as a 'Master'. I know it' a pain to keep opening to get to 'sliders' but I deal with it. It' worth a shot, hope it helps :cool: Dougie!

Hmm..PCM was already checked off. I just want to be able to control all volume with the volume control at the top right :(  Also Headphones wasn't even an option for me.

Right now the "upper-right" volume control is vertually useless.

---

### Post by DougieFresh4U on 2006-12-07
Sorry, I tried. I don't know how I got Headphone in there. I can appreciate the fact that you want the 'Master Control' to work as I also wish for the same. I had several post over the last 2 -3 weeks and and no one stepped up with the winning solution. So I have to use the 'hackey' way(is that even a word:confused: ) Useless isn't the word of choice I have for upper right corner switch!! Piece of %%^t!

---

### Post by Adramelech on 2006-12-07
The solution is already posted:

Right click on volume control from the drop down menu choose preferences then highlist PCM

This is different from right click -> open volume control then preferences.

---

### Post by raveneffct on 2006-12-07
> **Adramelech said:**
> The solution is already posted:

Right click on volume control from the drop down menu choose preferences then highlist PCM

This is different from right click -> open volume control then preferences.

I have done that...affects absolutely nothing.

---

### Post by DougieFresh4U on 2006-12-07
Thank you Adramelech. I now have control over my 'upper right corner volume' It was explained to me in another way, and I am glad you cleared that up for me

---

### Post by raveneffct on 2006-12-07
> **DougieFresh4U said:**
> Thank you Adramelech. I now have control over my 'upper right corner volume' It was explained to me in another way, and I am glad you cleared that up for me

Please explain it to me in the way that you got it to work!

---

### Post by Adramelech on 2006-12-07
glad it worked for you =)

@raveneffct: From the dropdown menu try chosing intel HDA (alsa mixer) and then highlight PCM below the drop down menu, if PCM is not listed, try restarting X, Ctrl+Alt+Backspace

Im just guessing so i dont know if it gonna work.

---

### Post by raveneffct on 2006-12-07
> **Adramelech said:**
> glad it worked for you =)

@raveneffct: From the dropdown menu try chosing intel HDA (alsa mixer) and then highlight PCM below the drop down menu, if PCM is not listed, try restarting X, Ctrl+Alt+Backspace

Im just guessing so i dont know if it gonna work.

It is listed, I highlighted it, then closed out...But it still doesn't affect anything :( (ex: When playing a youtube video, using that volume control does nothing)

---

### Post by Adramelech on 2006-12-07
hummm right click -> open vulme control -> play with slices =) find wich one actually change the volume and then repeat the process changin PCM with that one =), btw, whats that usb device? a modem?

---

### Post by raveneffct on 2006-12-07
> **Adramelech said:**
> hummm right click -> open vulme control -> play with slices =) find wich one actually change the volume and then repeat the process changin PCM with that one =), btw, whats that usb device? a modem?

It might be the webcam I have plugged in (It has a microphone in it) I hope it is cause I have no idea what else it would be.

*Does some stuff, comes back to reply*

Got it to work! Instead of PCM I hit surround, which works!

---

### Post by DougieFresh4U on 2006-12-07
I am wondering if you have played with the alsa mixer.some thing could be muted there. sorry I don't know the code to get at that maybe Adramelech can guide you on that if you have no luck with his other suggestions. I can say this though:it bothered the sh^t out of me for about 3 weeks and Adramelech did the trick                                                         EDIT: Good for you, I see you got it!:cool:

---

