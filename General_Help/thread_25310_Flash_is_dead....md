---
title: "Flash is dead..."
date: 2005-04-09
forum: General Help
---

### Post by mglukhovsky on 2005-04-09
Although Flash worked for me at one time, it has ceased to function. It doesn't matter if I'm using Firefox, Epiphany, Opera, or Konqueror. Even if I download an swf and try to use an SWF player on it, nothing plays. I suspect a recent Hoary upgrade broke this, but I can't be sure. I completely removed all Flash packages and installed flashplayer-mozilla, libflash0, and libflash-swfplayer one at a time, but nothing changed.

If anyone has any idea what may be causing this, please clue me in. I used [http://www.motograndprix.com/en/motogp/index.htm](http://www.motograndprix.com/en/motogp/index.htm)  as a test site, because it is a flash/html site that shows the problem at its worst Here is a screenshot attached to show the problem:

---

### Post by humanity_to_others on 2005-04-09
You can install flash via firefox by pressing the notification at firefox.

---

### Post by mglukhovsky on 2005-04-09
No... flash is detected, but it doesn't render correctly. Take a look at the attached image I posted: you can see yellow-brown rectangles in the upper-right corner of the animation but no actual rendering occurring. Moreover, no such notification even appears (which is why I said it is detected).

---

### Post by fackamato on 2005-04-09
Flash died for me too, some days ago. It doesn't matter if I apt-get install the flash, or use it from macromedia's site. I do get an error though, in firefox' toolbar at the bottom "plugin initatliztaion failed, try to reload the page", which of course doesn't work. **Note**: Some flash things does work, apparently old versions.. Or something. ;(

---

### Post by mglukhovsky on 2005-04-09
How do flash animations appear for you in their broken state? Do you see the same brown-yellow rectangles shown in the screenshot I attached?

---

### Post by fackamato on 2005-04-09
[QUOTE=mglukhovsky]How do flash animations appear for you in their broken state? Do you see the same brown-yellow rectangles shown in the screenshot I attached?[/QUOTE]

Hmm, [http://www.tehjunkyard.net/heyhey16k.swf](http://www.tehjunkyard.net/heyhey16k.swf) works for me. Could you give me an URL to a flash that doesn't work for you?

---

### Post by jeremy on 2005-04-10
this problem occurs when the .swf is embedded, and the size is set as a percentage rather than the true pixel size.
As far as I can see, this is a firefox/linux problem, it does not occur on other platforms (as far as I know).
The [http://www.tehjunkyard.net/heyhey16k.swf](http://www.tehjunkyard.net/heyhey16k.swf) example works beause the link goes directly to the flash file, rather than an .html page with the flash embedded.

---

### Post by mglukhovsky on 2005-04-10
Sadly, this doesn't work for me either. Take a look at the attached screenshot: I've got the same result. And no, it isn't a firefox/linux problem. No other browser can display Flash animations for me, and the standalone swf players won't either. Any ideas as to why flash would be completely broken?

---

### Post by mr.tulo on 2005-04-10
i dont get any sound, whats up with that?

---

### Post by jeremy on 2005-04-10
[QUOTE=mr.tulo]i dont get any sound, whats up with that?[/QUOTE]
 [http://ubuntuforums.org/showthread.php?t=21011](http://ubuntuforums.org/showthread.php?t=21011) has the answer to this.

---

### Post by mglukhovsky on 2005-04-10
An update on the problem: I tried opening the flash animation (swf) I downloaded in Totem, and I got sound, but no video. Clearly the rendering process isn't occurring.

---

### Post by zwaardmeester on 2005-04-16
I have a similar problem with Opera (8 beta3) and flash 7.0 r25. Opera freezes when I try to open a Flash file, but after +/- 30 seconds it begins to play (but i do have sound though).

EDIT: i have my flashproblems solved now. Opera was waiting for operamotifwrapper-1 to time out before starting operamotifwrapper-2. To find out which one you have to use, execute this:

> locate libXm.so

which returns libXm.so.N.xxx with N.xxx the version number. This N is also the operamotifwrapper you need. Goto /usr/lib/opera/plugins/ and rename the others (as root).

more info: [http://www.forum4designers.com/message208482.html](http://www.forum4designers.com/message208482.html)

---

### Post by mglukhovsky on 2005-04-16
[QUOTE=mglukhovsky]An update on the problem: I tried opening the flash animation (swf) I downloaded in Totem, and I got sound, but no video. Clearly the rendering process isn't occurring.[/QUOTE]
 Just wanted to thank everyone for their reponses and let people know that I've fixed the problem by removing ALL files relating to flash on my system, and reinstalling flashplayer-mozilla. Thanks again!

---

