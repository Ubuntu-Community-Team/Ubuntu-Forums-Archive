---
title: "Lubuntu 17.10 Hangs on hour long idle | EXT4-fs error spam"
date: 2018-07-03
forum: General Help
---

### Post by renny2125 on 2018-07-03
I run Lubuntu 17.10 on a 32GB Sandisk Ultra Fit on a Lenovo Thinkpad X230.
(Please do not make recommendations to change my install location. It will remain on the flash drive.)

I've had this problem where after several hours the system soft hangs, often applications will seem to work for a few clicks before everything stops working, the mouse either free or frozen. During this time, the flash drive's indicator will flash on and off, and will continue so with the application of the magic key sequence **Ctrl + SysRq + B**. This will also delay the startup of the computer off of the flash drive OR hard drive, and requires the computer to be fully powered off for a few seconds. After that, it's business as usual and the computer doesn't act up until it idles for several hours.

Half an hour before posting, I return to the laptop expecting the same scenario as above. I wake the display, to be greeted with the normal login screen, except every picture except for the background is replaced with a black-with-white-frame polaroid looking icon, with the corner peeled. I use **Ctrl+Alt+F1** to switch to tty1 and I'm met with the error spam that you see in both videos below. Another symptom, shown in one of the videos, is that the flash drive's indicator isn't blinking; likely the flash drive was remounted.
Side note: all the "^@"s are from me trying to switch back to the graphical tty.

[Journalctl Log]("https://pastebin.com/MHmqM7Ss")
[Video 1]("https://youtu.be/PF7zRp5yH8c")
[Video 2]("https://youtu.be/-BIYbGCCMz4")

---

### Post by renny2125 on 2018-07-09
bump

---

