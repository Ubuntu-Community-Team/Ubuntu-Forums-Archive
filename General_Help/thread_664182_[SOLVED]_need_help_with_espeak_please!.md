---
title: "[SOLVED] need help with espeak please!"
date: 2008-01-10
forum: General Help
---

### Post by NULL712 on 2008-01-10
OK so I fire up my trusty terminal and type   espeak "hello world"  and all I get is errors.
I am running ubuntu 7.10 on an AMD Duron with 440 Mb of RAM and Compiz Fusion!!

below is the output I get in the terminal any/all help is welcome! Thanx!

~$ espeak "hellow wolrd"
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000

:confused:

---

### Post by qwexer on 2008-02-07
I see you solved it...how? I'm getting the same error

---

### Post by NULL712 on 2008-02-13
Well I figured out that I didn't have a voice installed for Festival. Just fire up Synaptic and search for festival, then scroll down until you find the voices. Note: it helps to look at the package description as you search for the voice.  

I hope that helps.

Null377

---

