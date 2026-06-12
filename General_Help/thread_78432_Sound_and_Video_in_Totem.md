---
title: "Sound and Video in Totem"
date: 2005-10-18
forum: General Help
---

### Post by badboyz107 on 2005-10-18
Hey guys someone give me a hand here....I put Ubuntu on a computer for my parents (probably a mistake since they are 60+ but with window$ copyright..grrr) and ever since I have had issues with sound and video being intermitent on .wmv (and other ms sound/video files) in totem....Everything else seems to work just fine...including mp3's etc....only videos seem to have the problem

Choppy sound with no video
Video but no sound
Sound with no video

Suggestions and help are much appreciated or they will flip their lid and make me  put win98 on it.....agh!!

---

### Post by Murgle on 2005-10-18
have you installed the w32codecs?  if not look [here]("https://wiki.ubuntu.com/RestrictedFormats").

---

### Post by badboyz107 on 2005-10-18
yeah I just did that...however most of it said that it was already up to date....I did it anyway so I'll give it a shot and see....keep checking on me!!  thanks!

---

### Post by badboyz107 on 2005-10-18
CRAP....same shit different hour....no none of the codecs seemed to solve the problem....any other suggestions?

---

### Post by mykey on 2005-10-18
sudo apt-get install vlc

;o)

---

### Post by Murgle on 2005-10-18
also try 
sudo apt-get install totem-xine 
if you don't have that already.

---

### Post by badboyz107 on 2005-10-18
okay going to try those as well...will post more when I find out how it does...thanks

---

### Post by badboyz107 on 2005-10-18
Still a no go on any of that....doestn play video with the vlc, or with totem still....sweet mercy smile on me....argh!!!!

---

### Post by mykey on 2005-10-18
Hey 
vlc comes with all the codecs you need - are you sure your video files are o.k.? if so check the drivers for your soundcard and the ones for your graphicscard too - play with the different soundsystems - alsa - oss. on my machine totem gives me the images but no sound .. vlc plays everything without probs.

---

### Post by Shabba on 2005-10-18
Could i suggest that you try Easy Ubuntu [http://placelibre.ath.cx/keyes/index.php/2005/09/29/45-easy-ubuntu-23](http://placelibre.ath.cx/keyes/index.php/2005/09/29/45-easy-ubuntu-23) to ensure all the codecs are up to date. Also, i've never had much joy with Totem but vlc is 100% on anything windoze can output :)

---

### Post by badboyz107 on 2005-10-18
Okay I'll try that easy ubuntu link....I'm running out of hope

Yeah the files themselves are just fine I can send them to a xp machine and they are okay...something about ubuntu (or at least my install) that they dont like....vlc definatly didnt like them...lol

---

### Post by badboyz107 on 2005-10-19
[QUOTE=Shabba]Could i suggest that you try Easy Ubuntu [http://placelibre.ath.cx/keyes/index.php/2005/09/29/45-easy-ubuntu-23](http://placelibre.ath.cx/keyes/index.php/2005/09/29/45-easy-ubuntu-23) to ensure all the codecs are up to date. Also, i've never had much joy with Totem but vlc is 100% on anything windoze can output :)[/QUOTE]


Okay stupid question I suppose but I dont know how to install this once I had downloaded it to the computer...

And nothing I have do so far (have followed all suggestions and searched posts) has resolved this problem so what do I need to try next??

---

### Post by badboyz107 on 2005-10-28
WAAHOOO Everything seems to work now I am so damn happy and so are my parents!!  Thanks for the help everyone...

OH just in case your curious...the Easy Ubuntu seemed to solve the problems....gotta love it!!

---

