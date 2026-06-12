---
title: "Cracking sound"
date: 2007-11-17
forum: General Help
---

### Post by Koybe on 2007-11-17
Hello,

Since I'm using Linux, Fedora before, Ubuntu since Dapper I was never able to get a good sound quality. Everything run smoothly on Windows, I have quality speakers. I have a nforce2 motherboard.

All I found is lowering the PCM volume.. And yeah it nearly works. But I have to get it so low, I  need to push upper the volume from the speakers and I still run the same problem. I also turned off 'software mixing' in sound preferences with no luck.

It's a real problem as I use my Linux for everything but games and I nearly never boot Windows. This sound quality issue is then quite annoying.

Is there anyone who solved this issue?

Thank you.

---

### Post by ljubom on 2007-11-17
I just want to mention that I have the same problem - however it is not present in all applications. E.g. wesnoth (game) has this effect, however some music playing program like amarok not. I have a Asus P5B motherboard, Core 2 Duo and kubuntu 6.10.

Bye,
Ljubo

---

### Post by imon9 on 2007-11-17
yes, i have solved the same issue on my previous laptop,

here is guide i posted last time:
[http://ubuntuforums.org/showpost.php?p=2590500&postcount=11](http://ubuntuforums.org/showpost.php?p=2590500&postcount=11)

---

### Post by Koybe on 2007-11-17
Oh THANK YOU! It sounds a lot better. I was looking for this for years!

I removed this :
```
sudo apt-get remove gstreamer0.10-fluendo-mp3
``` And do what you did about alsa.

Nice!

---

### Post by imon9 on 2007-11-17
u're welcomed :)

---

