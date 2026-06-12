---
title: "Edgy - GDM login screen - no sound"
date: 2007-03-24
forum: General Help
---

### Post by greengrocer on 2007-03-24
Hello all,

I have noticed something odd with the GDM login screen on my Ubuntu Edgy install.

The default GDM login screen appears but I do not hear the drums (ie no sound)

However, if I enter a username and password, the login sound occurs and I can hear that.  All sound works whilst logged in.

I noticed that if I goto the "System" menu and then click "Administration", then click "Login Window", in the "Accessability" tab there is an option to play the current selected "Login Window Ready" sound.  I have found that no sound will play there either.

But I can play sounds everywhere else.

I would be elated if someone has an answer on why this bug is occuring to me.

Regards,
Greenie

---

### Post by adam.tropics on 2007-03-24
I can't imagine this would be it, but have you checked in /usr/share/sounds to see if question.wav is actually there, or simpler still, have you tried mapping it to a different sound to see if that makes any difference. Like I said unlikely, but worth checking.

---

### Post by rwe on 2008-05-09
This is also happening in Hardy 8.04

Yes, the question.wav file is there and it works.

There seems to be two problems, the first is if the filename contains spaces, then it won't play. If you rename the file and remove the spaces, then it will play.

The second problem, is that it doesn't play the file completely, it chops off the last part of the file.

In my case I had two files
"Computer; Authorization Accepted.wav"
"Computer; Access Denied.wav"

removing the spaces, the sounds now play, but get chopped off

i.e.  Access Deni
      Authorization accep

Not sure if this is a problem with they format of the wav file or not.

---

### Post by lleonardloh on 2008-07-02
I have the same problem occur after did installed pulse audio mixer... the question.wav did not sound at the login page.

---

