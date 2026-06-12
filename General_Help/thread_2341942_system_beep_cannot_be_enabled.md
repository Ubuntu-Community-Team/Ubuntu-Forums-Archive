---
title: "system beep cannot be enabled"
date: 2016-11-02
forum: General Help
---

### Post by schockschwerenot on 2016-11-02
hi there,

i'm working on a dell precision tower 5810 with external speakers and a kubuntu-16.04 system. and i tried to activate terminal bell (system beep?!) such that i am able to create a sound in a bash terminal. however, i haven't succeeded yet although i followed descriptions on various websites. so, what i've tried so far is:

```
echo -e '\a'
echo -en "\007"
```no success. then i executed

```
sudo modprobe pcspkr
``` in advance. again, no success. then, in "/etc/modprobe.d/blacklist.conf" i commented the line corresponding to the pc speaker:

```
#blacklist pcspkr
``` and restarted the pc before executing the two echo commands above again. no success. what's wrong with that machine?

of course i could (and did) install "sox" and execute something like

```
play -n synth 0.1 sine 800 vol 0.5
``` which gives a nice sound as i expect. however, since i'm planning to trigger the sound multiple times from within a bash script executed on a remote machine using ssh, a command such as "play" will try to create that sound on the remote machine which doesn't help me sitting at the local pc.

so, does anyone know, what else to do in order to be able to successfully use 

```
echo -e '\a'
echo -en "\007"
``` or any other sound-generating program on a local kubuntu terminal?

many thanks in advance
b.

---

