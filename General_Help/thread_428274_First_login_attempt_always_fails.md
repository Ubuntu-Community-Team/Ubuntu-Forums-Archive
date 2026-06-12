---
title: "First login attempt always fails"
date: 2007-04-30
forum: General Help
---

### Post by jamespi on 2007-04-30
every time i reboot my computer, the first time i try to log back in to gnome the first time i type my username/password it tells me i typed it wrong. i think it's been doing this since i upgraded to feisty.

i am certain it's not just coincidence as it been doing it for weeks and even if i type really  really carefully (it's not a long password) the first attempt always fails and the second time i go straight through.

any ideas?

---

### Post by tcpip4lyfe on 2007-04-30
Maybe change your password to something short to try it and see if it works.  If it does then change it back and see if you still have problems.  Or maybe its a sticky keyboard.  Try changing keyboards as well.

---

### Post by jawbreaker on 2007-04-30
Are you using a GDM with the face chooser? Are you clicking on the face instead of typing your username? I've been experiencing this problem where the system is not registering the first keypress. My wife keeps telling me she can't login because she clicks on her icon and then types her password. But the first character of her password isn't being registered. I noticed it because I'm used to typing my username. I've not found a solution... But this might be your problem as well.

---

### Post by jamespi on 2007-04-30
yeah i just figured it out before i read your reply - it didnt occur to me to actually look at the username i was typing - (i was watching the keyboard and making sure i pressed the right keys) it was not registering the first key i pressed so my username was wrong on every first attempt.

so the question now is - why doesnt it register the first keypress?

---

### Post by jawbreaker on 2007-05-01
i haven't figured that out yet. at first i thought it was a problem with gdm, but it happens when i boot in text mode too. i'm have trouble booting the latest kernel. i'm not sure if this is related or not. i have a ps/2 memorex keyboard... nothing special about it to cause problems. everything seems to work fine after the first login.

---

### Post by gmtyrant on 2007-05-02
A useless reply: I'm having the same difficulty, even after a complete reinstall of Kubuntu Fiesty.

---

### Post by Sebastral on 2007-05-05
Same problem here. Doesn't register first key, rather bothersome. Tried activating numlock @ gdm, didn't work :(

---

### Post by KlausU on 2007-05-11
Same problem here. On the first keypress, instead of recognizing the keypress numlock is deactivated. Happens with KDE/Text mode.

Btw using a Logitech Internet Pro keyboard. Problem exists only since Feisty and not on grub / other OS.

---

### Post by jamespi on 2007-05-17
i just booted into recovery mode (for an unrelated problem) and the first time i pressed a key the following blurb was splashed across the screen 

```
[  507.585161] input: AT Translated Set 2 keyboard as /class/input/input3
```

does this give anyone any clues?

---

### Post by varchar255 on 2007-05-24
Same problem here. Running Ubuntu Feisty on an AMD 64 X2, standard PS/2 keyboard. First keypress is not recognized; it deactivates NumLock instead.

Anything I can do to help test?

---

### Post by supersuckers on 2007-05-27
[https://bugs.launchpad.net/ubuntu/+bug/117173](https://bugs.launchpad.net/ubuntu/+bug/117173)
I filed a bug report for this.

---

### Post by 4KvRMU7Nnv on 2007-05-28
I had been having this same problem when I realized what was going wrong.  When it starts up and i hear that noise for the login prompt, numlock is already on (at least on my computer).  When I press the first key of my username, instead of showing up on the screen, it simply turns numlock off.  This results in my typing "ohn" instead of "john" thusly, the username and password don't match.  I tried it by turning off numlock before entering my password and it works fine.  Does anyone know how to make the numlock be off on startup?

---

### Post by jamespi on 2007-06-01
i dont think making numlock be off by default will help - if you think about it what you are actually doing is pressing a key before you type your name. the fact that is numlock and you happen to be turning numlock off at the same time is just a coincidence. you could do this with any key, not just numlock - i just type jjamespi instead of jamespi for instance.

---

### Post by jawbreaker on 2007-06-06
Arg.... Still nothing on this? How about a bump at least.... Did a fresh install and still having this problem.

---

### Post by jamespi on 2007-06-13
i cant remember the command for outputting info on your hardware (lspci only lists PCI devices) but on the hardware information window my PS/2 keyboard controller has the following key:

info.linux.driver: i8042

then the next device down is the KBD Port which has:

info.linux.driver: atkbd

which has a device under it called "AT translated set 2 keyboard"

an unrelated device is listed as "IBM Enhanced 101/102 key PS/2 mouse support" which has the key

info.linux.driver: i8042 kbd

does everyone else have the same drivers? perhaps this will narrow the problem down...

---

### Post by hdavid on 2007-06-15
i am having exactly the same problem. and it is only since the install of fiesty...

---

### Post by varchar255 on 2007-10-25
I used to have this problem on Feisty but after upgrading to Gutsy, everything works fine.

---

### Post by gmtyrant on 2007-10-25
Yep, me too. Gutsy has fixed a LOT of problems for me. Feisty was unusable on my machine.

---

