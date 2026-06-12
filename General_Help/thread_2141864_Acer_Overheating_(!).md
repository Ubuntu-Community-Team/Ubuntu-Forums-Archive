---
title: "Acer Overheating (!)"
date: 2013-05-03
forum: General Help
---

### Post by oO Flowzilla Oo on 2013-05-03
Hello, I am having some trouble with my Acer Aspire:

[http://www.cnet.com/laptops/acer-aspire-5315-2940/4505-3121_7-32863857.html](http://www.cnet.com/laptops/acer-aspire-5315-2940/4505-3121_7-32863857.html)

The problem that I'm having is that my computer is overheating... A lot. If I use VLC media player, it won't even last 15 minutes without completely shutting down. I didn't have this problem when I had Windows Vista (I currently have Ubuntu 12.04.1 LTS installed).

Is there a way to fix this? 

Thank you.

**Edit:** I forgot to mention that the fan doesn't turn on.

---

### Post by QIII on 2013-05-03
Has this just started happening since you installed Ubuntu?

---

### Post by oO Flowzilla Oo on 2013-05-03
Yes sir, it has.

Quick response... I like that :)

---

### Post by QIII on 2013-05-04
Does the fan spin when you initially turn it on?

---

### Post by oO Flowzilla Oo on 2013-05-04
Let me see...

**Edit:** It did!!! But then it turned off when the Acer screen thing came out.

[IMG]http://i31.photobucket.com/albums/c384/Tma20SC/acerbootscreen.jpg[/IMG]

^^^ Not my image. I found it on Google.

---

### Post by QIII on 2013-05-04
So, it came on at the BIOS splash, before the OS started?

---

### Post by oO Flowzilla Oo on 2013-05-04
Yes. It always does that, ever since I bought it.

I turn it on, it goes to that screen, then it shows a black screen that say's "Broadcom" something with some numbers on it and then it boots to Ubuntu (Purple screen with dots). It did the same thing with Windows.

Edit: It's not that same exact screen but it's similar.

[IMG]http://i17.photobucket.com/albums/b83/amru/LenovoS10_TID/PB082687.jpg[/IMG]

---

### Post by QIII on 2013-05-04
Do you have a setting in your BIOS that allows software fan control?

---

### Post by oO Flowzilla Oo on 2013-05-04
Let me find out. Be right back.

**Edit:** I don't think it has that option. All I see is:

> Information - Computer specs, manufacturer, etc...

> Main - System time, System date, System memory, Total memory, Video memory, Quick boot, Network boot, F12 Boot menu, D2D recovery, SATA mode

> Security - Set Supervisor Password, Set user password, Set HDD password

> Boot - Shows a list of ***"boot priority order***"

> Exit - Exit saving changes, discarding changes, etc...

That's it...

---

### Post by QIII on 2013-05-04
Never mind.  Did some research, and you're not going to like what I found.

That model was designed so that the Vista OS itself controlled the fan via software.  That means that there is no onboard fan control native to the motherboard, other than to kick it on for a moment during the POST.

But I did find a post [here](http://ubuntuforums.org/showthread.php?t=2010883) that appears to contain a solution.

Please post back the results here if this works for you.


Regards

QIII

---

### Post by oO Flowzilla Oo on 2013-05-04
Alright I'll check that out. Thanks. I could +rep you if I knew where the +rep button was...

---

### Post by QIII on 2013-05-04
If you get it to work, that's all the satisfaction I need!  ;)

---

### Post by oO Flowzilla Oo on 2013-05-04
I'm having some issues with step number 6 and 7. The terminal says that the location doesn't exist.

[http://ubuntuforums.org/showthread.php?t=1748521](http://ubuntuforums.org/showthread.php?t=1748521)

Edit: Nevermind. Got through it. Let me test it ...

2nd Edit: Well, it works. I had to change the temp1 thing to temp2 in the code and now it works.

Thank you, sir.

---

