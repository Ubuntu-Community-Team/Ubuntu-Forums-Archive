---
title: "complete system freeze"
date: 2008-03-19
forum: General Help
---

### Post by Ck.asdf on 2008-03-19
Today, I have had two complete lockups of my computer, running ubuntu Studio 7.10


One time was this morning:
I had firefox open, probably a couple other things, and I had just gotten finished ripping the audio files from the Animusic DVD lasta night, so when I went to school this morning, while my teacher was going on about classless networks and IPv6, I was converting those wavs to mp3s through SSH.

I wrote a batch file that would do each wav consecutively without my input, and I watched as it converted, and it stopped on track five. I got some weird notice about losing connection to the network, and I tried reconnecting with no luck, though I could ping it.
I forgot about it, paid attention through class, and I came home tonight after church to find that the system was completely locked up, keyboard and all.  I hit the reset button, went along my business, and it said I had new updates. I downloaded those, browsed stuff in firefox, listening to youtube, doing some console stuff.  I was trying to download and install bitpim for my phone when the download percentage stopped at 20%, and again, the system was at a complete halt.  Programs open at the time included firefox, pidgin, and gnome-terminal.  I tried control alt backspace, delete, even the caps/num/scroll lock buttons weren't changing the lights on the keyboard.

I hit reset again, and came to an ominous error screen:

```

[30.100109] crc error
[30.101161] kernel panic - not syncing: VFS: unable to mount root fs on unknown block (0,0)

```

I reset again, and got yet another message:

```

[25.026774] incomplete literal tree
[25.026812] invalid compressed format (err=1)
[25.027851] kernel panic - not syncing: VFS: unable to mount root fs on unknown block (0,0)

```

One more restart, and it booted up properly.  The only two apps running right now are firefox and gedit.


Any reasons why my system seems to lock up at random, and what I can do about it, so it doesn't happen again?

---

### Post by sowelie on 2008-03-19
Hmm...I would try googling those error messages, although they may be completely unrelated.

The only things that pop into my head are hardware issues.  Most likely either the hard drive or RAM.

---

### Post by Ck.asdf on 2008-03-20
I ran a memtest last night, and threw in the "-l" and put after it my home directory, hoping it would save the log there, but it didn't - where can I find the log?
Before I went to bed, I did see a couple errors.

---

