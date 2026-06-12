---
title: "UTF8 Text Problem"
date: 2007-09-25
forum: General Help
---

### Post by augegr on 2007-09-25
Hi to all

I opened a file cp1253 encoded, with kate. I changed the encoding inside kate to cp1253, and the text is readable. I select all the text, copy, paste in new utf8 text and save. The generated file is indeed utf8, readable by all linux editors and media players (srt file).
When I try to open it in windows using Wordpad the text is broken. If I try notepad it is displayed correctly. If I press save while in notepad, the text is readable in all windows and linux programs. 

Why is it that neither kate nor gedit can save utf8 like notepad does, so it will be readable everywhere? I have selected DOS/WINDOWS as End of Line, if that makes any difference.

---

### Post by leonidas666 on 2007-09-25
I am not a expert, but i think that some programs use a invisible utf8 character as the first character in a file as a "marker" to indicate files in utf8 encoding. You could open the file in a hex editor to find out what exactly is the difference.

In any case, i suspect that actually wordpad is having a non-standard behaviour, not kate.

---

### Post by augegr on 2007-09-26
Thanks for your answer. Unfortunately this is not the case for Wordpad as none of my media players show the subtitles correctly (and I have set all of them to use utf8 subtitles) either. 

I really can't find out what the problem may be..

---

