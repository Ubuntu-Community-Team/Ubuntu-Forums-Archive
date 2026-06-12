---
title: "Can't listen to YouTube!!!"
date: 2008-05-23
forum: General Help
---

### Post by durkhrod chogori on 2008-05-23
Can anyone pass on the command to update Flash Player in FF for Ubuntu 8.04?

Thanks in advance.

---

### Post by FuturePilot on 2008-05-23
I think this has to do with Flash Player and PulseAudio. Do you have any other sound applications running like Rhythmbox or something? If you do, close them and restart Firefox and try again.

---

### Post by durkhrod chogori on 2008-05-25
Hi,

No, I don't have anything running while trying to listen to YT.

???

Cheers.

---

### Post by Cerberu2 on 2008-05-25
installed needed plugins?,,if is firefox, a message in top appears, go tat and install the needed plugins :)

---

### Post by durkhrod chogori on 2008-05-26
Yes I installed plugins. Still doesn't work.

Btw, what the hell is "TAT"??? Duh!!

---

### Post by Cerberu2 on 2008-05-27
try do this:

go to "system->preferences->audio settings",change everything to pulse audio and :

 apt-get install --reinstall > pulseaudio libflashsupport


keep posting

---

### Post by sgreddin on 2008-05-27
I had the same issue. I use Rhythmbox and flash wouldn't play at the same time as my player. Also, even after restarting both Firefox and Rhythmbox, Rhythmbox would simply not play. But i fixed it by going System> Prefernces> Sound, switched Sound Events, Music and Movies, and Audio Conferencing to PulseAudio Sound server. You may need to only swithc Music and Movies, but i ytypically go for overkill to make sure it works. Next, Alt+F2 and type "killall pulseaudio". At this point my computer slowed down, froze for a few moments, and then resumed. It still wouldn't play from Rhythmbox but i simply rextarted the computer, and now I have simultaneous audio and no freezing
Hope this helps!

---

### Post by sizzam on 2008-05-27
I was having the same problem with Flash videos crashing Firefox.  There is an open bug ticket for this here:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888)


I corrected the problem for myself with steps gleaned from the bug ticket, details are in this post:

[http://ubuntuforums.org/showpost.php?p=5057137&postcount=5](http://ubuntuforums.org/showpost.php?p=5057137&postcount=5)

I have been crash-free since performing these steps.

---

### Post by VTshredder on 2008-05-27
Tried so many options and this one worked best for me!  Thanks a ton!!!!
No more crashing or sound issues after i followed your directions. 


> **sgreddin said:**
> I had the same issue. I use Rhythmbox and flash wouldn't play at the same time as my player. Also, even after restarting both Firefox and Rhythmbox, Rhythmbox would simply not play. But i fixed it by going System> Prefernces> Sound, switched Sound Events, Music and Movies, and Audio Conferencing to PulseAudio Sound server. You may need to only swithc Music and Movies, but i ytypically go for overkill to make sure it works. Next, Alt+F2 and type "killall pulseaudio". At this point my computer slowed down, froze for a few moments, and then resumed. It still wouldn't play from Rhythmbox but i simply rextarted the computer, and now I have simultaneous audio and no freezing
Hope this helps!

---

