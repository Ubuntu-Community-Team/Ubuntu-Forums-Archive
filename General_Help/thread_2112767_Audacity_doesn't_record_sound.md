---
title: "Audacity doesn't record sound"
date: 2013-02-05
forum: General Help
---

### Post by Vladimir Pavic on 2013-02-05
[COLOR=#314004][FONT=Verdana, sans-serif][SIZE=2]Dear friends, yesterday I installed Audacity (sound editing software) in my Ubuntu 10.04. However, the software doesn't recognise any input sound – it doesn't record. I tried fiddling around with settings, but all in vain. At the moment, my settings are as shown in the attached images. What do I have to change to be able to record sound?[/SIZE][/FONT][/COLOR]
 

 [COLOR=#314004][FONT=Verdana, sans-serif][SIZE=2]Thank you.[/SIZE][/FONT][/COLOR]

---

### Post by Thee on 2013-02-05
What about other sound applications like sound recorder, skype... are they detecting the mic ok?

---

### Post by Vladimir Pavic on 2013-02-06
A good question! I have just realised that the Sound Recorder doesn't recognise microfon either. (I don't have Skype installed). So, it seems that I have to change some microphone settings. But, what and how?

---

### Post by furything on 2013-02-06
I have had similar but with windows. My issue was usb headphones.

Put in a normal mike into the red/pink jack and tell windows to use that. Restarted audacity and it picked up that mike.

Are you using usb headphones?  Just a thought....

---

### Post by Vladimir Pavic on 2013-02-06
I don't use USB headphones. I use external microphone and I plug it correctly in the mike socket.

---

### Post by dannyboy79 on 2013-02-06
do you use pulseaudio? open pavucontrol if so and check it's configuration. also, check alsamixer to make sure your mic isn't muted

---

### Post by Vladimir Pavic on 2013-02-07
A friend of mine changed something in micophone settings and - now it works! Thank you all for help and concern.

---

