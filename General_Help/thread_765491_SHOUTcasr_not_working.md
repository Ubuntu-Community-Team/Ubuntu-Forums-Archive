---
title: "SHOUTcasr not working"
date: 2008-04-24
forum: General Help
---

### Post by nicol_bolas on 2008-04-24
I get

> 
Failed to execute child process "xmms" (no such file or directory).
I have installed Abraca and it still does not work.

Please help, Thank you.

---

### Post by Ripfox on 2008-04-24
Change the word xmms to audacity in the settings and install audacity

---

### Post by nicol_bolas on 2008-04-24
> **ripfox said:**
> Change the word xmms to audacity in the settings and install audacity

Where are the setting you are talking about?

---

### Post by Ripfox on 2008-04-24
This is streamtuner were talking about right?

---

### Post by nicol_bolas on 2008-04-24
> **ripfox said:**
> This is streamtuner were talking about right?

yes, but I can't find the setting or anywhere I can change xmms to audacity.

---

### Post by nicol_bolas on 2008-04-25
Bump

I still need help

---

### Post by natrixgli on 2008-04-25
Hi,

Audacity is not what you want, it's actually Audacious...

Open Streamtuner, and go to Edit > Preferences

Under "Applications" look for "xmms %q" and change to "audacious %q"

(you will probably see it twice, change both.)


Then, open Applications > Accessories > Terminal and type:

```
sudo apt-get install -y audacious
``` and press 'ENTER'

When prompted for your password, enter it (followed by 'ENTER')

Wait for it to finish, and enjoy some radio.


-n8

---

### Post by nicol_bolas on 2008-04-25
Thank you natrixgli, that worked
:guitar:

and thank you ripfox for trying.

---

### Post by Ripfox on 2008-04-25
Whoops..was on my way out the door...sorry AUDACIOUS not AUDACITY...lol sometimes I am a dumbass.

---

### Post by nicol_bolas on 2008-04-25
> **ripfox said:**
> Whoops..was on my way out the door...sorry AUDACIOUS not AUDACITY...lol sometimes I am a dumbass.

That's okay
:lolflag:

---

### Post by jsmumma on 2008-04-30
An alternative is to use Beep Media Player (BMP), which is installed as part of Hardy Heron. According to:

[INDENT][http://en.wikipedia.org/wiki/Beep_Media_Player](http://en.wikipedia.org/wiki/Beep_Media_Player)[/INDENT]

BMP was a fork of XMMS and Audacious was a fork of BMP.

Open streamtuner and follow the menu to:

[INDENT]Edit > Preferences[/INDENT]

Under "Applications" change both of the following lines:

[INDENT]Listen to a .m3u file    xmms %q[/INDENT]
[INDENT]Listen to a stream       xmms %q[/INDENT]

to:

[INDENT]Listen to a .m3u file    beep-media-player --show-main-window %q[/INDENT]
[INDENT]Listen to a stream       beep-media-player --show-main-window %q[/INDENT]

(You might expect, as I did, that "Listen to a stream" is the line to change, but the one that matters to streamtuner is "Listen to a .m3u file". By changing both lines, you have excised XMMS.)  

Now, when you "Tune In" to a stream, the BMP GUI appears on the desktop and BMP plays the stream just as XMMS did before. This worked for me and I am once again a happy camper. :)

Note that if you omit the

[INDENT]--show-main-window[/INDENT]

option, BMP will still play the stream. No GUI for BMP appears on the desktop, however, so you have no simple pause/play control over the stream and no stream information display. This may not be important for some users who simply want to tune in to a stream and listen.

---

