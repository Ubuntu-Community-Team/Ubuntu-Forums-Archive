---
title: "Restart sound?"
date: 2007-05-23
forum: General Help
---

### Post by Pikestaff on 2007-05-23
On occasion, my sound seems to quit working.  I can sometimes fix this problem, for example, killing Firefox will fix the problem a lot of the time.  Other times, though, I can't get the sound to come back unless I restart X.

I was wondering, since that can sort of be a pain (often I'm talking to people in IM or doing other stuff)... is there a way to restart the sound system without actually having to restart X or reboot the computer?  I've tried things like "sudo killall alsa" but that doesn't seem to help, is there some other command that will?

Thanks in advance.

---

### Post by tigerstripedcat on 2007-05-29
I've always wondered this--you should only have to restart linux if you change the kernel!--and I think I found out how:

do:

sudo /etc/init.d/alsa-utils restart

But sometimes this won't work if something is really holding on to the sound so do:

name@comp:~$ lsof | grep pcm
sh         5079    name   70u      CHR              116,6              13639 /dev/snd/pcmC0D0p
esd        5080    name   70u      CHR              116,6              13639 /dev/snd/pcmC0D0p

to find the process id and then kill it and restart:

name@comp:~$ kill -9 5079
name@comp:~$ kill -9 5080
name@comp:~$ lsof | grep pcm
sudo /etc/init.d/alsa-utils restart

and hopefully that will work.

---

### Post by jaadatepe on 2007-11-07
Dude -- you are my lord and savior, note lowercase <<not a blasphemer>>

This problem has plagued me for God knows how long. Big thanks.

Eventually I found the **alsa-utils restart** command, which saves me a good 60% of the time, but I was forced to restart the damn computer sometimes.

It seems like this would happen when you closed a program abruptly... I guess something is going wrong and it's not "releasing control" of the device, or something...

Either way, your directions worked so great!! This is the kind of stuff that needs to be shared more often. I don't know how long I looked for this post, and finally it's appeared. Thankfully. I love typing mumbo jumbo that fixes my computer.

---

### Post by asaturn on 2007-11-30
the built-in torrent client on 7.10 seems to always require me to kill them before I can get my sound back. thanks for the tip.

---

### Post by dror on 2007-12-17
I tried all of the above and nothing worked till I did 
/etc/init.d/alsa-utils reset
One more thing to try.

---

### Post by har5ha on 2007-12-28
> **tigerstripedcat said:**
> I've always wondered this--you should only have to restart linux if you change the kernel!--and I think I found out how:

do:

sudo /etc/init.d/alsa-utils restart

But sometimes this won't work if something is really holding on to the sound so do:

name@comp:~$ lsof | grep pcm
sh         5079    name   70u      CHR              116,6              13639 /dev/snd/pcmC0D0p
esd        5080    name   70u      CHR              116,6              13639 /dev/snd/pcmC0D0p

to find the process id and then kill it and restart:

name@comp:~$ kill -9 5079
name@comp:~$ kill -9 5080
name@comp:~$ lsof | grep pcm
sudo /etc/init.d/alsa-utils restart

and hopefully that will work.

Thanks !!

---

### Post by strange_cathect on 2008-02-18
I can confirm that the disappearing sound is related to the use of torrent download.  Has this been submitted as a bug?

---

### Post by otree013 on 2008-02-20
Hi, I have the same problem of sound cutting out unexpectedly but none of the above seem to work. Does anyone have any other suggestions?

---

### Post by socceroos on 2008-02-20
Apparently we'll have much better sound management in Ubuntu 8.04.

Hopefully this will rid us of all of these problems.

---

### Post by alainjackson on 2008-03-28
My problem is similar but different. I've got a dual boot Ubuntu/Windows system on an IBM laptop. If sound is working in Ubuntu it keeps working ok. The problem is if I boot into windows on my IBM laptop. If I hit the hardware mute key the sound goes off. Next time I boot into Ubuntu I can't get the sound to come back on. The mute and volume keys work in that they bring up the mute and volume dialogs in Ubuntu but no sound comes out. 

I've tried all the suggestions in this thread - restarting and resetting alsa and searching for processes hogging the sound card but none of that works. The only way to get sound back is to reboot into windows, un-mute the sound and come back to Ubuntu.

I am guessing here, but it's as if when I press the mute key in windows it's going in at some hardware level below what Ubuntu is working with. 

Any clues how to get sound back on without rebooting into windows?

Cheers!

---

### Post by antheia on 2008-06-14
> **tigerstripedcat said:**
> I've always wondered this--you should only have to restart linux if you change the kernel!--and I think I found out how:

do:

sudo /etc/init.d/alsa-utils restart

But sometimes this won't work if something is really holding on to the sound so do:

name@comp:~$ lsof | grep pcm
sh         5079    name   70u      CHR              116,6              13639 /dev/snd/pcmC0D0p
esd        5080    name   70u      CHR              116,6              13639 /dev/snd/pcmC0D0p

to find the process id and then kill it and restart:

name@comp:~$ kill -9 5079
name@comp:~$ kill -9 5080
name@comp:~$ lsof | grep pcm
sudo /etc/init.d/alsa-utils restart

and hopefully that will work.

Many, many thanks! :)

---

### Post by prostar on 2008-06-17
Post #2 also worked for me!  Finally!

---

