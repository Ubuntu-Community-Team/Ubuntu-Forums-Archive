---
title: "Firefox crushes and goes gray"
date: 2007-02-18
forum: General Help
---

### Post by yurukov on 2007-02-18
I've got kubuntu+beryl on an acer laptop. I love Firefox. I have used only firefox and made most of my friends use it too. I was shocked to see it freeze in linux. It was like breaking my world apart. 

Here's what happened - I was browsing around and at some point it started reading the harddisk a lot and stopped reacting. The mouse started moving at about 5 frames per second. Then the whole system froze. I thought that the x server is out, but the mouse still moved a bit and the harddisk was reading as hell. Also the firefox window went in gray colors and the back to normal. All this happened 4-5 times in the last week.

Then I did the Alt+Ctrl+F1, ps-ed the processes and killed firefox. When I switched back to the X server it was ok. I am not sure what I was browsing - I think it was google maps and some other heavy ajax stuff. My guess is that the program was overloaded and took too much momory or something. That should not be happening. I wish I could have taken screenshots, but the system was in too bad shape to run that.

Help :confused: !

---

### Post by xopher on 2007-02-18
This probably has to do with a plugin. Eg. Flash / Java. Are you on a 64bit system?

---

### Post by yurukov on 2007-02-18
Nope, not a 64. Could be a plugin, but I cannot recall having any opened pages with flash/java on them. Good possibility thought. Hasn't that happened to anyone else?

---

### Post by yurukov on 2007-02-19
Here is a screenshot of a crush. Also I found out that VLC and quicktime crushes the same way.

---

### Post by forkd on 2007-12-21
I found this link by searching after having the same issue.  I get it by cruising youtube so i assume it is the flashplayer.  I installed the flashplayer from 8.0x a few days ago and everything else seems to work.  

I initially thought there might be some issue but chkrootkit came back clean and firestarter is good.  nothing in general dmesg either so I must stick to the flashplayer theory.

---

### Post by TidusBlade on 2007-12-21
I have heard that the official firefox, like one not from the repos is more reliable, so you might wanna try it out [here](http://www.mozilla.com/en-US/firefox/?from=getfirefox).
EDIT: Woah, this is an old thread :S

---

