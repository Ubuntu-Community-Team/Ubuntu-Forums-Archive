---
title: "Killing applications"
date: 2008-07-06
forum: General Help
---

### Post by silkstone on 2008-07-06
A strange thing happened earlier on. Someone asked about how to play an mp3 file from a certain website, so I went there and clicked on the mp3 which tried to open in totem but gave an error message. So I saved the file and tried to play it in rhythmbox. No joy. But after that, neither Totem nor Rhythmbox would launch.

When I looked at System Monitor, Rhythmbox was shown as a Zombie, and Totem was shown as 'uninterruptible'. I tried to kill them from System Monitor, but that didn't work - they were still there.

So I tried to restart the machine, and it just hung. I had to do a hard reset (hold the power button). On reboot, everything was OK, but I'm sure there's a better way of killing applications that don't want to die!

Also, what is a zombie?

Any advice appreciated.

P.S. I don't usually have a problem playing mp3 file or streams, so I'm not really looking for a solution to why this particular one would not play - only to how to kill the application when there's a glitch. Thanks.

---

### Post by lamego on 2008-07-06
There is no easier way to get rid of a zombie process (usually the reboot does work, unlike in your case).

For a definition of a zombie process read:
[http://aplawrence.com/SCOFAQ/FAQ_scotec6cantkill.html](http://aplawrence.com/SCOFAQ/FAQ_scotec6cantkill.html)

---

### Post by silkstone on 2008-07-06
Thanks lamego. I'd still appreciate any other suggestions for what I could have done other than a hard reset.

---

### Post by ryanhaigh on 2008-07-06
This is a great way to shutdown your PC when it is unresponsive:
[http://en.wikipedia.org/wiki/Magic_SysRq_key#Raising_Elephants](http://en.wikipedia.org/wiki/Magic_SysRq_key#Raising_Elephants)

---

### Post by hansdown on 2008-07-06
> **silkstone said:**
> Thanks lamego. I'd still appreciate any other suggestions for what I could have done other than a hard reset.

Go to fosswire.com where You can download ubuntu reference cheat sheet. It has the famous R aising S kinny E lephants I s U tterly B oring escape code. Look at the bottom right corner of the cheat sheet under system.

---

### Post by lisati on 2008-07-06
Would this help? ```
sudo shutdown -r now
```

---

### Post by silkstone on 2008-07-07
Thanks for all the suggestions. I've made a note of them but will keep hoping that I won't need them too soon!

---

