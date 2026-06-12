---
title: "Terminal Control of ALSA"
date: 2006-07-16
forum: General Help
---

### Post by compwiz18 on 2006-07-16
Is there a command that will let a person control ALSA with the terminal?  I'm trying to make that little mute button on my laptop light up, and I've figured out that I have to turn off the external amplifier, then it'll come on.  So I would like know, more exactly, how to turn off the external amp with a terminal command.

Thanks in advance.

---

### Post by ayoli on 2006-07-16
amixer should do what you want :
```
NAME
       amixer - command-line mixer for ALSA soundcard driver

SYNOPSIS
       amixer [-c card] [cmd]

DESCRIPTION
       amixer  allows  command-line  control of the mixer for the ALSA soundcard driver.  amixer
       supports multiple soundcards.
```
so `man amixer` for further info, cause i wont copy the full page here :p
reagrds.

---

