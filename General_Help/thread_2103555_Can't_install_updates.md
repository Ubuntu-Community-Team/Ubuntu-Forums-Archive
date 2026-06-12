---
title: "Can't install updates"
date: 2013-01-10
forum: General Help
---

### Post by DrKosy on 2013-01-10
Since yesterday I can't install any updates anymore. I just get an error like this:
"can't sync mmap - msync (5: input -/ output error)"
I get this message no matter if I use Synaptic or apt-get in terminal.
Do anyone out there have any clue what that error could mean?

---

### Post by d4rk0wl on 2013-01-10
Apparently this is a known bug.
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/796849](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/796849)

mmap is a C function that allows and maps files to memory, so it is kind of worrisome that this might be hardware related.

Try to run:
```
sudo apt-get clean
```
Then:
```
sudo apt-get update
```

Also does apt inform you of any broken dependencies on an update?

Regards,
- D4rk0wl

---

### Post by DrKosy on 2013-01-12
I just tried out your advice.
> sudo apt-get cleandid the first trick, the error about mmap is gone. Unfortunally the error with sync (5: Input- /output error) is still there.

Another strange thing appeared just 5 Minutes ago. As I started my machine he booted into some kind of terminal called "setramfs" or something like that. After one reboot I grub showed me a boot list (the first time ever since I use Lubuntu). Choosing "normal start" crashed my machine. Another reboot got me back my usual Lubuntu.

I hope this was the last time I run into such strange things...

Edit: No broken dependencies on my machine (the only nice thing)

---

### Post by DrKosy on 2013-01-13
The trouble get more every day, now my file-system is mounted read-only :frown:
I tried secure mode from grub, started fsck, fixed all found errors. Than I was able to install all updates for VLC-Mediaplayer.
From time to time my filesystem is mounted read-only and if I get an writable HDD the same errors for updates occure than before. Even "apt-get clean" doesn't work as described before.
This are very wiered things, so I would be glad if someone would have a clue what I can do.

---

### Post by Max Blyss on 2013-01-13
> **DrKosy said:**
> The trouble get more every day, now my file-system is mounted read-only :frown:
I tried secure mode from grub, started fsck, fixed all found errors. Than I was able to install all updates for VLC-Mediaplayer.
From time to time my filesystem is mounted read-only and if I get an writable HDD the same errors for updates occure than before. Even "apt-get clean" doesn't work as described before.
This are very wiered things, so I would be glad if someone would have a clue what I can do.

Open up that box and check your connections.  Just make sure everything is plugged in alright, and make sure the jumper on your HDD is in the correct spot.

I had some boot and disk oddities a while back, and it amounted to a somehow - got - loose HDD connection.  Don't ask me how, that just fixed it.  Might be something you want to look at.

---

### Post by DrKosy on 2013-01-13
I do not know how but it just happend that my machine installed all updates as expected.
Nevertheless I'll check all my cables and things.
I'll report about my monitoring.

Edit: After two days of smooth work I hope my problems are finally gone. What a great feeling :-)

---

