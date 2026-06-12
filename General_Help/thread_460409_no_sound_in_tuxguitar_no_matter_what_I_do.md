---
title: "no sound in tuxguitar no matter what I do"
date: 2007-05-31
forum: General Help
---

### Post by Recker on 2007-05-31
> **DeadEyes said:**
> What I did was downloaded the sounbank deluxe from [http://java.sun.com/products/java-media/sound/soundbanks.html](http://java.sun.com/products/java-media/sound/soundbanks.html)
. Set tux guitar to use a custom soundbank and pointed it at the deluxe file.
I then added alsa-oss from the repos.
[b]
$sudo modprobe snd_seq
$aoss ./tuxguitar
[/b]

Edit your /etc/modules and add snd_seq if you want it loaded every time.

I did that. When i type $aoss ./tuxguitar in the terminal, it says...

bash: ./tuxguitar: No such file or directory

I do not understand why it says this. I looked and the directory is there. I did the other steps and still no sound, so this must be very important. Sorry, I am completely new to Linux and Ubuntu... it's probably very easy to fix.

---

