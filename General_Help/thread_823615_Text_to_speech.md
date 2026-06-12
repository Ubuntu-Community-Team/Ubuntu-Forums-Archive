---
title: "Text to speech"
date: 2008-06-09
forum: General Help
---

### Post by sponsoredwalk on 2008-06-09
Hi i am on 7.10 and am wondering if there are programs on ubuntu 7.10 that read text out loud in a computer-y voice, i am almost positive they exist on ubuntu but cannot find anything anywhere. thanx very much in advance.

---

### Post by fooman on 2008-06-09
espeak ?

try this in a terminal:

```
espeak ubuntu
```

i'm at work on a windows machine ATM so i can't test it out myself.

---

### Post by sponsoredwalk on 2008-06-09
Hey thanks a million, its great, been looking for it for a while and i had it all along :KS, but its hard to understand the instructions on the site and i would love to get the hang of it, please correct me where i go wrong,
~$ espeak -f /home/zxcv/mainClass.txt
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000

i try to play this text file but this is what i get, i can't keep typing text into a terminal because some of it is very long and i must press [return] or "enter" at every full stop to continue playing.
Thank you very much.

---

### Post by dje on 2008-06-09
Is there another program using sound eg. a paused song in a media player? if so close it and try again

hope that helps,
dje

---

### Post by cariboo on 2008-06-09
You could give speex a try. It is in the repository.

Jim

---

### Post by sponsoredwalk on 2008-06-09
I cd to the directory and type -  espeak -v mb-en1 -s130 -f mainClass.txt - and this works fine, which is great!!!
I see that there is a way to export the whole text file to a .wav but if i try 
:~$ espeak -s130 mainClass.txt -w /home/zxcv/mm3.wav  
i get a file mm3.wav but theres no audio and it is 93bites,
if i keep the -v mb-en1 in then i get - Failed to read voice 'mb-en1'. It is possible to export to a .wav the file right?

---

### Post by fooman on 2008-06-09
i believe you need the "-f" in the following:

```
espeak -s130 mainClass.txt -w /home/zxcv/mm3.wav
```

try it like this, see if it works:

```
espeak -s130 [COLOR="Red"]-f[/COLOR] mainClass.txt -w /home/zxcv/mm3.wav
```

---

### Post by sponsoredwalk on 2008-06-09
Wow thank a lot for the help, i can really use this program, :)

---

