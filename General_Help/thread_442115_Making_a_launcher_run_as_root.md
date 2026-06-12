---
title: "Making a launcher run as root"
date: 2007-05-13
forum: General Help
---

### Post by Nehvrook on 2007-05-13
Hi, I've been playing around getting games working in Ubuntu. I've got WoW working fine and just recently got Quake III working too. I don't like having to type commands each time I want to launch the game, so for WoW I made a launcher (Right click, create launcher).

I just used the command "Wine <path to wow.exe>" gave it a name and it launches WoW for me. I could do the same thing for quake easily, but I've had problems with sound in this game, the only way I can fix these problems is by running the commands

echo "quake3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss

and 

echo "quake3.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss

in the root terminal followed by the path to the Quake3 file.
Is it possible to make a launcher run these commands in the root terminal, and since they count as three seperate commands do I have to do anything to seperate them so it doesn't think they're all one big command?

I hope I was clear enough in explaining what I'm asking, thanks in advance for any help

---

### Post by aidanr on 2007-05-13
this is the way i'd do it
```
sudo gedit /usr/local/bin/q3fix
```
```
#!/bin/bash
echo "quake3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss &&
echo "quake3.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss &
```
```
sudo chmod +x /usr/local/bin/q3fix
```
```
sudo visudo
```
```
%admin ALL=(ALL) ALL, NOPASSWD:/usr/local/bin/q3fix
```
```
sudo gedit /usr/local/bin/q3
```
```
#!/bin/bash
sudo q3fix &&
cd /path/to/quake3/ &&
./quake3.x86 &
```
```
sudo chmod +x /usr/local/bin/q3
```

and then in the launcher just put q3, just so that the fix is run as root and the game run as normal user, btw have you tried it with aoss (aoss /path/to/quake3/quake3)?

---

### Post by Nehvrook on 2007-05-13
Okay I tried what you said, but I'm still learning aboux Linux so I might have done something wrong. I got a bit confused after the "sudo visudo" command, I wasn't sure where to enter stuff after that.
I did what I thought you meant but it didn't work. What exactly was I supposed to enter into the command part when creating the launcher?

I tried aoss <path to quake3> but that caused my system to hang (Like some other fixes for the sound did before I found those two wich work)

---

### Post by aidanr on 2007-05-13
when you type sudo visudo scroll to the bottom (down arrow) and add that line, then hit ctrl+x to exit and select save

---

### Post by Nehvrook on 2007-05-14
Thanks, this worked fine :)

---

### Post by Nehvrook on 2007-05-17
Edit: nvm

---

### Post by whistlenuts on 2008-01-25
aidanr, 

unrelated to getting quake running...but thanks for posting this...it helped me a ton setting up my machine. 

Cheers,
Matt

---

