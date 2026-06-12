---
title: "Quick"
date: 2006-08-10
forum: General Help
---

### Post by Dylan103 on 2006-08-10
What program do I use to copy cd's to a .mp3 instead of sound juicer wich converts to .ogg

---

### Post by vijirajan on 2006-08-10
You mean you want to convert regular cd audio files to mp3? If so you can use [COLOR="Red"]lame[/COLOR] to do that.

sudo apt-get install lame

and for each file run,

lame -f infile.wav outfile.mp3

---

### Post by Dylan103 on 2006-08-10
Is there a easier way to do that? I have like 80 cd's(regular) and want to burn to put on my mp3 player/computer.

---

### Post by vijirajan on 2006-08-10
If you think this is cumbersome, you can automate it in a script and run the script for each CD. There may be some tools out there that does this for you but basically this is how you convert an audio cd to mp3 cd. If I come across any tools I will let you know.

---

