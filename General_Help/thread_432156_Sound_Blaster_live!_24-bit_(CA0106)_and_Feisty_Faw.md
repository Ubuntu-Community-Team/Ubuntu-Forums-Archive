---
title: "Sound Blaster live! 24-bit (CA0106) and Feisty Fawn"
date: 2007-05-03
forum: General Help
---

### Post by WDSnav on 2007-05-03
When I first installed ubuntu 7.04 my sound worked perfecly and no issues at all. I let the system get all of its updates and it asked me to restart, so I restarted and now my sound does not work at all. The only choice I have in the volume control for CA0106 is recording, no playback. I typed in alsamixer into a the terminal and it says that the card is a "Intel ICH6" which is not what I am using. How can I fix this? Another issue, when I try to open desktop effects I get this error "The Composite extension is not available" I have installed my ATI card and its enable on the restricted hardware manager. How do I fix these issues??

---

### Post by kpkeerthi on 2007-05-03
Couple of things you may want to try

1. Remove .asoundrc and .asoundrc.conf from your HOME folder. (Or Back it up if you want to). Restart and see if sound works.

2. Try setting the sound device:

To list the cards you have
```

sudo asoundconf list

```

Set the default card - ICH6
```

sudo asoundconf set-default-card ICH6

```

Set the default card - Audigy2
```

sudo asoundconf set-default-card Audigy2

```

---

### Post by Tares on 2007-05-07
I don't want to start new thread, so I'll just ask here :

I have my eyes on this soundcard (ca0106) and I'm wondering that hardware mixing is working well under ubuntu, I mean playing q3 and speaking on ts, or other programs that use oss as their sound source ?

---

