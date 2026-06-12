---
title: "software for text to speech"
date: 2013-06-05
forum: General Help
---

### Post by mahboob218 on 2013-06-05
hi everyone 


can any one tell me about the software which can help me in speaking the text , like the software ''talk it '' for ubuntu?

i tried two or three software from ubuntu software center but those were of no use ,those software don't have good pronunciation , softwares like '' gespeaker '' etc .those don't work very well . is there any other software which can pronounce words offline with good pronunciation ?

---

### Post by Lars Noodén on 2013-06-05
There are several described here:

[https://help.ubuntu.com/community/TextToSpeech](https://help.ubuntu.com/community/TextToSpeech)

but one of the main ones for accessibility seems to be Orca:

[https://help.ubuntu.com/community/Accessibility](https://help.ubuntu.com/community/Accessibility)

---

### Post by slickymaster on 2013-06-05
I believe **espeak** is installed by default, if not it is in the repositories. Also in the repos, you have [Festival]("http://www.cstr.ed.ac.uk/projects/festival/") and [Orca Screen Reader]("https://help.gnome.org/users/orca/stable/").

You also have a few online good options:
[Oddcast Text to Speech]("http://www.oddcast.com/home/demos/tts/tts_example.php")
[AT&T Text to Speech]("http://www2.research.att.com/~ttsweb/tts/demo.php")
[Acapela Text to Speech]("http://www.acapela-group.com/text-to-speech-interactive-demo.html")

Another possible option could be [Cepstral]("http://www.cepstral.com/"), but it has a downsize to it since it's paid software.

---

### Post by mahboob218 on 2013-06-05
thanks ,, Lars Nooden

---

### Post by frytek on 2013-06-07
Check here: 

[http://ubuntuforums.org/showthread.php?t=2111436&p=12488983#post12488983](http://ubuntuforums.org/showthread.php?t=2111436&p=12488983#post12488983)

And here's a demo of your post, synthesized on my Mint (Ubuntu-based system)

[https://dl.dropboxusercontent.com/u/187581/kendra-g.mp3](https://dl.dropboxusercontent.com/u/187581/kendra-g.mp3)

this solutions uses SAPI on a dedicated wine installation, so it works flawlessly. demo voices in many languages are available on ivona  / acapela webpages. 

if you want to use a linux-only solution try to install mbrola (with voices). gespeaker workes with mbrola voices powered by espeak. in my recent mint this did not worked, though, as some paths were incorrect - you have to check it yourself. but instead of playing with these settings I would still recommend SAPI, because the effect is - as you can hear - very good. 

and one way of explanation: orca is a system of reading the content of the screen (for the blind). it can use many speech synthesis engines, while espeak is just the default. orca can work with SAPI, I believe, so you could use the solution I mentioned above. but I don't think you want to read the entire screen - probably just system messages and / or some text files. in this case you don't need orca. 
and if you do, I would recommend to switch to a special ubuntu distro for people with disabilities - because everyting will be configured out-of-the-box.

---

### Post by marko5 on 2014-04-23
I have to say, almost a year later, none of this software is something i would want to use on a regular basis, because it's all half-baked crap.

The usual open-source phenomenon: many different groups inventing the same wheel: as the result, none of the wheels work well.

I have a decent amount of linux end-user experience. After fiddling with all this trashware for a couple of hours now - libgnome-speech7, festival, orca, gespeaker, apt-getting anything that might be useful - i have yet to be able to make my system read a simple pdf file to speech. The speech quality is from the last century - the age of the typewriter. 

To expect an average vision-limited person to be able to make any of this garbage work on linux would be a pipe-dream - purely inhumane and pointless torture... lol

Even downloading that massive acroread 9.5 package didn't do it. That 90 MB of bloat didn't make any sound whatsoever! lol

[SOLVED]?! In you wildest dreams this issue isn't solved! It would have been solved if all these different dev groups would work together, but the open-source pencil-neck devs don't work that way: each one sealed inside there own silo, a chief of their separate repository of crapware, which only they know how to make work properly with just the right >%%&*#.conf /bash .hotbot >> .yahoo command...
lol
</rant>

---

