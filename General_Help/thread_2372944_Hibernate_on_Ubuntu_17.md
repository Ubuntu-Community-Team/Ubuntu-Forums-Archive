---
title: "Hibernate on Ubuntu 17"
date: 2017-09-30
forum: General Help
---

### Post by trivium2 on 2017-09-30
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]Helloeveryone.[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]I'mfairly new on the ubuntu environment, and I'm having an issues withhibernating my laptop.[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]Ihave used both ubuntu 16 and 17, and I always had the sameproblem.[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]Basicaly,I searched everywhere and I cant find a solution. I tried all thecommands I could find to force the laptop to hibernate, but they areinvalid. I recently increased the size of my swap partition, assuggested, but nothing changed, I only have the option to suspend.[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]I'm using an Acer E5-573g with 17.04.
Any clues? I ran out of ideas.
Thanks in advance.[/FONT][/COLOR]

---

### Post by ajgreeny on 2017-09-30
Please give us more information on exactly what you have already tried.

Is this a clean install of 17.04, which now by default uses a swapfile, not a swap partition.  You can not hibernate if you use a swapfile as far as I'm aware, though that may have changed recently without my knowledge.

Do you really need to hibernate as opposed to suspend?
Booting from hibernation took as long as a cold boot on my machine when I last tried it in 14.04, so I do not bother enabling it any more.

You might like to look at [https://ubuntuforums.org/showthread.php?t=2219403](https://ubuntuforums.org/showthread.php?t=2219403) which is about 14.04 but I think still stands if you really do have a swap partition.

---

### Post by trivium2 on 2017-09-30
Checked that link, still nothing. One of the first commands I used was [COLOR=#111111][FONT=Consolas] sudo pm-hibernate which keeps coming as invalid, but on 17.04, it's just doesn't do anything, no error at all.
I tried editing some files the same way that link proposes and it doesn't work, makes no difference at all.
I've seen people saying that on non ubuntu certified laptops hibernate will not work, but I'm sure there is a way to go around this.
I'm trying to be as specific as I can because as I mentioned, I'm pretty new with ubuntu and I got so used to hibernate that its driving me crazy.[/FONT][/COLOR]

---

### Post by trivium2 on 2017-09-30
Tried this command now: [COLOR=#111111][FONT=Consolas]sudo systemctl hibernate and I got the error: [/FONT][/COLOR]Failed to hibernate system via logind: Sleep verb not supported.
Any clues?

---

