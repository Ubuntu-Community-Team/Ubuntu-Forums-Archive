---
title: "Ubuntu freezes after login"
date: 2008-06-19
forum: General Help
---

### Post by Coolvortex on 2008-06-19
Hello, I'm new to the forum and pretty new to the whole linux thing too. I installed ubuntu and liked it a lot, everything worked so fine apart from some small issues that I managed to solve by myself (learning a lot of things about linux and it's console commands and everything). After three or four days of use, I turned on my computer like usual, got to the login screen and put my userid and passowrd. The screen became yellow like usual, but nothing happened. Then, after a while, a grey square showed up on the upper left side of the screen. If I move the mouse on that grey square, the cursor looks just like the one you get when you point the mouse on a textbox (the "I").
I booted on recovery mode, did the X server fix thing but nothing happened. I tried the GNOME emergency mode, but it does exactly the same thing. The only thing working is the console, but as I said I'm new to linux (years and years of dos and windows) and I don't know what to do. Gimme a hand!

Thanks in advance for the help

---

### Post by Coolvortex on 2008-06-19
bump

---

### Post by Coolvortex on 2008-06-20
Please... does anyone know a way to solve this? Looks like no one is even reading this....

---

### Post by Zorael on 2008-06-20
If noone is answering that likely just means that noone has an immediate answer for you. Not every problem is obvious. I'm certain to come across as harsh now, but you're not in a position to *demand* help, and guilting people into it is certainly not the way. :>


I'd try creating a new user, from a terminal interface if necessary since you can't login.
```
# adduser -m -G admin newusername
```

If it works for him/her/it, you could gradually try to copy your old settings between their /home/ directories.

---

### Post by Coolvortex on 2008-06-20
Sorry... I didn't mean to guilt anyone... I just thought no one had seen the thread. Sorry again

Anyway, I tried adding a new user but it does exactly the same thing. I'd say it's some kind of graphical issue but I woulnd't bet on it. I tried removing the ati restricted drivers with apt-get from the recovery console but nothing changed, not even a little bit. 
I noticed one thing though: when the system loads, there's something that "fail"s instead of ok, but it just goes too fast and I can't read it.
Is there a bootlog or something?

---

### Post by VMC on 2008-06-20
Maybe an update caused your problem. Tell us what the specs are for you computer, CPU & Speed, RAM, HD, Video. That may reveal something.

---

### Post by Coolvortex on 2008-06-21
My computer has an athlon64 3200 cpu, 1GB of ram, an ati x1900gt video card, a sata dvd burner, two sata HDs and an IDE HD (the one which ubuntu is installed on). I had added some lines in "fstab" to make ubuntu mount the other two disks on load (they're formatted in ntfs, but there's all my data there), but that doesn't seem to be the problem either since I erased those lines but it still does the same thing.

---

