---
title: "My mp3 player is not being recognized"
date: 2007-05-16
forum: General Help
---

### Post by Mr_Mischif on 2007-05-16
OK, here's the deal: I have this 256MB mp3 player, and recently, basically since I upgraded to feisty fawn, it hasn't been recognized. I mean if I check udevmonitor, it shows up as being plugged in, but I get no chance to change the songs in it. Can anyone think of why and how to help?

---

### Post by chatters on 2007-05-16
Are you using an iPod? in which case try installing gtkpod.
If not
 mount /dev/sda(X) /home/*username*/Desktop/*NewFolder*

you might have to guess the X if you do not know it

---

### Post by Mr_Mischif on 2007-05-16
No, it's an old RCA lyra.

---

### Post by DarkN00b on 2007-05-18
I bought a cheap 256 Meg MP3 player today and could not get it to work for anything. Then I RTFM. :)

It turns out I was able to set the player to act as a USB storage device. After I did so I plugged it in and it was recognized, automounted and Nautilus helpfully opened a window for me so I could drag files into it. :guitar:

I don't know if this will help you, but you never know...

---

