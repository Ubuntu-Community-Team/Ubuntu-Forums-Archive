---
title: "No sound after upgrade to mate 16.1"
date: 2017-06-10
forum: General Help
---

### Post by gaherzog on 2017-06-10
I have no sound. I am not command line literate, but I can follow directions. I just upgraded from ubuntu 16.04.2 to ubuntu mate 16.1 because I could not deal with the desktop environment of the  ubuntu 16.04.2.  alsamixer is greyed out and the sound preferences menu option shows dummy output and for input it shows monitor of dummy output. the audio worked fine with the ubuntu 16.04.2. the computer is a gateway LT4004u netbook.

lspci: 00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)

aplay: device_list:268: no soundcards found...

thanks in advance for any assistance

---

### Post by gaherzog on 2017-06-10
solved.*I found this solution  [https://itsfoss.com/fix-sound-ubuntu-1304-quick-tip/](https://itsfoss.com/fix-sound-ubuntu-1304-quick-tip/)  *and had to go right down the line*to the very last*suggestion.*at that point*I had to install*gedit. upon opening the file it was already*no.*so I changed it to yes.*and when I rebooted*all the sound was working.

---

