---
title: "sound: i can't hear anything"
date: 2007-10-30
forum: General Help
---

### Post by scuba_suit on 2007-10-30
this morning it was working find, i guess SOMEBODY (like typing in caps the person in my household can hear it) was adding music to their facebook page and probably listening to other things too (i checked out the history to see who and where they went to), is there a way to bring back the sound or check what might be running to kill it so that the sound can be back? i did the [b]ps -A[/a] code to see what was up, but then again i'ma supernoob and don't know what the hell i'm doing (NOT LIKE THE OTHER PEOPLE IN MY HOUSE... there i go again with the caps)

---

### Post by Crafty Kisses on 2007-10-30
> **scuba_suit said:**
> this morning it was working find, i guess SOMEBODY (like typing in caps the person in my household can hear it) was adding music to their facebook page and probably listening to other things too (i checked out the history to see who and where they went to), is there a way to bring back the sound or check what might be running to kill it so that the sound can be back? i did the [b]ps -A[/a] code to see what was up, but then again i'ma supernoob and don't know what the hell i'm doing (NOT LIKE THE OTHER PEOPLE IN MY HOUSE... there i go again with the caps)

Post the following output:
```
lspci
```

---

### Post by bingoUV on 2007-10-30
scuba_suit, don't cry. 
1. Did you try the good old reboot? If some process has acquired your sound and hidden it in the dungeons , it will come back after reboot.

2. Install mplayer and alsa-oss. Do the following
```

aoss mplayer /path/to/music/file

```
Can you hear anythig?

---

### Post by scuba_suit on 2007-10-30
> **Codename said:**
> Post the following output:
```
lspci
```

hey codename, i did **lspci**, all this code popped up, what next? bingoUV, i'll try your method next if there is no avail....

---

### Post by scuba_suit on 2007-10-30
by the way, i've logged off and rebooted and no dice, still nothing... hey codename do i do a "sudo kill" on this:

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)

lemme know

---

### Post by scuba_suit on 2007-10-30
i did this

sudo asoundconf list

and i got one name for the soundcard, how do i make it work or close at this point?

---

### Post by bingoUV on 2007-10-31
> **scuba_suit said:**
> i did this

sudo asoundconf list

and i got one name for the soundcard, how do i make it work or close at this point?

You do not need to do this, as your sound card is recognized and it once worked. Some process might just have grabbed the sound card, you need to free it. Try "aoss mplayer" that I mentioned above. 

If that works, we will work on  recognizing the process that grabs sound card and force it to behave properly.

---

### Post by scuba_suit on 2007-10-31
cool, i will try this afternoon and letyou know the deal

---

### Post by dkuhlman on 2007-10-31
My sound problem seemed similar.  Sound was working yesterday morning, but not in the afternoon.

In my case there was a simple solution, although it took me several hours to find it.

In another thread on sound problems, someone suggested checking the volume.  In my case the volume was OK, but I was muted.

I'm running Gnome, and there is an icon on the panel that looks like a little speaker.  I right-clicked on that and then un-checked "Mute".

Now I can hear sound again.  Super.

Hope this helps.

Dave

---

### Post by scuba_suit on 2007-10-31
hey i didn't notice it before but now there is a red box with an x in it, i right click and the menu pops up, it has the "mute" on, but i click it and doesn't uncheck it, anyone know what i could do to unmute?

---

