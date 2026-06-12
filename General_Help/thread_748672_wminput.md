---
title: "wminput"
date: 2008-04-07
forum: General Help
---

### Post by sekinto on 2008-04-07
So I downloaded the Wiimote drivers for Linux and after playing FoF with my Guitar Hero 3 guitar I decided I wanted to do more. So I open up one of the wminput configuration files and they say things like:

somebutton = KEY_A
someotherbutton = BTN_LEFT

So obviously in this case when you press somebutton it would be like hitting the A key and when pressing someotherbutton it would be like left clicking. I want to change some things, but the problem is that I don't know the names of the events, is there anywhere I can find a list of events that do certain things (ex. cursor up, #7 key, middle click, et cetera...).

---

### Post by sekinto on 2008-04-07
Anyone?

---

### Post by sekinto on 2008-04-08
Does anyone know where I can find a list?

---

### Post by mgschwan on 2008-06-18
Hi i am not sure if you still need the key names but you can find them in the source of cwiid, (either in action_enum.c or action_enum.txt)

Here is a link to the file
[http://abstrakraft.org/cwiid/browser/trunk/wminput/action_enum.txt](http://abstrakraft.org/cwiid/browser/trunk/wminput/action_enum.txt)

Greetings 
mgschwan

---

