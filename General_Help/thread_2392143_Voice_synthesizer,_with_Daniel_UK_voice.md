---
title: "Voice synthesizer, with Daniel UK voice"
date: 2018-05-17
forum: General Help
---

### Post by Drenriza on 2018-05-17
Hi all
For an experiment that i am currently fiddling with i would like to be able to download a voice synthesizer with the Daniel UK voice.
Example of the voice here (youtube) [https://www.youtube.com/watch?v=YFwc_egzP7g&t=15s](https://www.youtube.com/watch?v=YFwc_egzP7g&t=15s)

This example is for Windows, and i doubt it's source to be honest.
Is their a way on Ubuntu to download a voice synthesizer with the language pack in question? In a way
that dont download a series of crap ware, viruses or other junk.

Do we have it in the repo perhaps?

Any advice are most welcome.
Thanks in advance![URL="https://www.youtube.com/watch?v=yj3dhTnyotY"]
[/URL]

---

### Post by HermanAB on 2018-05-17
Install packages 'festival' and 'espeak'.

Daniel and the voice used by Apple Siri, are standard voices in these packages.

---

### Post by Drenriza on 2018-05-17
Thanks for the reply HermanAB!

---

### Post by Drenriza on 2018-05-23
Hi @HermanAB
I have now gotten around to play with festival on ubuntu 16.04.
Do you know where i can get the Daniel UK voice file?
Do we have a voice repo somewhere to get such files from?

I know you write
> Daniel and the voice used by Apple Siri, are standard voices in these packages.
But i cannot find anything resembling the voice in the link i gave earlier

Example for festival,
when i run $festival and $(voice.list) i can only see kal_diphone as voice.
Is this a package of voices or a single voice?

---

### Post by HermanAB on 2018-05-23
I don't know if Daniel is here:
[http://festvox.org/festival/downloads.html](http://festvox.org/festival/downloads.html)
[http://www.cstr.ed.ac.uk/downloads/festival/2.4/voices/](http://www.cstr.ed.ac.uk/downloads/festival/2.4/voices/)

It's been years since I played with Festival and Daniel was in the original distribution.

---

