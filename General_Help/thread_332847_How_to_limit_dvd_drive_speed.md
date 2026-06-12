---
title: "How to limit dvd drive speed?"
date: 2007-01-06
forum: General Help
---

### Post by satanius on 2007-01-06
I just switched from Win Xp to Ubuntu and I must say i like it very much, but there are some thing that I miss. One of this little annoyances is loud sound that my dvd drive makes. I use my computer a lot for watching dvd and divx movies since I don't have dvd player and that sound just ruins the fun. In windows I use nero drive speed or anydvd to limit speed. I've already tried -eject and -hdparm commands and they don't work. I'm googling the whole day trying to find the solution with no luck, so I decided to ask here. Oh, and by the way, I have NEC nd-3500 drive if that helps.

---

### Post by dcstar on 2007-01-06
> **satanius said:**
> I just switched from Win Xp to Ubuntu and I must say i like it very much, but there are some thing that I miss. One of this little annoyances is loud sound that my dvd drive makes. I use my computer a lot for watching dvd and divx movies since I don't have dvd player and that sound just ruins the fun. In windows I use nero drive speed or anydvd to limit speed. I've already tried -eject and -hdparm commands and they don't work. I'm googling the whole day trying to find the solution with no luck, so I decided to ask here. Oh, and by the way, I have NEC nd-3500 drive if that helps.

I believe the **powertweak** package may have a setting for this.

---

### Post by orb9220 on 2007-01-06
Also if you have flashed your firmware with other that removes riplock gives faster read times on ripping but makes some drives nosierrr.

Flashing the drive back to orignal firmware may resolve the issue.

---

### Post by satanius on 2007-01-07
I tried with powertweak, it has cdrom speed settings but they don't work. Well, it says that not all drives support this, it seams that nd-3500 is one of them. I did flash my drive's firmware to remove riplock, I could flash it back with original but that was not solution I was hoping to get. I read somewhere that -eject and -hdparm work only with cdroms, not dvds, is it true, or is it problem in NEC drives? Btw, thaks for your response.

---

### Post by orb9220 on 2007-01-07
Well I had the noisy riplock with liggy's custom firmware and I went back to 1.05 stock I believe and my nec 3550a is quite as a mouse.

I use dvdshrink  and dvd decrypter under wine to rip my movie dvd's and everything works just like on my windowsXP side.

---

### Post by satanius on 2007-01-07
I did as you suggested and went back to official 2.1B firmware. I see/hear some improvement but it's still pretty loud. Well, I suppose I could live with that if there is no better solution. Thank you for your help.
-----------------------------------------------------------------------------------------------
Edited:

OK, I found the real solution on cdfreaks forum so I will post it here, maybe someone will have some use of it. 

Download and compile a short C program which generates the necessary SET_STREAMING ioctl commands.
                       wget [http://noto.de/speed/speedcontrol.c](http://noto.de/speed/speedcontrol.c)
                       gcc -o speedcontrol speedcontrol.c

Set DVD drive speed to x1
                       speedcontrol -x1 /dev/hda (I had tu use ./speedcontrol as root, replace hda with your device) 

Reset the DVD speed to normal
                       speedcontrol -x0 /dev/hda

And that's it, works great!!!

---

### Post by samwyse on 2007-02-11
Thanks for Speedcontrol. It works for me as a normal user.

---

