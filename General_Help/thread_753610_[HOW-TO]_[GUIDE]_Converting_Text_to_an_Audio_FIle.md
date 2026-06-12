---
title: "[HOW-TO] [GUIDE] Converting Text to an Audio FIle"
date: 2008-04-12
forum: General Help
---

### Post by s3a on 2008-04-12
**I will show you how to convert text to a .wav file:**

1) Highlight then copy the text that you want to convert
2) Click Applications-->Accessories-->Terminal
3) Type: "sudo gedit"
4) Paste the text you had previously copied.
5) **Name the file "temp"** and save the file **on desktop.**
6) Now do the following in the terminal:

a) cd ~/Desktop
b) espeak -f **temp**.txt -w **temp**.wav -s 85

Things can be tweaked better but as of now, these are my preferred settings and I don't know how to change the settings by myself anyway lol. Changing "85" to different numbers increases or decreases the read speed.

---

### Post by ryanhaigh on 2008-04-14
Espeak is a great little app especially considering its installed by default. When I was updating my little sisters computer over ssh I made her computer tell her to save all her stuff and restart.

---

### Post by Rinzwind on 2008-04-14
Damn this is sooooooooo cool :D
Thank you!!!!!!!!!! :)
I'll have a blast with this.

---

### Post by ryanhaigh on 2008-04-15
You can also use this in combination with pdftotext to convert an ebook into an audiobook. You can also save space by using lame to create an mp3 rather than wav file. [This thread](http://ubuntuforums.org/showthread.php?t=707042 ) has details on how you can do that.

---

