---
title: "From Text to Speech: offline program."
date: 2018-10-24
forum: General Help
---

### Post by irv on 2018-10-24
I use an online program called "From Text To Speech," that works great, that is when it is working. I find that their site is down or working slow when it is overused.
Maybe I should not complain because it is free to use. But seeing I use it a lot, I was wondering if someone knows of a stand-alone program that is not an online app.
How the program works and what it does:
I copy and paste a text file into it, and it converts it to an audio file using a digital voice. It allows you to chose a language, a voice, and the speed of reading. After it is done it allows you to save the file as an mp3 format.
Does anyone know of a program like this?

---

### Post by HermanAB on 2018-10-25
There are many solutions.

$ espeak "I cannot do that, Dave." >dave.wav
$ sox dave.wav dave.mp3

Or as a one liner:
$ espeak "I cannot do that, Dave." | sox - dave.mp3

---

### Post by irv on 2018-10-25
Yes, that will work, but it is one of the worst digital voices I've ever heard. I create audiobooks, and that would be like listening to a robot.

---

### Post by HermanAB on 2018-10-25
If don't like the voice, install Festival and get a different voice.  It has a few good voices, male and female, including an Irish voice that sounds like Apple Siri.

---

### Post by irv on 2018-10-26
I have it set up to read the selected text but would like to pipe it to an mp3 file. How would I assign it to do this?
```
xsel | festival --tts --pipe

```

I created a sample audio file I would like to use, but have no idea where to file it.
[This is what it sounds like.]("http://wabasha-server.net/Audio_Files/Sound-File-Sample.mp3")

---

### Post by #&amp;thj^% on 2018-10-26
I use something like:
```
espeak -f myfile --stdout | ffmpeg -i - -ar 44100 -ac 2 -ab 192k -f mp3 final.mp3

```
Change to your needs
EDIT I should mention that>> the --stdout option to espeak will tell it to write the audio data to stdout instead of putting it through the audio device. From there you can pipe it into e.g. ffmpeg for conversion to the proper format.
EDIT2: To use the voice you need use something along the lines of this:
```
 espeak -v mb-en1 -f '/home/me/Documents/a surround sound setup.' --stdout | ffmpeg -i - -ar 44100 -ac 2 -ab 192k -f mp3 1final.mp3

```

---

### Post by HermanAB on 2018-10-26
There are many ways to skin this cat:
$ xsel | festival --tts --pipe >file.wav
$ xsel | festival --tts --pipe | sox - file.mp3
$ xsel | festival --tts --pipe | ffmpeg -i - -ar 44100 -ac 2 -ab 192k -f mp3 file.mp3

---

### Post by irv on 2018-10-26
Thanks a lot for all the help. When I find the right voice I will have to play around with all these commands. I have already made a script to read text from anywhere that I highlight it. But I still don't like the voice. I wish I could find Harry's voice file, the one I posted a sample on.

---

### Post by HermanAB on 2018-10-26
Voice files for Festival:
[https://ubuntuforums.org/showthread.php?t=751169](https://ubuntuforums.org/showthread.php?t=751169)
[http://homepages.inf.ed.ac.uk/jyamagis/software/page54/page54.html](http://homepages.inf.ed.ac.uk/jyamagis/software/page54/page54.html)
[http://festvox.org/festival/downloads.html](http://festvox.org/festival/downloads.html)
[https://ubuntuforums.org/showthread.php?t=677277](https://ubuntuforums.org/showthread.php?t=677277)

---

### Post by irv on 2018-10-29
Thanks for all the input. I will mark the thread as solved.

---

