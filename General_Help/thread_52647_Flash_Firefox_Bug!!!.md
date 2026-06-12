---
title: "Flash Firefox Bug!!!"
date: 2005-07-28
forum: General Help
---

### Post by DimitrisChr on 2005-07-28
Well i am not sure if this is a bug or something went wrong with the installation of flash player but since all other web pages appear fine (i don't know about the ones that use text like the following, but use animations and buttons only) i think there is a bug with flash player and firefox.
I am using firefox and flash player from the apt-get sources in the ubuntu guide.
As you can see from the following pics firefox in windows displays the flash animation with text where firefox in ubuntu does not.
Any ideas? 
Thanks in advance!!!

[IMG]http://i16.photobucket.com/albums/b39/LinuxRulez/WindowsXP.png[/IMG]

[IMG]http://i16.photobucket.com/albums/b39/LinuxRulez/UbuntuLinux.png[/IMG]

---

### Post by Holdem on 2005-07-28
Link to the above page would be good.
Then I'll let you know if it's just your PC.

---

### Post by Caboto on 2005-07-28
Do
sudo apt-get install gsfonts-x11 msttcorefonts
and you should be fine.

---

### Post by DimitrisChr on 2005-07-29
Well i installed the packages you said but i still can't view the page correctly.  Its a little bit better than before but i can't see text.
By the way the page is [www.mbides.com](www.mbides.com)

Here is a screenshot of what i get after installing the packages you suggested.
Thanks again!

[IMG]http://i16.photobucket.com/albums/b39/LinuxRulez/Screenshot.png[/IMG]

---

### Post by Caboto on 2005-07-29
I've got the exact same result. Seems like you (we) are missing some cyrillic fonts (Not quite sure what language that is, sorry). Perhaps you should try to search via Synaptic for "font" and install some xfont-cronyx or xfont-bolkhov packages?
I'm not sure, if it's really that. But it looks like missing fonts.

---

### Post by DimitrisChr on 2005-07-29
Thanks again for your help. The language is Greek  :razz: 
I will try to install some xfonts and see if it fixes the problem!

---

